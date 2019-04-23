---
title: 建立具有外掛程式的 .NET Core 應用程式
description: 了解如何建立支援外掛程式的 .NET Core 應用程式。
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/28/2019
ms.openlocfilehash: a9431ee28c7df21a8688f845be20e062eca21887
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773424"
---
# <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="ffcc5-103">建立具有外掛程式的 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="ffcc5-103">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="ffcc5-104">本教學課程會示範如何：</span><span class="sxs-lookup"><span data-stu-id="ffcc5-104">This tutorial shows you how to:</span></span>

- <span data-ttu-id="ffcc5-105">建構專案以支援外掛程式。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-105">Structure a project to support plugins.</span></span>
- <span data-ttu-id="ffcc5-106">建立自訂 <xref:System.Runtime.Loader.AssemblyLoadContext> 以載入每個外掛程式。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-106">Create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load each plugin.</span></span>
- <span data-ttu-id="ffcc5-107">使用 `System.Runtime.Loader.AssemblyDependencyResolver` 類型以允許外掛程式具有相依性。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-107">Use the `System.Runtime.Loader.AssemblyDependencyResolver` type to allow plugins to have dependencies.</span></span>
- <span data-ttu-id="ffcc5-108">撰寫只要複製組建成品即可輕鬆部署的外掛程式。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-108">Author plugins that can be easily deployed by just copying the build artifacts.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ffcc5-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="ffcc5-109">Prerequisites</span></span>

- <span data-ttu-id="ffcc5-110">安裝 [.NET Core 3.0 Preview 2 SDK](https://www.microsoft.com/net/core) 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-110">Install the [.NET Core 3.0 Preview 2 SDK](https://www.microsoft.com/net/core) or a newer version.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="ffcc5-111">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="ffcc5-111">Create the application</span></span>

<span data-ttu-id="ffcc5-112">第一個步驟是建立應用程式：</span><span class="sxs-lookup"><span data-stu-id="ffcc5-112">The first step is to create the application:</span></span>

1. <span data-ttu-id="ffcc5-113">建立新的資料夾，並在該資料夾中執行 `dotnet new console -o AppWithPlugin`。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-113">Create a new folder, and in that folder run `dotnet new console -o AppWithPlugin`.</span></span> 
2. <span data-ttu-id="ffcc5-114">為了讓專案建置更容易，請建立 Visual Studio 方案檔。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-114">To make building the project easier, create a Visual Studio solution file.</span></span> <span data-ttu-id="ffcc5-115">在相同的資料夾中執行 `dotnet new sln`。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-115">Run `dotnet new sln` in the same folder.</span></span> 
3. <span data-ttu-id="ffcc5-116">執行 `dotnet sln add AppWithPlugin/AppWithPlugin.csproj` 以將應用程式專案新增至方案。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-116">Run `dotnet sln add AppWithPlugin/AppWithPlugin.csproj` to add the app project to the solution.</span></span>

<span data-ttu-id="ffcc5-117">現在，我們可以填入應用程式的基本架構。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-117">Now we can fill in the skeleton of our application.</span></span> <span data-ttu-id="ffcc5-118">以下列程式碼取代 *AppWithPlugin/Program.cs* 檔案中的程式碼：</span><span class="sxs-lookup"><span data-stu-id="ffcc5-118">Replace the code in the *AppWithPlugin/Program.cs* file with the following code:</span></span>

```csharp
using PluginBase;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Reflection;

namespace AppWithPlugin
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                if (args.Length == 1 && args[0] == "/d")
                {
                    Console.WriteLine("Waiting for any key...");
                    Console.ReadLine();
                }

                // Load commands from plugins.

                if (args.Length == 0)
                {
                    Console.WriteLine("Commands: ");
                    // Output the loaded commands.
                }
                else
                {
                    foreach (string commandName in args)
                    {
                        Console.WriteLine($"-- {commandName} --");

                        // Execute the command with the name passed as an argument.

                        Console.WriteLine();
                    }
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex);
            }
        }
    }
}

```

## <a name="create-the-plugin-interfaces"></a><span data-ttu-id="ffcc5-119">建立外掛程式介面</span><span class="sxs-lookup"><span data-stu-id="ffcc5-119">Create the plugin interfaces</span></span>

<span data-ttu-id="ffcc5-120">建置具有外掛程式之應用程式其下一步是定義外掛程式需要實作的介面。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-120">The next step in building an app with plugins is defining the interface the plugins need to implement.</span></span> <span data-ttu-id="ffcc5-121">建議您建立類別庫，其中包含您打算用來在應用程式與外掛程式之間通訊的任何類型。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-121">We suggest that you make a class library that contains any types that you plan to use for communicating between your app and plugins.</span></span> <span data-ttu-id="ffcc5-122">這項劃分可讓您以套件形式發佈外掛程式介面，而不必提供完整的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-122">This division allows you to publish your plugin interface as a package without having to ship your full application.</span></span>

<span data-ttu-id="ffcc5-123">在專案的根資料夾中，執行 `dotnet new classlib -o PluginBase`。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-123">In the root folder of the project, run `dotnet new classlib -o PluginBase`.</span></span> <span data-ttu-id="ffcc5-124">另外執行 `dotnet sln add PluginBase/PluginBase.csproj` 以將專案新增至方案檔。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-124">Also, run `dotnet sln add PluginBase/PluginBase.csproj` to add the project to the solution file.</span></span> <span data-ttu-id="ffcc5-125">刪除 `PluginBase/Class1.cs` 檔案，並在 `PluginBase` 資料夾中，使用下列介面定義來建立名為 `ICommand.cs` 的新檔案：</span><span class="sxs-lookup"><span data-stu-id="ffcc5-125">Delete the `PluginBase/Class1.cs` file, and create a new file in the `PluginBase` folder named `ICommand.cs` with the following interface definition:</span></span>

[!code-csharp[the-plugin-interface](~/samples/core/extensions/AppWithPlugin/PluginBase/ICommand.cs)]

<span data-ttu-id="ffcc5-126">此 `ICommand` 介面是所有外掛程式都會實作的介面。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-126">This `ICommand` interface is the interface that all of the plugins will implement.</span></span>

<span data-ttu-id="ffcc5-127">現在已定義 `ICommand` 介面，可以為應用程式專案多填入一些資訊。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-127">Now that the `ICommand` interface is defined, the application project can be filled in a little more.</span></span> <span data-ttu-id="ffcc5-128">從根資料夾使用 `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` 命令，將 `AppWithPlugin` 專案的參考新增至 `PluginBase` 專案。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-128">Add a reference from the `AppWithPlugin` project to the `PluginBase` project with the `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj`  command from the root folder.</span></span>

<span data-ttu-id="ffcc5-129">以下列程式碼片段取代 `// Load commands from plugins` 註解，讓它從指定的檔案路徑載入外掛程式：</span><span class="sxs-lookup"><span data-stu-id="ffcc5-129">Replace the `// Load commands from plugins` comment with the following code snippet to enable it to load plugins from given file paths:</span></span>

```csharp
string[] pluginPaths = new string[]
{
    // Paths to plugins to load.
};

IEnumerable<ICommand> commands = pluginPaths.SelectMany(pluginPath =>
{
    Assembly pluginAssembly = LoadPlugin(pluginPath);
    return CreateCommands(pluginAssembly);
}).ToList();
```

<span data-ttu-id="ffcc5-130">然後以下列程式碼片段取代 `// Output the loaded commands` 註解：</span><span class="sxs-lookup"><span data-stu-id="ffcc5-130">Then replace the `// Output the loaded commands` comment with the following code snippet:</span></span>

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

<span data-ttu-id="ffcc5-131">以下列程式碼片段取代 `// Execute the command with the name passed as an argument` 註解：</span><span class="sxs-lookup"><span data-stu-id="ffcc5-131">Replace the `// Execute the command with the name passed as an argument` comment with the following snippet:</span></span>

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

<span data-ttu-id="ffcc5-132">最後，將靜態方法新增至名為 `LoadPlugin` 和 `CreateCommands` 的 `Program` 類別，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ffcc5-132">And finally, add static methods to the `Program` class named `LoadPlugin` and `CreateCommands`, as shown here:</span></span>

```csharp
static Assembly LoadPlugin(string relativePath)
{
    throw new NotImplementedException();
}

static IEnumerable<ICommand> CreateCommands(Assembly assembly)
{
    int count = 0;

    foreach (Type type in assembly.GetTypes())
    {
        if (typeof(ICommand).IsAssignableFrom(type))
        {
            ICommand result = Activator.CreateInstance(type) as ICommand;
            if (result != null)
            {
                count++;
                yield return result;
            }
        }
    }

    if (count == 0)
    {
        string availableTypes = string.Join(",", assembly.GetTypes().Select(t => t.FullName));
        throw new ApplicationException(
            $"Can't find any type which implements ICommand in {assembly} from {assembly.Location}.\n" +
            $"Available types: {availableTypes}");
    }
}
```

## <a name="load-plugins"></a><span data-ttu-id="ffcc5-133">載入外掛程式</span><span class="sxs-lookup"><span data-stu-id="ffcc5-133">Load plugins</span></span>

<span data-ttu-id="ffcc5-134">現在應用程式可以從載入的外掛程式組件正確地載入並具現化命令，但仍然無法載入外掛程式組件。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-134">Now the application can correctly load and instantiate commands from loaded plugin assemblies, but it is still unable to load the plugin assemblies.</span></span> <span data-ttu-id="ffcc5-135">在 *AppWithPlugin* 資料夾中，使用下列內容來建立名為 *PluginLoadContext.cs* 的檔案：</span><span class="sxs-lookup"><span data-stu-id="ffcc5-135">Create a file named *PluginLoadContext.cs* in the *AppWithPlugin* folder with the following contents:</span></span>

[!code-csharp[loading-plugins](~/samples/core/extensions/AppWithPlugin/AppWithPlugin/PluginLoadContext.cs)]

<span data-ttu-id="ffcc5-136">`PluginLoadContext` 類型衍生自 <xref:System.Runtime.Loader.AssemblyLoadContext>。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-136">The `PluginLoadContext` type derives from <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="ffcc5-137">`AssemblyLoadContext` 類型是執行階段中的一種特殊類型，可讓開發人員將載入的組件隔離到不同的群組，以確保組件版本不會衝突。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-137">The `AssemblyLoadContext` type is a special type in the runtime that allows developers to isolate loaded assemblies into different groups to ensure that assembly versions do not conflict.</span></span> <span data-ttu-id="ffcc5-138">此外，自訂 `AssemblyLoadContext` 可以選擇要從中載入組件的不同路徑，並覆寫預設行為。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-138">Additionally, a custom `AssemblyLoadContext` can choose different paths to load assemblies from and override the default behavior.</span></span> <span data-ttu-id="ffcc5-139">`PluginLoadContext` 使用 .NET Core 3.0 中引進的 `AssemblyDependencyResolver` 類型執行個體，將組件名稱解析為路徑。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-139">The `PluginLoadContext` uses an instance of the `AssemblyDependencyResolver` type introduced in .NET Core 3.0 to resolve assembly names to paths.</span></span> <span data-ttu-id="ffcc5-140">`AssemblyDependencyResolver` 物件是以 .NET 類別庫路徑所建構。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-140">The `AssemblyDependencyResolver` object is constructed with the path to a .NET class library.</span></span> <span data-ttu-id="ffcc5-141">它會根據其路徑已傳遞至 `AssemblyDependencyResolver` 建構函式的類別庫檔案 *deps.json*，將組件和原生程式庫解析為其相對路徑。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-141">It resolves assemblies and native libraries to their relative paths based on the *deps.json* file for the class library whose path was passed to the `AssemblyDependencyResolver` constructor.</span></span> <span data-ttu-id="ffcc5-142">自訂 `AssemblyLoadContext` 可讓外掛程式具有自己的相依性，而 `AssemblyDependencyResolver` 可讓您輕鬆正確地載入相依性。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-142">The custom `AssemblyLoadContext` enables plugins to have their own dependencies, and the `AssemblyDependencyResolver` makes it easy to correctly load the dependencies.</span></span>

<span data-ttu-id="ffcc5-143">現在 `AppWithPlugin` 專案具有 `PluginLoadContext` 類型，請以下列主體更新 `Program.LoadPlugin` 方法：</span><span class="sxs-lookup"><span data-stu-id="ffcc5-143">Now that the `AppWithPlugin` project has the `PluginLoadContext` type, update the `Program.LoadPlugin` method with the following body:</span></span>

```csharp
static Assembly LoadPlugin(string relativePath)
{
    // Navigate up to the solution root
    string root = Path.GetFullPath(Path.Combine(
        Path.GetDirectoryName(
            Path.GetDirectoryName(
                Path.GetDirectoryName(
                    Path.GetDirectoryName(
                        Path.GetDirectoryName(typeof(Program).Assembly.Location)))))));

    string pluginLocation = Path.GetFullPath(Path.Combine(root, relativePath.Replace('\\', Path.DirectorySeparatorChar)));
    Console.WriteLine($"Loading commands from: {pluginLocation}");
    PluginLoadContext loadContext = new PluginLoadContext(pluginLocation);
    return loadContext.LoadFromAssemblyName(new AssemblyName(Path.GetFileNameWithoutExtension(pluginLocation)));
}
```

<span data-ttu-id="ffcc5-144">藉由對每個外掛程式使用不同的 `PluginLoadContext` 執行個體，外掛程式就可以有不同或甚至衝突的相依性，而不會發生問題。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-144">By using a different `PluginLoadContext` instance for each plugin, the plugins can have different or even conflicting dependencies without issue.</span></span>

## <a name="create-a-simple-plugin-with-no-dependencies"></a><span data-ttu-id="ffcc5-145">建立沒有相依性的簡單外掛程式</span><span class="sxs-lookup"><span data-stu-id="ffcc5-145">Create a simple plugin with no dependencies</span></span>

<span data-ttu-id="ffcc5-146">回到根資料夾，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ffcc5-146">Back in the root folder, do the following:</span></span>

1. <span data-ttu-id="ffcc5-147">執行 `dotnet new classlib -o HelloPlugin` 以建立名為 `HelloPlugin` 的新類別庫專案。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-147">Run `dotnet new classlib -o HelloPlugin` to create a new class library project named `HelloPlugin`.</span></span>
2. <span data-ttu-id="ffcc5-148">執行 `dotnet sln add HelloPlugin/HelloPlugin.csproj` 以將專案新增至 `AppWithPlugin` 方案。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-148">Run `dotnet sln add HelloPlugin/HelloPlugin.csproj` to add the project to the `AppWithPlugin` solution.</span></span> 
3. <span data-ttu-id="ffcc5-149">使用下列內容，以名為 *HelloCommand.cs* 的檔案取代名為 *HelloPlugin/Class1.cs* 的檔案：</span><span class="sxs-lookup"><span data-stu-id="ffcc5-149">Replace the *HelloPlugin/Class1.cs* file with a file named *HelloCommand.cs* with the following contents:</span></span>

[!code-csharp[the-hello-plugin](~/samples/core/extensions/AppWithPlugin/HelloPlugin/HelloCommand.cs)]

<span data-ttu-id="ffcc5-150">現在，開啟 *HelloPlugin.csproj* 檔案。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-150">Now, open the *HelloPlugin.csproj* file.</span></span> <span data-ttu-id="ffcc5-151">看起來應類似如下：</span><span class="sxs-lookup"><span data-stu-id="ffcc5-151">It should look similar to the following:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

<span data-ttu-id="ffcc5-152">在 `<Project>` 標籤之間，新增下列項目：</span><span class="sxs-lookup"><span data-stu-id="ffcc5-152">In between the `<Project>` tags, add the following elements:</span></span>

```xml
<ItemGroup>
<ProjectReference Include="..\PluginBase\PluginBase.csproj">
    <Private>false</Private>
</ProjectReference>
</ItemGroup>
```

<span data-ttu-id="ffcc5-153">`<Private>false</Private>` 項目非常重要。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-153">The `<Private>false</Private>` element is very important.</span></span> <span data-ttu-id="ffcc5-154">這會指示 MSBuild 不要將 *PluginBase.dll* 複製到 HelloPlugin 的輸出目錄。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-154">This tells MSBuild to not copy *PluginBase.dll* to the output directory for HelloPlugin.</span></span> <span data-ttu-id="ffcc5-155">如果 *PluginBase.dll* 組件存在於輸出目錄中，`PluginLoadContext` 會在其中尋找組件，並在載入 *HelloPlugin.dll* 組件時將它載入。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-155">If the *PluginBase.dll* assembly is present in the output directory, `PluginLoadContext` will find the assembly there and load it when it loads the *HelloPlugin.dll* assembly.</span></span> <span data-ttu-id="ffcc5-156">此時，`HelloPlugin.HelloCommand` 類型會從 `HelloPlugin` 專案輸出目錄中的 *PluginBase.dll* 實作 `ICommand` 介面，而不是實作預設載入內容中所載入的 `ICommand` 介面。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-156">At this point, the `HelloPlugin.HelloCommand` type will implement the `ICommand` interface from the *PluginBase.dll* in the output directory of the `HelloPlugin` project, not the `ICommand` interface that is loaded into the default load context.</span></span> <span data-ttu-id="ffcc5-157">因為執行階段將這兩種類型視為不同組件的不同類型，所以 `AppWithPlugin.Program.CreateCommands` 方法將找不到命令。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-157">Since the runtime sees these two types as different types from different assemblies, the `AppWithPlugin.Program.CreateCommands` method will not find the commands.</span></span> <span data-ttu-id="ffcc5-158">因此，需要 `<Private>false</Private>` 中繼資料才能參考含有外掛程式介面的組件。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-158">As a result, the `<Private>false</Private>` metadata is required for the reference to the assembly containing the plugin interfaces.</span></span>

<span data-ttu-id="ffcc5-159">現在 `HelloPlugin` 專案已完成，我們應該更新 `AppWithPlugin` 專案以了解何處可以找到 `HelloPlugin` 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-159">Now that the `HelloPlugin` project is complete, we should update the `AppWithPlugin` project to know where the `HelloPlugin` plugin can be found.</span></span> <span data-ttu-id="ffcc5-160">在 `// Paths to plugins to load` 註解後面，新增 `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` 作為 `pluginPaths` 陣列的項目。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-160">After the `// Paths to plugins to load` comment, add `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` as an element of the `pluginPaths` array.</span></span>

## <a name="create-a-plugin-with-library-dependencies"></a><span data-ttu-id="ffcc5-161">建立具有程式庫相依性的外掛程式</span><span class="sxs-lookup"><span data-stu-id="ffcc5-161">Create a plugin with library dependencies</span></span>

<span data-ttu-id="ffcc5-162">幾乎所有外掛程式都比簡單的 "Hello World" 還要複雜，且許多外掛程式都會相依於其他程式庫。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-162">Almost all plugins are more complex than a simple "Hello World", and many plugins have dependencies on other libraries.</span></span> <span data-ttu-id="ffcc5-163">範例中的 `JsonPlugin` 和 `OldJson` 外掛程式專案示範兩個外掛程式，其中包含相依於 `Newtonsoft.Json` 的 NuGet 套件相依性。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-163">The `JsonPlugin` and `OldJson` plugin projects in the sample show two examples of plugins with NuGet package dependencies on `Newtonsoft.Json`.</span></span> <span data-ttu-id="ffcc5-164">專案檔本身並沒有專案參考的任何特殊資訊，且 (在新增 `pluginPaths` 陣列的外掛程式路徑之後) 外掛程式會完美執行，即使在執行相同的 AppWithPlugin 應用程式同時執行也一樣。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-164">The project files themselves do not have any special information for the project references, and (after adding the plugin paths to the `pluginPaths` array) the plugins run perfectly, even if run in the same execution of the AppWithPlugin app.</span></span> <span data-ttu-id="ffcc5-165">不過，這些專案不會將參考的組件複製到其輸出目錄，因此組件必須存在於使用者的電腦上，外掛程式才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-165">However, these projects do not copy the referenced assemblies to their output directory, so the assemblies need to be present on the user's machine for the plugins to work.</span></span> <span data-ttu-id="ffcc5-166">此問題有兩個解決方法。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-166">There are two ways to work around this problem.</span></span> <span data-ttu-id="ffcc5-167">第一個選項是使用 `dotnet publish` 命令來發佈類別庫。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-167">The first option is to use the `dotnet publish` command to publish the class library.</span></span> <span data-ttu-id="ffcc5-168">或者，如果您想要能夠使用外掛程式的 `dotnet build` 輸出，您可以在外掛程式專案檔的 `<PropertyGroup>` 標籤之間新增 `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` 屬性。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-168">Alternatively, if you want to be able to use the output of `dotnet build` for your plugin, you can add the `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` property between the `<PropertyGroup>` tags in the plugin's project file.</span></span> <span data-ttu-id="ffcc5-169">如需範例，請參閱 `XcopyablePlugin` 外掛程式專案。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-169">See the `XcopyablePlugin` plugin project for an example.</span></span>

## <a name="other-plugin-examples-in-the-sample"></a><span data-ttu-id="ffcc5-170">範例中的其他外掛程式示範</span><span class="sxs-lookup"><span data-stu-id="ffcc5-170">Other plugin examples in the sample</span></span>

<span data-ttu-id="ffcc5-171">在 [the dotnet/samples 存放庫](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin)中可以找到此教學課程的完整原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-171">The complete source code for this tutorial can be found in [the dotnet/samples repository](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span> <span data-ttu-id="ffcc5-172">完整的範例包含 `AssemblyDependencyResolver` 行為的一些其他範例。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-172">The completed sample includes a few other examples of `AssemblyDependencyResolver` behavior.</span></span> <span data-ttu-id="ffcc5-173">例如，`AssemblyDependencyResolver` 物件也可以解析 NuGet 套件隨附的原生程式庫，以及當地語系化附屬組件。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-173">For example, the `AssemblyDependencyResolver` object can also resolve native libraries as well as localized satellite assemblies included in NuGet packages.</span></span> <span data-ttu-id="ffcc5-174">範例存放庫中的 `UVPlugin` 和 `FrenchPlugin` 示範了這些案例。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-174">The `UVPlugin` and `FrenchPlugin` in the samples repository demonstrate these scenarios.</span></span>

## <a name="how-to-reference-a-plugin-interface-assembly-defined-in-a-nuget-package"></a><span data-ttu-id="ffcc5-175">如何參考 NuGet 套件中所定義的外掛程式介面組件</span><span class="sxs-lookup"><span data-stu-id="ffcc5-175">How to reference a plugin interface assembly defined in a NuGet package</span></span>

<span data-ttu-id="ffcc5-176">假設應用程式 A 在 NuGet 套件中定義了名為 `A.PluginBase` 的外掛程式介面。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-176">Let's say that there is an app A that has a plugin interface defined in the NuGet package named `A.PluginBase`.</span></span> <span data-ttu-id="ffcc5-177">如何在您的外掛程式專案中正確地參考套件？</span><span class="sxs-lookup"><span data-stu-id="ffcc5-177">How do you reference the package correctly in your plugin project?</span></span> <span data-ttu-id="ffcc5-178">針對專案參考，在專案檔中的 `ProjectReference` 項目上使用 `<Private>false</Private>` 中繼資料可防止將 DLL 複製到輸出。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-178">For project references, using the `<Private>false</Private>` metadata on the `ProjectReference` element in the project file prevented the dll from being copied to the output.</span></span>

<span data-ttu-id="ffcc5-179">若要正確地參考 `A.PluginBase` 套件，您需要將專案檔中的 `<PackageReference>` 項目變更如下：</span><span class="sxs-lookup"><span data-stu-id="ffcc5-179">To correctly reference the `A.PluginBase` package, you want to change the `<PackageReference>` element in the project file to the following:</span></span>

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

<span data-ttu-id="ffcc5-180">這可防止將 `A.PluginBase` 組件複製到您外掛程式的輸出目錄，並確保外掛程式將會使用 A 的 `A.PluginBase` 版本。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-180">This prevents the `A.PluginBase` assemblies from being copied to the output directory of your plugin and ensures that your plugin will use A's version of `A.PluginBase`.</span></span>

## <a name="plugin-target-framework-recommendations"></a><span data-ttu-id="ffcc5-181">外掛程式目標 Framework 建議</span><span class="sxs-lookup"><span data-stu-id="ffcc5-181">Plugin target framework recommendations</span></span>

<span data-ttu-id="ffcc5-182">因為外掛程式相依性載入使用 *deps.json* 檔案，所以所有外掛程式的目標 Framework 會有相關的 gotcha。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-182">Because plugin dependency loading uses the *deps.json* file, there is a gotcha related to the plugin's target framework.</span></span> <span data-ttu-id="ffcc5-183">具體來說，您的外掛程式應以執行階段為目標 (例如 .NET Core 3.0)，而不是 .NET Standard 版本。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-183">Specifically, your plugins should target a runtime, such as .NET Core 3.0, instead of a version of .NET Standard.</span></span> <span data-ttu-id="ffcc5-184">`deps.json` 檔案是根據專案的目標 Framework 所產生，由於許多 .NET Standard 相容套件提供可對 .NET Standard 建置之參考組件和適用於特定執行階段的實作組件，因此 `deps.json` 可能無法正確地看到實作組件，或可能捕捉 .NET Standard 版的組件，而不是您預期的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="ffcc5-184">The `deps.json` file is generated based on which framework the project targets, and since many .NET Standard-compatible packages ship reference assemblies for building against .NET Standard and implementation assemblies for specific runtimes, the `deps.json` may not correctly see implementation assemblies, or it may grab the .NET Standard version of an assembly instead of the .NET Core version you expect.</span></span>

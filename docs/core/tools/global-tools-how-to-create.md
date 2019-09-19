---
title: 如何建立 .NET Core 通用工具
description: 描述如何建立通用工具。 通用工具是透過 .NET Core CLI 安裝的主控台應用程式。
author: Thraka
ms.author: adegeo
ms.date: 08/22/2018
ms.openlocfilehash: 5c2b1e459f0308f5f96eb041c10f4d7a7ae0ca20
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117440"
---
# <a name="create-a-net-core-global-tool-using-the-net-core-cli"></a><span data-ttu-id="09c75-104">使用 .NET Core CLI 建立 .NET Core 通用工具</span><span class="sxs-lookup"><span data-stu-id="09c75-104">Create a .NET Core Global Tool using the .NET Core CLI</span></span>

<span data-ttu-id="09c75-105">本文會教導您如何建立及封裝 .NET Core 通用工具。</span><span class="sxs-lookup"><span data-stu-id="09c75-105">This article teaches you how to create and package a .NET Core Global Tool.</span></span> <span data-ttu-id="09c75-106">.NET Core CLI 可讓您建立作為通用工具的主控台應用程式，其他人也可以輕鬆地安裝及執行該工具。</span><span class="sxs-lookup"><span data-stu-id="09c75-106">The .NET Core CLI allows you to create a console application as a Global Tool, which others can easily install and run.</span></span> <span data-ttu-id="09c75-107">.NET Core 通用工具是從 .NET Core CLI 安裝的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="09c75-107">.NET Core Global Tools are NuGet packages that are installed from the .NET Core CLI.</span></span> <span data-ttu-id="09c75-108">如需通用工具的詳細資訊，請參閱 [.NET Core 通用工具概觀](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="09c75-108">For more information about Global Tools, see [.NET Core Global Tools overview](global-tools.md).</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="create-a-project"></a><span data-ttu-id="09c75-109">建立專案</span><span class="sxs-lookup"><span data-stu-id="09c75-109">Create a project</span></span>

<span data-ttu-id="09c75-110">本文使用 .NET Core CLI 來建立和管理專案。</span><span class="sxs-lookup"><span data-stu-id="09c75-110">This article uses the .NET Core CLI to create and manage a project.</span></span>

<span data-ttu-id="09c75-111">我們的範例工具是會產生 ASCII Bot 並列印訊息的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="09c75-111">Our example tool will be a console application that generates an ASCII bot and prints a message.</span></span> <span data-ttu-id="09c75-112">首先，建立新的 .NET Core 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="09c75-112">First, create a new .NET Core Console Application.</span></span>

```dotnetcli
dotnet new console -o botsay
```

<span data-ttu-id="09c75-113">瀏覽至先前命令所建立的 `botsay` 目錄。</span><span class="sxs-lookup"><span data-stu-id="09c75-113">Navigate to the `botsay` directory created by the previous command.</span></span>

## <a name="add-the-code"></a><span data-ttu-id="09c75-114">新增程式碼</span><span class="sxs-lookup"><span data-stu-id="09c75-114">Add the code</span></span>

<span data-ttu-id="09c75-115">使用您慣用的文字編輯器 (例如 `vim` 或[Visual Studio Code](https://code.visualstudio.com/))，開啟 `Program.cs` 檔案。</span><span class="sxs-lookup"><span data-stu-id="09c75-115">Open the `Program.cs` file with your favorite text editor, such as `vim` or [Visual Studio Code](https://code.visualstudio.com/).</span></span>

<span data-ttu-id="09c75-116">將下列 `using` 指示詞新增至檔案頂端，這有助於縮短用來顯示應用程式版本資訊的程式碼。</span><span class="sxs-lookup"><span data-stu-id="09c75-116">Add the following `using` directive to the top of the file, this helps shorten the code to display the version information of the application.</span></span>

```csharp
using System.Reflection;
```

<span data-ttu-id="09c75-117">接下來，向下移動至 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="09c75-117">Next, move down to the `Main` method.</span></span> <span data-ttu-id="09c75-118">使用下列程式碼來取代方法，以處理應用程式的命令列引數。</span><span class="sxs-lookup"><span data-stu-id="09c75-118">Replace the method with the following code to process the command-line arguments for your application.</span></span> <span data-ttu-id="09c75-119">如果未傳遞任何引數，則會顯示簡短的說明訊息。</span><span class="sxs-lookup"><span data-stu-id="09c75-119">If no arguments were passed, a short help message is displayed.</span></span> <span data-ttu-id="09c75-120">否則，所有引數都會轉換成字串並且以 Bot 列印。</span><span class="sxs-lookup"><span data-stu-id="09c75-120">Otherwise, all of those arguments are transformed into a string and printed with the bot.</span></span>

```csharp
static void Main(string[] args)
{
    if (args.Length == 0)
    {
        var versionString = Assembly.GetEntryAssembly()
                                .GetCustomAttribute<AssemblyInformationalVersionAttribute>()
                                .InformationalVersion
                                .ToString();

        Console.WriteLine($"botsay v{versionString}");
        Console.WriteLine("-------------");
        Console.WriteLine("\nUsage:");
        Console.WriteLine("  botsay <message>");
        return;
    }

    ShowBot(string.Join(' ', args));
}
```

### <a name="create-the-bot"></a><span data-ttu-id="09c75-121">建立 Bot</span><span class="sxs-lookup"><span data-stu-id="09c75-121">Create the bot</span></span>

<span data-ttu-id="09c75-122">接下來，新增名為 `ShowBot` 的新方法來採用字串參數。</span><span class="sxs-lookup"><span data-stu-id="09c75-122">Next, add a new method named `ShowBot` that takes a string parameter.</span></span> <span data-ttu-id="09c75-123">這個方法會列印出訊息和 ASCII Bot。</span><span class="sxs-lookup"><span data-stu-id="09c75-123">This method prints out the message and the ASCII bot.</span></span> <span data-ttu-id="09c75-124">ASCII Bot 程式碼取自 [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) 範例。</span><span class="sxs-lookup"><span data-stu-id="09c75-124">The ASCII bot code was taken from the [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) sample.</span></span>

```csharp
static void ShowBot(string message)
{
    string bot = $"\n        {message}";
    bot += @"
    __________________
                      \
                       \
                          ....
                          ....'
                           ....
                        ..........
                    .............'..'..
                 ................'..'.....
               .......'..........'..'..'....
              ........'..........'..'..'.....
             .'....'..'..........'..'.......'.
             .'..................'...   ......
             .  ......'.........         .....
             .    _            __        ......
            ..    #            ##        ......
           ....       .                 .......
           ......  .......          ............
            ................  ......................
            ........................'................
           ......................'..'......    .......
        .........................'..'.....       .......
     ........    ..'.............'..'....      ..........
   ..'..'...      ...............'.......      ..........
  ...'......     ...... ..........  ......         .......
 ...........   .......              ........        ......
.......        '...'.'.              '.'.'.'         ....
.......       .....'..               ..'.....
   ..       ..........               ..'........
          ............               ..............
         .............               '..............
        ...........'..              .'.'............
       ...............              .'.'.............
      .............'..               ..'..'...........
      ...............                 .'..............
       .........                        ..............
        .....
";
    Console.WriteLine(bot);
}
```

### <a name="test-the-tool"></a><span data-ttu-id="09c75-125">測試工具</span><span class="sxs-lookup"><span data-stu-id="09c75-125">Test the tool</span></span>

<span data-ttu-id="09c75-126">執行專案，並查看輸出結果。</span><span class="sxs-lookup"><span data-stu-id="09c75-126">Run the project and see the output.</span></span> <span data-ttu-id="09c75-127">請嘗試這些命令列變化，以查看不同的結果：</span><span class="sxs-lookup"><span data-stu-id="09c75-127">Try these variations of the command-line to see different results:</span></span>

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- hello from the bot
```

<span data-ttu-id="09c75-128">`--` 分隔符號之後的所有引數會傳遞至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="09c75-128">All arguments after the `--` delimiter are passed to your application.</span></span>

## <a name="setup-the-global-tool"></a><span data-ttu-id="09c75-129">安裝通用工具</span><span class="sxs-lookup"><span data-stu-id="09c75-129">Setup the global tool</span></span>

<span data-ttu-id="09c75-130">在您可以將應用程式封裝及散佈為通用工具之前，您應該修改專案檔案。</span><span class="sxs-lookup"><span data-stu-id="09c75-130">Before you can pack and distribute the application as a Global Tool, you need to modify the project file.</span></span> <span data-ttu-id="09c75-131">開啟 `botsay.csproj` 檔案，然後將三個新 XML 節點新增至 `<Project><PropertyGroup>` 節點：</span><span class="sxs-lookup"><span data-stu-id="09c75-131">Open the `botsay.csproj` file and add three new XML nodes to the `<Project><PropertyGroup>` node:</span></span>

- `<PackAsTool>`\
<span data-ttu-id="09c75-132">[必要] 表示會封裝應用程式以安裝為通用工具。</span><span class="sxs-lookup"><span data-stu-id="09c75-132">[REQUIRED] Indicates that the application will be packaged for install as a Global Tool.</span></span>

- `<ToolCommandName>`\
<span data-ttu-id="09c75-133">[選用] 工具的替代名稱，否則工具的命令名稱會跟隨著專案檔案命名。</span><span class="sxs-lookup"><span data-stu-id="09c75-133">[OPTIONAL] An alternative name for the tool, otherwise the command name for the tool will be named after the project file.</span></span> <span data-ttu-id="09c75-134">您在套件中可以有多個工具，選擇唯一且易記的名稱，有助於與相同套件中的其他工具區分。</span><span class="sxs-lookup"><span data-stu-id="09c75-134">You can have multiple tools in a package, choosing a unique and friendly name helps differentiate from other tools in the same package.</span></span>

- `<PackageOutputPath>`\
<span data-ttu-id="09c75-135">[選用] 在其中產生 NuGet 套件的位置。</span><span class="sxs-lookup"><span data-stu-id="09c75-135">[OPTIONAL] Where the NuGet package will be produced.</span></span> <span data-ttu-id="09c75-136">NuGet 套件是 .NET Core CLI 通用工具用來安裝工具的套件。</span><span class="sxs-lookup"><span data-stu-id="09c75-136">The NuGet package is what the .NET Core CLI Global Tools uses to install your tool.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>

    <PackAsTool>true</PackAsTool>
    <ToolCommandName>botsay</ToolCommandName>
    <PackageOutputPath>./nupkg</PackageOutputPath>

  </PropertyGroup>

</Project>
```

<span data-ttu-id="09c75-137">即使 `<PackageOutputPath>` 是選擇性的，請在此範例中使用它。</span><span class="sxs-lookup"><span data-stu-id="09c75-137">Even though `<PackageOutputPath>` is optional, use it in this example.</span></span> <span data-ttu-id="09c75-138">請確定您已設定：`<PackageOutputPath>./nupkg</PackageOutputPath>`。</span><span class="sxs-lookup"><span data-stu-id="09c75-138">Make sure you set it: `<PackageOutputPath>./nupkg</PackageOutputPath>`.</span></span>

<span data-ttu-id="09c75-139">接下來，為您的應用程式建立 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="09c75-139">Next, create a NuGet package for your application.</span></span>

```dotnetcli
dotnet pack
```

<span data-ttu-id="09c75-140">`botsay.1.0.0.nupkg` 檔案是在資料夾 (由 `botsay.csproj` 檔案中的 `<PackageOutputPath>` XML 值識別) 中建立的，在此範例中是 `./nupkg` 資料夾。</span><span class="sxs-lookup"><span data-stu-id="09c75-140">The `botsay.1.0.0.nupkg` file is created in the folder identified by the `<PackageOutputPath>` XML value from the `botsay.csproj` file, which in this example is the `./nupkg` folder.</span></span> <span data-ttu-id="09c75-141">這可讓您輕鬆地安裝和測試。</span><span class="sxs-lookup"><span data-stu-id="09c75-141">This makes it easy to install and test.</span></span> <span data-ttu-id="09c75-142">當您想要公開發行工具時，請將它上傳至 <https://www.nuget.org>。</span><span class="sxs-lookup"><span data-stu-id="09c75-142">When you want to release a tool publicly, upload it to <https://www.nuget.org>.</span></span> <span data-ttu-id="09c75-143">在工具於 NuGet 上可供使用之後，開發人員便可使用 [dotnet tool install](dotnet-tool-install.md) 命令的 `--global` 選項來為所有使用者安裝該工具。</span><span class="sxs-lookup"><span data-stu-id="09c75-143">Once the tool is available on NuGet, developers can perform a user-wide installation of the tool using the `--global` option of the [dotnet tool install](dotnet-tool-install.md) command.</span></span>

<span data-ttu-id="09c75-144">既然您已經有了套件，請從該套件安裝工具：</span><span class="sxs-lookup"><span data-stu-id="09c75-144">Now that you have a package, install the tool from that package:</span></span>

```dotnetcli
dotnet tool install --global --add-source ./nupkg botsay
```

<span data-ttu-id="09c75-145">`--add-source` 參數會告訴 .NET Core CLI 暫時使用 `./nupkg` 資料夾 (我們的 `<PackageOutputPath>` 資料夾) 作為 NuGet 套件的額外來源摘要。</span><span class="sxs-lookup"><span data-stu-id="09c75-145">The `--add-source` parameter tells the .NET Core CLI to temporarily use the `./nupkg` folder (our `<PackageOutputPath>` folder) as an additional source feed for NuGet packages.</span></span> <span data-ttu-id="09c75-146">如需安裝通用工具的詳細資訊，請參閱 [.NET Core 通用工具概觀](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="09c75-146">For more information about installing Global Tools, see [.NET Core Global Tools overview](global-tools.md).</span></span>

<span data-ttu-id="09c75-147">如果安裝成功，則會顯示一則訊息，其中顯示用來呼叫此工具的命令以及安裝的版本，類似於下例範例：</span><span class="sxs-lookup"><span data-stu-id="09c75-147">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: botsay
Tool 'botsay' (version '1.0.0') was successfully installed.
```

<span data-ttu-id="09c75-148">您現在應該可以輸入 `botsay` 並且取得工具的回應。</span><span class="sxs-lookup"><span data-stu-id="09c75-148">You should now be able to type `botsay` and get a response from the tool.</span></span>

> [!NOTE]
> <span data-ttu-id="09c75-149">如果安裝成功，但是您無法使用 `botsay` 命令，您需要開啟新的終端機以重新整理路徑。</span><span class="sxs-lookup"><span data-stu-id="09c75-149">If the install was successful, but you cannot use the `botsay` command, you may need to open a new terminal to refresh the PATH.</span></span>

## <a name="remove-the-tool"></a><span data-ttu-id="09c75-150">移除工具</span><span class="sxs-lookup"><span data-stu-id="09c75-150">Remove the tool</span></span>

<span data-ttu-id="09c75-151">一旦您完成工具的實驗，可以使用下列命令來將它移除：</span><span class="sxs-lookup"><span data-stu-id="09c75-151">Once you're done experimenting with the tool, you can remove it with the following command:</span></span>

```dotnetcli
dotnet tool uninstall -g botsay
```

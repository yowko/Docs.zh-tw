---
title: 教程：創建 .NET 核心工具
description: 瞭解如何創建 .NET 核心工具。 工具是使用 .NET 核心 CLI 安裝的主控台應用程式。
ms.date: 02/12/2020
ms.openlocfilehash: 88cc3be7b149834ace0c5f3ba8ac8c039199908f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156721"
---
# <a name="tutorial-create-a-net-core-tool-using-the-net-core-cli"></a><span data-ttu-id="25ddf-104">教程：使用 .NET 核心 CLI 創建 .NET 核心工具</span><span class="sxs-lookup"><span data-stu-id="25ddf-104">Tutorial: Create a .NET Core tool using the .NET Core CLI</span></span>

<span data-ttu-id="25ddf-105">**本文適用于：✔️** .NET 核心 2.1 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="25ddf-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="25ddf-106">本教程將教您如何創建和打包 .NET 核心工具。</span><span class="sxs-lookup"><span data-stu-id="25ddf-106">This tutorial teaches you how to create and package a .NET Core tool.</span></span> <span data-ttu-id="25ddf-107">.NET Core CLI 允許您創建主控台應用程式作為工具，其他人可以安裝和運行該工具。</span><span class="sxs-lookup"><span data-stu-id="25ddf-107">The .NET Core CLI lets you create a console application as a tool, which others can install and run.</span></span> <span data-ttu-id="25ddf-108">.NET 核心工具是從 .NET 核心 CLI 安裝的 NuGet 套裝軟體。</span><span class="sxs-lookup"><span data-stu-id="25ddf-108">.NET Core tools are NuGet packages that are installed from the .NET Core CLI.</span></span> <span data-ttu-id="25ddf-109">有關工具的詳細資訊，請參閱[.NET 核心工具概述](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="25ddf-109">For more information about tools, see [.NET Core tools overview](global-tools.md).</span></span>

<span data-ttu-id="25ddf-110">您將創建的工具是一個主控台應用程式，該應用程式將消息作為輸入，並將消息與創建機器人圖像的文本行一起顯示。</span><span class="sxs-lookup"><span data-stu-id="25ddf-110">The tool that you'll create is a console application that takes a message as input and displays the message along with lines of text that create the image of a robot.</span></span>

<span data-ttu-id="25ddf-111">這是三個教程系列中的第一個。</span><span class="sxs-lookup"><span data-stu-id="25ddf-111">This is the first in a series of three tutorials.</span></span> <span data-ttu-id="25ddf-112">在本教程中，您將創建和打包工具。</span><span class="sxs-lookup"><span data-stu-id="25ddf-112">In this tutorial, you create and package a tool.</span></span> <span data-ttu-id="25ddf-113">在接下來的兩個教程[中，您將該工具用作全域工具](global-tools-how-to-use.md)[，並將該工具用作本地工具](local-tools-how-to-use.md)。</span><span class="sxs-lookup"><span data-stu-id="25ddf-113">In the next two tutorials you [use the tool as a global tool](global-tools-how-to-use.md) and [use the tool as a local tool](local-tools-how-to-use.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="25ddf-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="25ddf-114">Prerequisites</span></span>

- <span data-ttu-id="25ddf-115">[.NET 核心 SDK 3.1](https://dotnet.microsoft.com/download)或更高版本。</span><span class="sxs-lookup"><span data-stu-id="25ddf-115">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) or a later version.</span></span>

  <span data-ttu-id="25ddf-116">本教程和[以下全域工具教程](global-tools-how-to-use.md)適用于 .NET Core SDK 2.1 和更高版本，因為全域工具可從該版本開始使用。</span><span class="sxs-lookup"><span data-stu-id="25ddf-116">This tutorial and the following [tutorial for global tools](global-tools-how-to-use.md) apply to .NET Core SDK 2.1 and later versions because global tools are available starting in that version.</span></span> <span data-ttu-id="25ddf-117">但本教程假定您已經安裝了 3.1 或更高版本，以便您可以選擇繼續使用[本地工具教程](local-tools-how-to-use.md)。</span><span class="sxs-lookup"><span data-stu-id="25ddf-117">But this tutorial assumes you have installed 3.1 or later so that you have the option of continuing on to the [local tools tutorial](local-tools-how-to-use.md).</span></span> <span data-ttu-id="25ddf-118">本地工具可從 .NET 核心 SDK 3.0 中開始。</span><span class="sxs-lookup"><span data-stu-id="25ddf-118">Local tools are available starting in .NET Core SDK 3.0.</span></span> <span data-ttu-id="25ddf-119">無論將其用作全域工具還是將工具用作本地工具，創建工具的過程都是相同的。</span><span class="sxs-lookup"><span data-stu-id="25ddf-119">The procedures for creating a tool are the same whether you use it as a global tool or as a local tool.</span></span>
  
- <span data-ttu-id="25ddf-120">您偏好的文字編輯器或程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="25ddf-120">A text editor or code editor of your choice.</span></span>

## <a name="create-a-project"></a><span data-ttu-id="25ddf-121">建立專案</span><span class="sxs-lookup"><span data-stu-id="25ddf-121">Create a project</span></span>

1. <span data-ttu-id="25ddf-122">打開命令提示符並創建名為*存儲庫*的資料夾。</span><span class="sxs-lookup"><span data-stu-id="25ddf-122">Open a command prompt and create a folder named *repository*.</span></span>

1. <span data-ttu-id="25ddf-123">導航到*存儲庫*資料夾並輸入以下命令：</span><span class="sxs-lookup"><span data-stu-id="25ddf-123">Navigate to the *repository* folder and enter the following command:</span></span>

   ```dotnetcli
   dotnet new console -n microsoft.botsay
   ```

   <span data-ttu-id="25ddf-124">該命令在*存儲庫*資料夾下創建名為*microsoft.botsay*的新資料夾。</span><span class="sxs-lookup"><span data-stu-id="25ddf-124">The command creates a new folder named *microsoft.botsay* under the *repository* folder.</span></span>

1. <span data-ttu-id="25ddf-125">導航到*microsoft.botsay*資料夾。</span><span class="sxs-lookup"><span data-stu-id="25ddf-125">Navigate to the *microsoft.botsay* folder.</span></span>

   ```console
   cd microsoft.botsay
   ```

## <a name="add-the-code"></a><span data-ttu-id="25ddf-126">新增程式碼</span><span class="sxs-lookup"><span data-stu-id="25ddf-126">Add the code</span></span>

1. <span data-ttu-id="25ddf-127">使用代碼`Program.cs`編輯器打開該檔。</span><span class="sxs-lookup"><span data-stu-id="25ddf-127">Open the `Program.cs` file with your code editor.</span></span>

1. <span data-ttu-id="25ddf-128">將以下`using`指令添加到檔頂部：</span><span class="sxs-lookup"><span data-stu-id="25ddf-128">Add the following `using` directive to the top of the file:</span></span>

   ```csharp
   using System.Reflection;
   ```

1. <span data-ttu-id="25ddf-129">將`Main`方法替換為以下代碼，以處理應用程式的命令列參數。</span><span class="sxs-lookup"><span data-stu-id="25ddf-129">Replace the `Main` method with the following code to process the command-line arguments for the application.</span></span>

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

   <span data-ttu-id="25ddf-130">如果未傳遞任何參數，則會顯示一條簡短的説明消息。</span><span class="sxs-lookup"><span data-stu-id="25ddf-130">If no arguments are passed, a short help message is displayed.</span></span> <span data-ttu-id="25ddf-131">否則，所有參數都串聯到單個字串中，並通過調用在下一步中創建`ShowBot`的方法進行列印。</span><span class="sxs-lookup"><span data-stu-id="25ddf-131">Otherwise, all of the arguments are concatenated into a single string and printed by calling the `ShowBot` method that you create in the next step.</span></span>

1. <span data-ttu-id="25ddf-132">添加名為採用`ShowBot`字串參數的新方法。</span><span class="sxs-lookup"><span data-stu-id="25ddf-132">Add a new method named `ShowBot` that takes a string parameter.</span></span> <span data-ttu-id="25ddf-133">該方法使用文本行列印出機器人的消息和圖像。</span><span class="sxs-lookup"><span data-stu-id="25ddf-133">The method prints out the message and an image of a robot using lines of text.</span></span>

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

1. <span data-ttu-id="25ddf-134">儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="25ddf-134">Save your changes.</span></span>

## <a name="test-the-application"></a><span data-ttu-id="25ddf-135">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="25ddf-135">Test the application</span></span>

<span data-ttu-id="25ddf-136">執行專案，並查看輸出結果。</span><span class="sxs-lookup"><span data-stu-id="25ddf-136">Run the project and see the output.</span></span> <span data-ttu-id="25ddf-137">在命令列嘗試這些變體以查看不同的結果：</span><span class="sxs-lookup"><span data-stu-id="25ddf-137">Try these variations at the command line to see different results:</span></span>

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

<span data-ttu-id="25ddf-138">`--` 分隔符號之後的所有引數會傳遞至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="25ddf-138">All arguments after the `--` delimiter are passed to your application.</span></span>

## <a name="package-the-tool"></a><span data-ttu-id="25ddf-139">打包工具</span><span class="sxs-lookup"><span data-stu-id="25ddf-139">Package the tool</span></span>

<span data-ttu-id="25ddf-140">在將應用程式打包並分發為工具之前，需要修改專案檔案。</span><span class="sxs-lookup"><span data-stu-id="25ddf-140">Before you can pack and distribute the application as a tool, you need to modify the project file.</span></span>

1. <span data-ttu-id="25ddf-141">打開*Microsoft.botsay.csproj*檔，並在`<PropertyGroup>`節點的末尾添加新的 XML 節點：</span><span class="sxs-lookup"><span data-stu-id="25ddf-141">Open the *microsoft.botsay.csproj* file and add three new XML nodes to the end of the `<PropertyGroup>` node:</span></span>

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   <span data-ttu-id="25ddf-142">`<ToolCommandName>`是一個可選元素，用於指定在安裝工具後調用該工具的命令。</span><span class="sxs-lookup"><span data-stu-id="25ddf-142">`<ToolCommandName>` is an optional element that specifies the command that will invoke the tool after it's installed.</span></span> <span data-ttu-id="25ddf-143">如果未提供此元素，該工具的命令名稱是沒有 *.csproj*副檔名的專案檔案名。</span><span class="sxs-lookup"><span data-stu-id="25ddf-143">If this element isn't provided, the command name for the tool is the project file name without the *.csproj* extension.</span></span>

   <span data-ttu-id="25ddf-144">`<PackageOutputPath>`是確定 NuGet 包的可選元素。</span><span class="sxs-lookup"><span data-stu-id="25ddf-144">`<PackageOutputPath>` is an optional element that determines where the NuGet package will be produced.</span></span> <span data-ttu-id="25ddf-145">NuGet 包是 .NET 核心 CLI 用於安裝工具的內容。</span><span class="sxs-lookup"><span data-stu-id="25ddf-145">The NuGet package is what the .NET Core CLI uses to install your tool.</span></span>

   <span data-ttu-id="25ddf-146">專案檔案現在類似于以下示例：</span><span class="sxs-lookup"><span data-stu-id="25ddf-146">The project file now looks like the following example:</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">
  
     <PropertyGroup>

       <OutputType>Exe</OutputType>
       <TargetFramework>netcoreapp3.1</TargetFramework>
  
       <PackAsTool>true</PackAsTool>
       <ToolCommandName>botsay</ToolCommandName>
       <PackageOutputPath>./nupkg</PackageOutputPath>
  
     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="25ddf-147">通過運行[dotnet 包](dotnet-pack.md)命令創建 NuGet 包：</span><span class="sxs-lookup"><span data-stu-id="25ddf-147">Create a NuGet package by running the [dotnet pack](dotnet-pack.md) command:</span></span>

   ```dotnetcli
   dotnet pack
   ```

   <span data-ttu-id="25ddf-148">*Microsoft.botsay.1.0.0.nupkg*檔在`<PackageOutputPath>`*Microsoft.botsay.csproj*檔中的值標識的資料夾中創建，在此示例中是 *./nupkg*資料夾。</span><span class="sxs-lookup"><span data-stu-id="25ddf-148">The *microsoft.botsay.1.0.0.nupkg* file is created in the folder identified by the `<PackageOutputPath>` value from the *microsoft.botsay.csproj* file, which in this example is the *./nupkg* folder.</span></span>
  
   <span data-ttu-id="25ddf-149">當您想要公開發布工具時，可以將其上載到`https://www.nuget.org`。</span><span class="sxs-lookup"><span data-stu-id="25ddf-149">When you want to release a tool publicly, you can upload it to `https://www.nuget.org`.</span></span> <span data-ttu-id="25ddf-150">在 NuGet 上提供該工具後，開發人員可以使用[dotnet 工具安裝命令安裝](dotnet-tool-install.md)該工具。</span><span class="sxs-lookup"><span data-stu-id="25ddf-150">Once the tool is available on NuGet, developers can install the tool by using the [dotnet tool install](dotnet-tool-install.md) command.</span></span> <span data-ttu-id="25ddf-151">在本教程中，您直接從本地*nupkg*資料夾中安裝包，因此無需將包上載到 NuGet。</span><span class="sxs-lookup"><span data-stu-id="25ddf-151">For this tutorial you install the package directly from the local *nupkg* folder, so there's no need to upload the package to NuGet.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="25ddf-152">疑難排解</span><span class="sxs-lookup"><span data-stu-id="25ddf-152">Troubleshoot</span></span>

<span data-ttu-id="25ddf-153">如果您在學習本教程時收到錯誤訊息，請參閱[疑難排解 .NET Core 工具使用問題](troubleshoot-usage-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="25ddf-153">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="25ddf-154">後續步驟</span><span class="sxs-lookup"><span data-stu-id="25ddf-154">Next steps</span></span>

<span data-ttu-id="25ddf-155">在本教程中，您創建了一個主控台應用程式，並將其打包為工具。</span><span class="sxs-lookup"><span data-stu-id="25ddf-155">In this tutorial, you created a console application and packaged it as a tool.</span></span> <span data-ttu-id="25ddf-156">要瞭解如何將該工具用作全域工具，請先進行下一教程。</span><span class="sxs-lookup"><span data-stu-id="25ddf-156">To learn how to use the tool as a global tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="25ddf-157">安裝和使用全域工具</span><span class="sxs-lookup"><span data-stu-id="25ddf-157">Install and use a global tool</span></span>](global-tools-how-to-use.md)

<span data-ttu-id="25ddf-158">如果您願意，可以跳過全域工具教程，然後直接轉到本地工具教程。</span><span class="sxs-lookup"><span data-stu-id="25ddf-158">If you prefer, you can skip the global tools tutorial and go directly to the local tools tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="25ddf-159">安裝和使用本機工具</span><span class="sxs-lookup"><span data-stu-id="25ddf-159">Install and use a local tool</span></span>](local-tools-how-to-use.md)

---
title: 教學課程：建立 .NET 工具
description: 瞭解如何建立 .NET 工具。 工具是使用 .NET CLI 安裝的主控台應用程式。
ms.topic: tutorial
ms.date: 12/14/2020
ms.openlocfilehash: dc5cf014336848ff1a3035647a386419653a083b
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633893"
---
# <a name="tutorial-create-a-net-tool-using-the-net-cli"></a><span data-ttu-id="34b48-104">教學課程：使用 .NET CLI 建立 .NET 工具</span><span class="sxs-lookup"><span data-stu-id="34b48-104">Tutorial: Create a .NET tool using the .NET CLI</span></span>

<span data-ttu-id="34b48-105">本文 **適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="34b48-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="34b48-106">本教學課程會教您如何建立和封裝 .NET 工具。</span><span class="sxs-lookup"><span data-stu-id="34b48-106">This tutorial teaches you how to create and package a .NET tool.</span></span> <span data-ttu-id="34b48-107">.NET CLI 可讓您以工具的形式建立主控台應用程式，讓其他人可以安裝和執行。</span><span class="sxs-lookup"><span data-stu-id="34b48-107">The .NET CLI lets you create a console application as a tool, which others can install and run.</span></span> <span data-ttu-id="34b48-108">.NET 工具是從 .NET CLI 安裝的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="34b48-108">.NET tools are NuGet packages that are installed from the .NET CLI.</span></span> <span data-ttu-id="34b48-109">如需工具的詳細資訊，請參閱 [.net 工具總覽](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="34b48-109">For more information about tools, see [.NET tools overview](global-tools.md).</span></span>

<span data-ttu-id="34b48-110">您將建立的工具是主控台應用程式，它會將訊息做為輸入，並顯示訊息以及建立機器人影像的文字行。</span><span class="sxs-lookup"><span data-stu-id="34b48-110">The tool that you'll create is a console application that takes a message as input and displays the message along with lines of text that create the image of a robot.</span></span>

<span data-ttu-id="34b48-111">這是一系列三個教學課程中的第一個。</span><span class="sxs-lookup"><span data-stu-id="34b48-111">This is the first in a series of three tutorials.</span></span> <span data-ttu-id="34b48-112">在本教學課程中，您會建立並封裝工具。</span><span class="sxs-lookup"><span data-stu-id="34b48-112">In this tutorial, you create and package a tool.</span></span> <span data-ttu-id="34b48-113">在接下來的兩個教學課程中，您將 [使用此工具作為全域工具](global-tools-how-to-use.md) ，並 [使用此工具作為本機工具](local-tools-how-to-use.md)。</span><span class="sxs-lookup"><span data-stu-id="34b48-113">In the next two tutorials you [use the tool as a global tool](global-tools-how-to-use.md) and [use the tool as a local tool](local-tools-how-to-use.md).</span></span> <span data-ttu-id="34b48-114">無論您使用的是全域工具或本機工具，建立工具的程式都相同。</span><span class="sxs-lookup"><span data-stu-id="34b48-114">The procedures for creating a tool are the same whether you use it as a global tool or as a local tool.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="34b48-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="34b48-115">Prerequisites</span></span>

- <span data-ttu-id="34b48-116">[.NET SDK 5.0.100](https://dotnet.microsoft.com/download) 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="34b48-116">[.NET SDK 5.0.100](https://dotnet.microsoft.com/download) or a later version.</span></span>

  <span data-ttu-id="34b48-117">本教學課程使用 .NET SDK 5.0，但從 .NET Core SDK 2.1 開始提供通用工具。</span><span class="sxs-lookup"><span data-stu-id="34b48-117">This tutorial uses .NET SDK 5.0, but global tools are available starting in .NET Core SDK 2.1.</span></span> <span data-ttu-id="34b48-118">從 .NET Core SDK 3.0 開始提供本機工具。</span><span class="sxs-lookup"><span data-stu-id="34b48-118">Local tools are available starting in .NET Core SDK 3.0.</span></span>

- <span data-ttu-id="34b48-119">您偏好的文字編輯器或程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="34b48-119">A text editor or code editor of your choice.</span></span>

## <a name="create-a-project"></a><span data-ttu-id="34b48-120">建立專案</span><span class="sxs-lookup"><span data-stu-id="34b48-120">Create a project</span></span>

1. <span data-ttu-id="34b48-121">開啟命令提示字元，並建立名為「存放 *庫*」的資料夾。</span><span class="sxs-lookup"><span data-stu-id="34b48-121">Open a command prompt and create a folder named *repository*.</span></span>

1. <span data-ttu-id="34b48-122">流覽至存放 *庫* 資料夾，並輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="34b48-122">Navigate to the *repository* folder and enter the following command:</span></span>

   ```dotnetcli
   dotnet new console -n microsoft.botsay -f net5.0
   ```

   <span data-ttu-id="34b48-123">此命令會在存放 *庫* 資料夾下建立名為 *botsay* 的新資料夾。</span><span class="sxs-lookup"><span data-stu-id="34b48-123">The command creates a new folder named *microsoft.botsay* under the *repository* folder.</span></span>

   > [!NOTE]
   > <span data-ttu-id="34b48-124">在本教學課程中，您將建立以 .NET 5.0 為目標的工具。</span><span class="sxs-lookup"><span data-stu-id="34b48-124">For this tutorial you create a tool that targets .NET 5.0.</span></span> <span data-ttu-id="34b48-125">若要以不同的架構為目標，請變更 `-f|--framework` 選項。</span><span class="sxs-lookup"><span data-stu-id="34b48-125">To target a different framework, change the `-f|--framework` option.</span></span> <span data-ttu-id="34b48-126">若要以多個架構為目標，請將 `TargetFramework` 專案變更為 `TargetFrameworks` 專案檔中的元素，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="34b48-126">To target multiple frameworks, change the `TargetFramework` element to a `TargetFrameworks` element in the project file, as shown in the following example:</span></span>
   >
   > ```xml
   > <Project Sdk="Microsoft.NET.Sdk">
   >   <PropertyGroup>
   >     <OutputType>Exe</OutputType>
   >     <TargetFrameworks>netcoreapp3.1;net5.0</TargetFrameworks>
   >   </PropertyGroup>
   > </Project>
   > ```

1. <span data-ttu-id="34b48-127">流覽至 *botsay* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="34b48-127">Navigate to the *microsoft.botsay* folder.</span></span>

   ```console
   cd microsoft.botsay
   ```

## <a name="add-the-code"></a><span data-ttu-id="34b48-128">新增程式碼</span><span class="sxs-lookup"><span data-stu-id="34b48-128">Add the code</span></span>

1. <span data-ttu-id="34b48-129">`Program.cs`使用您的程式碼編輯器開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="34b48-129">Open the `Program.cs` file with your code editor.</span></span>

1. <span data-ttu-id="34b48-130">將下列指示詞新增 `using` 至檔案頂端：</span><span class="sxs-lookup"><span data-stu-id="34b48-130">Add the following `using` directive to the top of the file:</span></span>

   ```csharp
   using System.Reflection;
   ```

1. <span data-ttu-id="34b48-131">`Main`以下列程式碼取代方法，以處理應用程式的命令列引數。</span><span class="sxs-lookup"><span data-stu-id="34b48-131">Replace the `Main` method with the following code to process the command-line arguments for the application.</span></span>

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

   <span data-ttu-id="34b48-132">如果未傳遞任何引數，則會顯示簡短的說明訊息。</span><span class="sxs-lookup"><span data-stu-id="34b48-132">If no arguments are passed, a short help message is displayed.</span></span> <span data-ttu-id="34b48-133">否則，所有引數都會串連成單一字串，並藉由呼叫 `ShowBot` 您在下一個步驟中建立的方法來列印。</span><span class="sxs-lookup"><span data-stu-id="34b48-133">Otherwise, all of the arguments are concatenated into a single string and printed by calling the `ShowBot` method that you create in the next step.</span></span>

1. <span data-ttu-id="34b48-134">加入名為的新方法 `ShowBot` ，這個方法接受字串參數。</span><span class="sxs-lookup"><span data-stu-id="34b48-134">Add a new method named `ShowBot` that takes a string parameter.</span></span> <span data-ttu-id="34b48-135">方法會使用文字行來印出訊息和機器人的影像。</span><span class="sxs-lookup"><span data-stu-id="34b48-135">The method prints out the message and an image of a robot using lines of text.</span></span>

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

1. <span data-ttu-id="34b48-136">儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="34b48-136">Save your changes.</span></span>

## <a name="test-the-application"></a><span data-ttu-id="34b48-137">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="34b48-137">Test the application</span></span>

<span data-ttu-id="34b48-138">執行專案，並查看輸出結果。</span><span class="sxs-lookup"><span data-stu-id="34b48-138">Run the project and see the output.</span></span> <span data-ttu-id="34b48-139">請在命令列嘗試這些變化，以查看不同的結果：</span><span class="sxs-lookup"><span data-stu-id="34b48-139">Try these variations at the command line to see different results:</span></span>

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

<span data-ttu-id="34b48-140">`--` 分隔符號之後的所有引數會傳遞至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="34b48-140">All arguments after the `--` delimiter are passed to your application.</span></span>

## <a name="package-the-tool"></a><span data-ttu-id="34b48-141">封裝工具</span><span class="sxs-lookup"><span data-stu-id="34b48-141">Package the tool</span></span>

<span data-ttu-id="34b48-142">您必須先修改專案檔，才能將應用程式封裝並散發為工具。</span><span class="sxs-lookup"><span data-stu-id="34b48-142">Before you can pack and distribute the application as a tool, you need to modify the project file.</span></span>

1. <span data-ttu-id="34b48-143">開啟 *botsay .csproj* 檔案，然後將三個新的 XML 節點新增至節點的結尾 `<PropertyGroup>` ：</span><span class="sxs-lookup"><span data-stu-id="34b48-143">Open the *microsoft.botsay.csproj* file and add three new XML nodes to the end of the `<PropertyGroup>` node:</span></span>

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   <span data-ttu-id="34b48-144">`<ToolCommandName>` 是選擇性專案，指定在安裝工具之後將叫用工具的命令。</span><span class="sxs-lookup"><span data-stu-id="34b48-144">`<ToolCommandName>` is an optional element that specifies the command that will invoke the tool after it's installed.</span></span> <span data-ttu-id="34b48-145">如果未提供此元素，則工具的命令名稱是不含 *.csproj* 副檔名的專案檔名稱。</span><span class="sxs-lookup"><span data-stu-id="34b48-145">If this element isn't provided, the command name for the tool is the project file name without the *.csproj* extension.</span></span>

   <span data-ttu-id="34b48-146">`<PackageOutputPath>` 是選擇性元素，可決定將產生 NuGet 套件的位置。</span><span class="sxs-lookup"><span data-stu-id="34b48-146">`<PackageOutputPath>` is an optional element that determines where the NuGet package will be produced.</span></span> <span data-ttu-id="34b48-147">NuGet 套件是 .NET CLI 用來安裝工具的功能。</span><span class="sxs-lookup"><span data-stu-id="34b48-147">The NuGet package is what the .NET CLI uses to install your tool.</span></span>

   <span data-ttu-id="34b48-148">專案檔現在看起來如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="34b48-148">The project file now looks like the following example:</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>

       <OutputType>Exe</OutputType>
       <TargetFramework>net5.0</TargetFramework>

       <PackAsTool>true</PackAsTool>
       <ToolCommandName>botsay</ToolCommandName>
       <PackageOutputPath>./nupkg</PackageOutputPath>

     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="34b48-149">執行 [dotnet pack](dotnet-pack.md) 命令來建立 NuGet 套件：</span><span class="sxs-lookup"><span data-stu-id="34b48-149">Create a NuGet package by running the [dotnet pack](dotnet-pack.md) command:</span></span>

   ```dotnetcli
   dotnet pack
   ```

   <span data-ttu-id="34b48-150">*Nupkg* 檔案會建立在 botsay .csproj 檔案中的值所識別的資料夾中 `<PackageOutputPath>` ，在此範例中為/nupkg 資料夾（在此範例中為資料夾）。</span><span class="sxs-lookup"><span data-stu-id="34b48-150">The *microsoft.botsay.1.0.0.nupkg* file is created in the folder identified by the `<PackageOutputPath>` value from the *microsoft.botsay.csproj* file, which in this example is the *./nupkg* folder.</span></span>

   <span data-ttu-id="34b48-151">當您想要公開發行工具時，可以將它上傳至 `https://www.nuget.org` 。</span><span class="sxs-lookup"><span data-stu-id="34b48-151">When you want to release a tool publicly, you can upload it to `https://www.nuget.org`.</span></span> <span data-ttu-id="34b48-152">當此工具可在 NuGet 上使用時，開發人員可以使用 [dotnet 工具安裝](dotnet-tool-install.md) 命令來安裝此工具。</span><span class="sxs-lookup"><span data-stu-id="34b48-152">Once the tool is available on NuGet, developers can install the tool by using the [dotnet tool install](dotnet-tool-install.md) command.</span></span> <span data-ttu-id="34b48-153">在本教學課程中，您會直接從本機 *nupkg* 資料夾安裝套件，所以不需要將套件上傳至 NuGet。</span><span class="sxs-lookup"><span data-stu-id="34b48-153">For this tutorial you install the package directly from the local *nupkg* folder, so there's no need to upload the package to NuGet.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="34b48-154">疑難排解</span><span class="sxs-lookup"><span data-stu-id="34b48-154">Troubleshoot</span></span>

<span data-ttu-id="34b48-155">如果您在遵循本教學課程時收到錯誤訊息，請參閱 [疑難排解 .net 工具使用問題](troubleshoot-usage-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="34b48-155">If you get an error message while following the tutorial, see [Troubleshoot .NET tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="34b48-156">下一步</span><span class="sxs-lookup"><span data-stu-id="34b48-156">Next steps</span></span>

<span data-ttu-id="34b48-157">在本教學課程中，您已建立主控台應用程式，並將它封裝為工具。</span><span class="sxs-lookup"><span data-stu-id="34b48-157">In this tutorial, you created a console application and packaged it as a tool.</span></span> <span data-ttu-id="34b48-158">若要瞭解如何使用此工具做為通用工具，請繼續進行下一個教學課程。</span><span class="sxs-lookup"><span data-stu-id="34b48-158">To learn how to use the tool as a global tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="34b48-159">安裝和使用全域工具</span><span class="sxs-lookup"><span data-stu-id="34b48-159">Install and use a global tool</span></span>](global-tools-how-to-use.md)

<span data-ttu-id="34b48-160">如果您想要的話，可以略過全域工具教學課程，並直接移至本機工具教學課程。</span><span class="sxs-lookup"><span data-stu-id="34b48-160">If you prefer, you can skip the global tools tutorial and go directly to the local tools tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="34b48-161">安裝和使用本機工具</span><span class="sxs-lookup"><span data-stu-id="34b48-161">Install and use a local tool</span></span>](local-tools-how-to-use.md)

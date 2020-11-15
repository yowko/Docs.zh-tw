---
title: 教學課程：建立 .NET 工具
description: 瞭解如何建立 .NET 工具。 工具是使用 .NET CLI 安裝的主控台應用程式。
ms.topic: tutorial
ms.date: 02/12/2020
ms.openlocfilehash: 93d0567f3d73707f828f84fad6128804debf6579
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "94633774"
---
# <a name="tutorial-create-a-net-tool-using-the-net-cli"></a><span data-ttu-id="178bb-104">教學課程：使用 .NET CLI 建立 .NET 工具</span><span class="sxs-lookup"><span data-stu-id="178bb-104">Tutorial: Create a .NET tool using the .NET CLI</span></span>

<span data-ttu-id="178bb-105">本文 **適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="178bb-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="178bb-106">本教學課程會教您如何建立和封裝 .NET 工具。</span><span class="sxs-lookup"><span data-stu-id="178bb-106">This tutorial teaches you how to create and package a .NET tool.</span></span> <span data-ttu-id="178bb-107">.NET CLI 可讓您以工具的形式建立主控台應用程式，讓其他人可以安裝和執行。</span><span class="sxs-lookup"><span data-stu-id="178bb-107">The .NET CLI lets you create a console application as a tool, which others can install and run.</span></span> <span data-ttu-id="178bb-108">.NET 工具是從 .NET CLI 安裝的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="178bb-108">.NET tools are NuGet packages that are installed from the .NET CLI.</span></span> <span data-ttu-id="178bb-109">如需工具的詳細資訊，請參閱 [.net 工具總覽](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="178bb-109">For more information about tools, see [.NET tools overview](global-tools.md).</span></span>

<span data-ttu-id="178bb-110">您將建立的工具是主控台應用程式，它會將訊息做為輸入，並顯示訊息以及建立機器人影像的文字行。</span><span class="sxs-lookup"><span data-stu-id="178bb-110">The tool that you'll create is a console application that takes a message as input and displays the message along with lines of text that create the image of a robot.</span></span>

<span data-ttu-id="178bb-111">這是一系列三個教學課程中的第一個。</span><span class="sxs-lookup"><span data-stu-id="178bb-111">This is the first in a series of three tutorials.</span></span> <span data-ttu-id="178bb-112">在本教學課程中，您會建立並封裝工具。</span><span class="sxs-lookup"><span data-stu-id="178bb-112">In this tutorial, you create and package a tool.</span></span> <span data-ttu-id="178bb-113">在接下來的兩個教學課程中，您將 [使用此工具作為全域工具](global-tools-how-to-use.md) ，並 [使用此工具作為本機工具](local-tools-how-to-use.md)。</span><span class="sxs-lookup"><span data-stu-id="178bb-113">In the next two tutorials you [use the tool as a global tool](global-tools-how-to-use.md) and [use the tool as a local tool](local-tools-how-to-use.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="178bb-114">先決條件</span><span class="sxs-lookup"><span data-stu-id="178bb-114">Prerequisites</span></span>

- <span data-ttu-id="178bb-115">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="178bb-115">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) or a later version.</span></span>

  <span data-ttu-id="178bb-116">本教學課程和下列 [通用工具的教學](global-tools-how-to-use.md) 課程適用于 .NET Core SDK 2.1 和更新版本，因為從該版本開始，可以使用全域工具。</span><span class="sxs-lookup"><span data-stu-id="178bb-116">This tutorial and the following [tutorial for global tools](global-tools-how-to-use.md) apply to .NET Core SDK 2.1 and later versions because global tools are available starting in that version.</span></span> <span data-ttu-id="178bb-117">但本教學課程假設您已安裝3.1 或更新版本，讓您可以選擇繼續進行 [本機工具教學](local-tools-how-to-use.md)課程。</span><span class="sxs-lookup"><span data-stu-id="178bb-117">But this tutorial assumes you have installed 3.1 or later so that you have the option of continuing on to the [local tools tutorial](local-tools-how-to-use.md).</span></span> <span data-ttu-id="178bb-118">從 .NET Core SDK 3.0 開始提供本機工具。</span><span class="sxs-lookup"><span data-stu-id="178bb-118">Local tools are available starting in .NET Core SDK 3.0.</span></span> <span data-ttu-id="178bb-119">無論您使用的是全域工具或本機工具，建立工具的程式都相同。</span><span class="sxs-lookup"><span data-stu-id="178bb-119">The procedures for creating a tool are the same whether you use it as a global tool or as a local tool.</span></span>
  
- <span data-ttu-id="178bb-120">您偏好的文字編輯器或程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="178bb-120">A text editor or code editor of your choice.</span></span>

## <a name="create-a-project"></a><span data-ttu-id="178bb-121">建立專案</span><span class="sxs-lookup"><span data-stu-id="178bb-121">Create a project</span></span>

1. <span data-ttu-id="178bb-122">開啟命令提示字元，並建立名為「存放 *庫* 」的資料夾。</span><span class="sxs-lookup"><span data-stu-id="178bb-122">Open a command prompt and create a folder named *repository*.</span></span>

1. <span data-ttu-id="178bb-123">流覽至存放 *庫* 資料夾，並輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="178bb-123">Navigate to the *repository* folder and enter the following command:</span></span>

   ```dotnetcli
   dotnet new console -n microsoft.botsay
   ```

   <span data-ttu-id="178bb-124">此命令會在存放 *庫* 資料夾下建立名為 *botsay* 的新資料夾。</span><span class="sxs-lookup"><span data-stu-id="178bb-124">The command creates a new folder named *microsoft.botsay* under the *repository* folder.</span></span>

1. <span data-ttu-id="178bb-125">流覽至 *botsay* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="178bb-125">Navigate to the *microsoft.botsay* folder.</span></span>

   ```console
   cd microsoft.botsay
   ```

## <a name="add-the-code"></a><span data-ttu-id="178bb-126">新增程式碼</span><span class="sxs-lookup"><span data-stu-id="178bb-126">Add the code</span></span>

1. <span data-ttu-id="178bb-127">`Program.cs`使用您的程式碼編輯器開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="178bb-127">Open the `Program.cs` file with your code editor.</span></span>

1. <span data-ttu-id="178bb-128">將下列指示詞新增 `using` 至檔案頂端：</span><span class="sxs-lookup"><span data-stu-id="178bb-128">Add the following `using` directive to the top of the file:</span></span>

   ```csharp
   using System.Reflection;
   ```

1. <span data-ttu-id="178bb-129">`Main`以下列程式碼取代方法，以處理應用程式的命令列引數。</span><span class="sxs-lookup"><span data-stu-id="178bb-129">Replace the `Main` method with the following code to process the command-line arguments for the application.</span></span>

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

   <span data-ttu-id="178bb-130">如果未傳遞任何引數，則會顯示簡短的說明訊息。</span><span class="sxs-lookup"><span data-stu-id="178bb-130">If no arguments are passed, a short help message is displayed.</span></span> <span data-ttu-id="178bb-131">否則，所有引數都會串連成單一字串，並藉由呼叫 `ShowBot` 您在下一個步驟中建立的方法來列印。</span><span class="sxs-lookup"><span data-stu-id="178bb-131">Otherwise, all of the arguments are concatenated into a single string and printed by calling the `ShowBot` method that you create in the next step.</span></span>

1. <span data-ttu-id="178bb-132">加入名為的新方法 `ShowBot` ，這個方法接受字串參數。</span><span class="sxs-lookup"><span data-stu-id="178bb-132">Add a new method named `ShowBot` that takes a string parameter.</span></span> <span data-ttu-id="178bb-133">方法會使用文字行來印出訊息和機器人的影像。</span><span class="sxs-lookup"><span data-stu-id="178bb-133">The method prints out the message and an image of a robot using lines of text.</span></span>

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

1. <span data-ttu-id="178bb-134">儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="178bb-134">Save your changes.</span></span>

## <a name="test-the-application"></a><span data-ttu-id="178bb-135">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="178bb-135">Test the application</span></span>

<span data-ttu-id="178bb-136">執行專案，並查看輸出結果。</span><span class="sxs-lookup"><span data-stu-id="178bb-136">Run the project and see the output.</span></span> <span data-ttu-id="178bb-137">請在命令列嘗試這些變化，以查看不同的結果：</span><span class="sxs-lookup"><span data-stu-id="178bb-137">Try these variations at the command line to see different results:</span></span>

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

<span data-ttu-id="178bb-138">`--` 分隔符號之後的所有引數會傳遞至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="178bb-138">All arguments after the `--` delimiter are passed to your application.</span></span>

## <a name="package-the-tool"></a><span data-ttu-id="178bb-139">封裝工具</span><span class="sxs-lookup"><span data-stu-id="178bb-139">Package the tool</span></span>

<span data-ttu-id="178bb-140">您必須先修改專案檔，才能將應用程式封裝並散發為工具。</span><span class="sxs-lookup"><span data-stu-id="178bb-140">Before you can pack and distribute the application as a tool, you need to modify the project file.</span></span>

1. <span data-ttu-id="178bb-141">開啟 *botsay .csproj* 檔案，然後將三個新的 XML 節點新增至節點的結尾 `<PropertyGroup>` ：</span><span class="sxs-lookup"><span data-stu-id="178bb-141">Open the *microsoft.botsay.csproj* file and add three new XML nodes to the end of the `<PropertyGroup>` node:</span></span>

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   <span data-ttu-id="178bb-142">`<ToolCommandName>` 是選擇性專案，指定在安裝工具之後將叫用工具的命令。</span><span class="sxs-lookup"><span data-stu-id="178bb-142">`<ToolCommandName>` is an optional element that specifies the command that will invoke the tool after it's installed.</span></span> <span data-ttu-id="178bb-143">如果未提供此元素，則工具的命令名稱是不含 *.csproj* 副檔名的專案檔名稱。</span><span class="sxs-lookup"><span data-stu-id="178bb-143">If this element isn't provided, the command name for the tool is the project file name without the *.csproj* extension.</span></span>

   <span data-ttu-id="178bb-144">`<PackageOutputPath>` 是選擇性元素，可決定將產生 NuGet 套件的位置。</span><span class="sxs-lookup"><span data-stu-id="178bb-144">`<PackageOutputPath>` is an optional element that determines where the NuGet package will be produced.</span></span> <span data-ttu-id="178bb-145">NuGet 套件是 .NET Core CLI 用來安裝工具的內容。</span><span class="sxs-lookup"><span data-stu-id="178bb-145">The NuGet package is what the .NET Core CLI uses to install your tool.</span></span>

   <span data-ttu-id="178bb-146">專案檔現在看起來如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="178bb-146">The project file now looks like the following example:</span></span>

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

1. <span data-ttu-id="178bb-147">執行 [dotnet pack](dotnet-pack.md) 命令來建立 NuGet 套件：</span><span class="sxs-lookup"><span data-stu-id="178bb-147">Create a NuGet package by running the [dotnet pack](dotnet-pack.md) command:</span></span>

   ```dotnetcli
   dotnet pack
   ```

   <span data-ttu-id="178bb-148">*Nupkg* 檔案會建立在 botsay .csproj 檔案中的值所識別的資料夾中 `<PackageOutputPath>` ，在此範例 *microsoft.botsay.csproj* 中為/nupkg 資料夾（在此範例中為 *./nupkg* 資料夾）。</span><span class="sxs-lookup"><span data-stu-id="178bb-148">The *microsoft.botsay.1.0.0.nupkg* file is created in the folder identified by the `<PackageOutputPath>` value from the *microsoft.botsay.csproj* file, which in this example is the *./nupkg* folder.</span></span>
  
   <span data-ttu-id="178bb-149">當您想要公開發行工具時，可以將它上傳至 `https://www.nuget.org` 。</span><span class="sxs-lookup"><span data-stu-id="178bb-149">When you want to release a tool publicly, you can upload it to `https://www.nuget.org`.</span></span> <span data-ttu-id="178bb-150">當此工具可在 NuGet 上使用時，開發人員可以使用 [dotnet 工具安裝](dotnet-tool-install.md) 命令來安裝此工具。</span><span class="sxs-lookup"><span data-stu-id="178bb-150">Once the tool is available on NuGet, developers can install the tool by using the [dotnet tool install](dotnet-tool-install.md) command.</span></span> <span data-ttu-id="178bb-151">在本教學課程中，您會直接從本機 *nupkg* 資料夾安裝套件，所以不需要將套件上傳至 NuGet。</span><span class="sxs-lookup"><span data-stu-id="178bb-151">For this tutorial you install the package directly from the local *nupkg* folder, so there's no need to upload the package to NuGet.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="178bb-152">疑難排解</span><span class="sxs-lookup"><span data-stu-id="178bb-152">Troubleshoot</span></span>

<span data-ttu-id="178bb-153">如果您在遵循本教學課程時收到錯誤訊息，請參閱 [疑難排解 .net 工具使用問題](troubleshoot-usage-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="178bb-153">If you get an error message while following the tutorial, see [Troubleshoot .NET tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="178bb-154">後續步驟</span><span class="sxs-lookup"><span data-stu-id="178bb-154">Next steps</span></span>

<span data-ttu-id="178bb-155">在本教學課程中，您已建立主控台應用程式，並將它封裝為工具。</span><span class="sxs-lookup"><span data-stu-id="178bb-155">In this tutorial, you created a console application and packaged it as a tool.</span></span> <span data-ttu-id="178bb-156">若要瞭解如何使用此工具做為通用工具，請繼續進行下一個教學課程。</span><span class="sxs-lookup"><span data-stu-id="178bb-156">To learn how to use the tool as a global tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="178bb-157">安裝和使用全域工具</span><span class="sxs-lookup"><span data-stu-id="178bb-157">Install and use a global tool</span></span>](global-tools-how-to-use.md)

<span data-ttu-id="178bb-158">如果您想要的話，可以略過全域工具教學課程，並直接移至本機工具教學課程。</span><span class="sxs-lookup"><span data-stu-id="178bb-158">If you prefer, you can skip the global tools tutorial and go directly to the local tools tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="178bb-159">安裝和使用本機工具</span><span class="sxs-lookup"><span data-stu-id="178bb-159">Install and use a local tool</span></span>](local-tools-how-to-use.md)

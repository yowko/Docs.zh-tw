---
title: 教學課程：建立 .NET 工具
description: 瞭解如何建立 .NET 工具。 工具是使用 .NET CLI 安裝的主控台應用程式。
ms.topic: tutorial
ms.date: 02/12/2020
ms.openlocfilehash: 8f2dd15982aff9fe2d9db9ce2cff8ac1b22e440e
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512628"
---
# <a name="tutorial-create-a-net-tool-using-the-net-cli"></a>教學課程：使用 .NET CLI 建立 .NET 工具

本文 **適用于：** ✔️ .net CORE 2.1 SDK 和更新版本

本教學課程會教您如何建立和封裝 .NET 工具。 .NET CLI 可讓您以工具的形式建立主控台應用程式，讓其他人可以安裝和執行。 .NET 工具是從 .NET CLI 安裝的 NuGet 套件。 如需工具的詳細資訊，請參閱 [.net 工具總覽](global-tools.md)。

您將建立的工具是主控台應用程式，它會將訊息做為輸入，並顯示訊息以及建立機器人影像的文字行。

這是一系列三個教學課程中的第一個。 在本教學課程中，您會建立並封裝工具。 在接下來的兩個教學課程中，您將 [使用此工具作為全域工具](global-tools-how-to-use.md) ，並 [使用此工具作為本機工具](local-tools-how-to-use.md)。 無論您使用的是全域工具或本機工具，建立工具的程式都相同。

## <a name="prerequisites"></a>Prerequisites

- [.NET SDK 5.0](https://dotnet.microsoft.com/download) 或更新版本。

  本教學課程使用 .NET SDK 5.0，但從 .NET Core SDK 2.1 開始提供通用工具。 從 .NET Core SDK 3.0 開始提供本機工具。
  
- 您偏好的文字編輯器或程式碼編輯器。

## <a name="create-a-project"></a>建立專案

1. 開啟命令提示字元，並建立名為「存放 *庫*」的資料夾。

1. 流覽至存放 *庫* 資料夾，並輸入下列命令：

   ```dotnetcli
   dotnet new console -n microsoft.botsay
   ```

   此命令會在存放 *庫* 資料夾下建立名為 *botsay* 的新資料夾。

1. 流覽至 *botsay* 資料夾。

   ```console
   cd microsoft.botsay
   ```

## <a name="add-the-code"></a>新增程式碼

1. `Program.cs`使用您的程式碼編輯器開啟檔案。

1. 將下列指示詞新增 `using` 至檔案頂端：

   ```csharp
   using System.Reflection;
   ```

1. `Main`以下列程式碼取代方法，以處理應用程式的命令列引數。

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

   如果未傳遞任何引數，則會顯示簡短的說明訊息。 否則，所有引數都會串連成單一字串，並藉由呼叫 `ShowBot` 您在下一個步驟中建立的方法來列印。

1. 加入名為的新方法 `ShowBot` ，這個方法接受字串參數。 方法會使用文字行來印出訊息和機器人的影像。

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

1. 儲存您的變更。

## <a name="test-the-application"></a>測試應用程式

執行專案，並查看輸出結果。 請在命令列嘗試這些變化，以查看不同的結果：

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

`--` 分隔符號之後的所有引數會傳遞至您的應用程式。

## <a name="package-the-tool"></a>封裝工具

您必須先修改專案檔，才能將應用程式封裝並散發為工具。

1. 開啟 *botsay .csproj* 檔案，然後將三個新的 XML 節點新增至節點的結尾 `<PropertyGroup>` ：

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   `<ToolCommandName>` 是選擇性專案，指定在安裝工具之後將叫用工具的命令。 如果未提供此元素，則工具的命令名稱是不含 *.csproj* 副檔名的專案檔名稱。

   `<PackageOutputPath>` 是選擇性元素，可決定將產生 NuGet 套件的位置。 NuGet 套件是 .NET CLI 用來安裝工具的功能。

   專案檔現在看起來如下列範例所示：

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

1. 執行 [dotnet pack](dotnet-pack.md) 命令來建立 NuGet 套件：

   ```dotnetcli
   dotnet pack
   ```

   *Nupkg* 檔案會建立在 botsay .csproj 檔案中的值所識別的資料夾中 `<PackageOutputPath>` ，在此範例中為/nupkg 資料夾（在此範例中為資料夾）。
  
   當您想要公開發行工具時，可以將它上傳至 `https://www.nuget.org` 。 當此工具可在 NuGet 上使用時，開發人員可以使用 [dotnet 工具安裝](dotnet-tool-install.md) 命令來安裝此工具。 在本教學課程中，您會直接從本機 *nupkg* 資料夾安裝套件，所以不需要將套件上傳至 NuGet。

## <a name="troubleshoot"></a>疑難排解

如果您在遵循本教學課程時收到錯誤訊息，請參閱 [疑難排解 .net 工具使用問題](troubleshoot-usage-issues.md)。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已建立主控台應用程式，並將它封裝為工具。 若要瞭解如何使用此工具做為通用工具，請繼續進行下一個教學課程。

> [!div class="nextstepaction"]
> [安裝和使用全域工具](global-tools-how-to-use.md)

如果您想要的話，可以略過全域工具教學課程，並直接移至本機工具教學課程。

> [!div class="nextstepaction"]
> [安裝和使用本機工具](local-tools-how-to-use.md)

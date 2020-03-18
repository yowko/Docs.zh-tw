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
# <a name="tutorial-create-a-net-core-tool-using-the-net-core-cli"></a>教程：使用 .NET 核心 CLI 創建 .NET 核心工具

**本文適用于：✔️** .NET 核心 2.1 SDK 和更高版本

本教程將教您如何創建和打包 .NET 核心工具。 .NET Core CLI 允許您創建主控台應用程式作為工具，其他人可以安裝和運行該工具。 .NET 核心工具是從 .NET 核心 CLI 安裝的 NuGet 套裝軟體。 有關工具的詳細資訊，請參閱[.NET 核心工具概述](global-tools.md)。

您將創建的工具是一個主控台應用程式，該應用程式將消息作為輸入，並將消息與創建機器人圖像的文本行一起顯示。

這是三個教程系列中的第一個。 在本教程中，您將創建和打包工具。 在接下來的兩個教程[中，您將該工具用作全域工具](global-tools-how-to-use.md)[，並將該工具用作本地工具](local-tools-how-to-use.md)。

## <a name="prerequisites"></a>必要條件

- [.NET 核心 SDK 3.1](https://dotnet.microsoft.com/download)或更高版本。

  本教程和[以下全域工具教程](global-tools-how-to-use.md)適用于 .NET Core SDK 2.1 和更高版本，因為全域工具可從該版本開始使用。 但本教程假定您已經安裝了 3.1 或更高版本，以便您可以選擇繼續使用[本地工具教程](local-tools-how-to-use.md)。 本地工具可從 .NET 核心 SDK 3.0 中開始。 無論將其用作全域工具還是將工具用作本地工具，創建工具的過程都是相同的。
  
- 您偏好的文字編輯器或程式碼編輯器。

## <a name="create-a-project"></a>建立專案

1. 打開命令提示符並創建名為*存儲庫*的資料夾。

1. 導航到*存儲庫*資料夾並輸入以下命令：

   ```dotnetcli
   dotnet new console -n microsoft.botsay
   ```

   該命令在*存儲庫*資料夾下創建名為*microsoft.botsay*的新資料夾。

1. 導航到*microsoft.botsay*資料夾。

   ```console
   cd microsoft.botsay
   ```

## <a name="add-the-code"></a>新增程式碼

1. 使用代碼`Program.cs`編輯器打開該檔。

1. 將以下`using`指令添加到檔頂部：

   ```csharp
   using System.Reflection;
   ```

1. 將`Main`方法替換為以下代碼，以處理應用程式的命令列參數。

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

   如果未傳遞任何參數，則會顯示一條簡短的説明消息。 否則，所有參數都串聯到單個字串中，並通過調用在下一步中創建`ShowBot`的方法進行列印。

1. 添加名為採用`ShowBot`字串參數的新方法。 該方法使用文本行列印出機器人的消息和圖像。

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

執行專案，並查看輸出結果。 在命令列嘗試這些變體以查看不同的結果：

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

`--` 分隔符號之後的所有引數會傳遞至您的應用程式。

## <a name="package-the-tool"></a>打包工具

在將應用程式打包並分發為工具之前，需要修改專案檔案。

1. 打開*Microsoft.botsay.csproj*檔，並在`<PropertyGroup>`節點的末尾添加新的 XML 節點：

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   `<ToolCommandName>`是一個可選元素，用於指定在安裝工具後調用該工具的命令。 如果未提供此元素，該工具的命令名稱是沒有 *.csproj*副檔名的專案檔案名。

   `<PackageOutputPath>`是確定 NuGet 包的可選元素。 NuGet 包是 .NET 核心 CLI 用於安裝工具的內容。

   專案檔案現在類似于以下示例：

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

1. 通過運行[dotnet 包](dotnet-pack.md)命令創建 NuGet 包：

   ```dotnetcli
   dotnet pack
   ```

   *Microsoft.botsay.1.0.0.nupkg*檔在`<PackageOutputPath>`*Microsoft.botsay.csproj*檔中的值標識的資料夾中創建，在此示例中是 *./nupkg*資料夾。
  
   當您想要公開發布工具時，可以將其上載到`https://www.nuget.org`。 在 NuGet 上提供該工具後，開發人員可以使用[dotnet 工具安裝命令安裝](dotnet-tool-install.md)該工具。 在本教程中，您直接從本地*nupkg*資料夾中安裝包，因此無需將包上載到 NuGet。

## <a name="troubleshoot"></a>疑難排解

如果您在學習本教程時收到錯誤訊息，請參閱[疑難排解 .NET Core 工具使用問題](troubleshoot-usage-issues.md)。

## <a name="next-steps"></a>後續步驟

在本教程中，您創建了一個主控台應用程式，並將其打包為工具。 要瞭解如何將該工具用作全域工具，請先進行下一教程。

> [!div class="nextstepaction"]
> [安裝和使用全域工具](global-tools-how-to-use.md)

如果您願意，可以跳過全域工具教程，然後直接轉到本地工具教程。

> [!div class="nextstepaction"]
> [安裝和使用本機工具](local-tools-how-to-use.md)

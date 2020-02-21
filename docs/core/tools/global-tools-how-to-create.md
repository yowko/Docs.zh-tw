---
title: 教學課程：建立 .NET Core 工具
description: 瞭解如何建立 .NET Core 工具。 工具是使用 .NET Core CLI 安裝的主控台應用程式。
ms.date: 02/12/2020
ms.openlocfilehash: 558bf9e37efc8de68a61f1384fababe342ab7d66
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543400"
---
# <a name="tutorial-create-a-net-core-tool-using-the-net-core-cli"></a>教學課程：使用 .NET Core CLI 建立 .NET Core 工具

**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本

本教學課程會教您如何建立和封裝 .NET Core 工具。 此 .NET Core CLI 可讓您建立主控台應用程式，做為其他人可以安裝和執行的工具。 .NET Core 工具是從 .NET Core CLI 安裝的 NuGet 套件。 如需工具的詳細資訊，請參閱[.Net Core 工具總覽](global-tools.md)。

您將建立的工具是一個主控台應用程式，它會將訊息做為輸入，並顯示訊息以及建立機器人映射的文字行。

這是一系列三個教學課程中的第一個。 在本教學課程中，您會建立和封裝工具。 在接下來的兩個教學課程中，您[將使用此工具做為全域工具](global-tools-how-to-use.md)，並[使用此工具做為本機工具](local-tools-how-to-use.md)。

## <a name="prerequisites"></a>Prerequisites

- [.NET Core SDK 3.1](https://dotnet.microsoft.com/download)或更新版本。

  本教學課程和[通用工具](global-tools-how-to-use.md)的下列教學課程適用于 .NET Core SDK 2.1 和更新版本，因為從該版本開始會提供通用工具。 但本教學課程假設您已安裝3.1 或更新版本，讓您可以選擇繼續進行[本機工具教學](local-tools-how-to-use.md)課程。 從 .NET Core SDK 3.0 開始提供本機工具。 無論您使用它做為全域工具或本機工具，建立工具的程式都是一樣的。
  
- 您偏好的文字編輯器或程式碼編輯器。

## <a name="create-a-project"></a>建立專案

1. 開啟命令提示字元，並建立名為*repository*的資料夾。

1. 流覽至存放*庫*資料夾，並輸入下列命令，將 `<name>` 取代為唯一值，讓專案名稱成為唯一的。 

   ```dotnetcli
   dotnet new console -n botsay-<name>
   ```

   例如，您可以執行下列命令：

   ```dotnetcli
   dotnet new console -n botsay-nancydavolio
   ```

   命令會在存放*庫*資料夾底下建立名為*botsay\<名稱 >* 的新資料夾。

1. 流覽至*botsay-\<名稱 >*  資料夾。

   ```console
   cd botsay-<name>
   ```

## <a name="add-the-code"></a>新增程式碼

1. 使用您的程式碼編輯器開啟 `Program.cs` 檔案。

1. 將下列 `using` 指示詞新增至檔案頂端：

   ```csharp
   using System.Reflection;
   ```

1. 以下列程式碼取代 `Main` 方法，以處理應用程式的命令列引數。

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

   如果未傳遞任何引數，則會顯示簡短的說明訊息。 否則，所有引數都會串連成單一字串，並藉由呼叫您在下一個步驟中建立的 `ShowBot` 方法來列印。

1. 新增名為 `ShowBot` 的新方法，以接受字串參數。 方法會使用文字行來印出訊息和機器人的影像。

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

在您可以將應用程式封裝並散發為工具之前，您需要修改專案檔案。 

1. 開啟*botsay\<名稱 > .csproj*檔案，然後將三個新的 XML 節點加入至 `<PropertyGroup>` 節點的結尾：

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   `<ToolCommandName>` 是選擇性的專案，它會指定在安裝工具之後叫用它的命令。 如果未提供此元素，則工具的命令名稱是不含 *.csproj*副檔名的專案檔案名稱。

   `<PackageOutputPath>` 是選擇性元素，可決定將產生 NuGet 封裝的位置。 NuGet 套件是 .NET Core CLI 用來安裝工具的功能。

   專案檔現在看起來如下列範例所示：

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

1. 執行[dotnet pack](dotnet-pack.md)命令來建立 NuGet 套件：

   ```dotnetcli
   dotnet pack
   ```

   從*botsay\<名稱 > .csproj*檔案中的 `<PackageOutputPath>` 值所識別的資料夾中建立的*botsay\<名稱 > nupkg*檔案，在此範例中是 */nupkg*資料夾。
  
   當您想要公開發行工具時，可以將它上傳至 `https://www.nuget.org`。 當此工具可在 NuGet 上使用之後，開發人員就可以使用[dotnet tool install](dotnet-tool-install.md)命令來安裝此工具。 在本教學課程中，您會直接從本機*nupkg*資料夾安裝套件，因此不需要將套件上傳至 NuGet。

## <a name="troubleshoot"></a>疑難排解

如果您在教學課程之後收到錯誤訊息，請參閱針對[.Net Core 工具使用問題進行疑難排解](troubleshoot-usage-issues.md)。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已建立主控台應用程式，並將它封裝為工具。 若要瞭解如何以全域工具的形式使用此工具，請前進到下一個教學課程。

> [!div class="nextstepaction"]
> [安裝和使用通用工具](global-tools-how-to-use.md)

如果您想要的話，可以略過全域工具教學課程，直接移至本機工具教學課程。

> [!div class="nextstepaction"]
> [安裝和使用本機工具](local-tools-how-to-use.md)

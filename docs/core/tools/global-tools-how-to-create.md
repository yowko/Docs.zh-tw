---
title: 如何建立 .NET Core 通用工具
description: 描述如何建立通用工具。 通用工具是透過 .NET Core CLI 安裝的主控台應用程式。
author: Thraka
ms.author: adegeo
ms.date: 08/22/2018
ms.openlocfilehash: 3860aad5e2c13714298d50bb9ac10daec3aadf01
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2018
ms.locfileid: "47231205"
---
# <a name="create-a-net-core-global-tool-using-the-net-core-cli"></a>使用 .NET Core CLI 建立 .NET Core 通用工具

本文會教導您如何建立及封裝 .NET Core 通用工具。 .NET Core CLI 可讓您建立作為通用工具的主控台應用程式，其他人也可以輕鬆地安裝及執行該工具。 .NET Core 通用工具是從 .NET Core CLI 安裝的 NuGet 套件。 如需通用工具的詳細資訊，請參閱 [.NET Core 通用工具概觀][global-tool-info]。

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="create-a-project"></a>建立專案

本文使用 .NET Core CLI 來建立和管理專案。

我們的範例工具是會產生 ASCII Bot 並列印訊息的主控台應用程式。 首先，建立新的 .NET Core 主控台應用程式。

```console
dotnet new console -o botsay
```

瀏覽至先前命令所建立的 `botsay` 目錄。

## <a name="add-the-code"></a>新增程式碼

使用您慣用的文字編輯器 (例如 `vim` 或[Visual Studio Code](https://code.visualstudio.com/))，開啟 `Program.cs` 檔案。

將下列 `using` 指示詞新增至檔案頂端，這有助於縮短用來顯示應用程式版本資訊的程式碼。

```csharp
using System.Reflection;
```

接下來，向下移動至 `Main` 方法。 使用下列程式碼來取代方法，以處理應用程式的命令列引數。 如果未傳遞任何引數，則會顯示簡短的說明訊息。 否則，所有引數都會轉換成字串並且以 Bot 列印。

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

### <a name="create-the-bot"></a>建立 Bot

接下來，新增名為 `ShowBot` 的新方法來採用字串參數。 這個方法會列印出訊息和 ASCII Bot。 ASCII Bot 程式碼取自 [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) 範例。

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

### <a name="test-the-tool"></a>測試工具

執行專案，並查看輸出結果。 請嘗試這些命令列變化，以查看不同的結果：

```csharp
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- hello from the bot
```

`--` 分隔符號之後的所有引數會傳遞至您的應用程式。

## <a name="setup-the-global-tool"></a>安裝通用工具

在您可以將應用程式封裝及散佈為通用工具之前，您應該修改專案檔案。 開啟 `botsay.csproj` 檔案，然後將三個新 XML 節點新增至 `<Project><PropertyGroup>` 節點：

- `<PackAsTool>`  
[必要] 表示會封裝應用程式以安裝為通用工具。

- `<ToolCommandName>`  
[選用] 工具的替代名稱，否則工具的命令名稱會跟隨著專案檔案命名。 您在套件中可以有多個工具，選擇唯一且易記的名稱，有助於與相同套件中的其他工具區分。

- `<PackageOutputPath>`  
[選用] 在其中產生 NuGet 套件的位置。 NuGet 套件是 .NET Core CLI 通用工具用來安裝工具的套件。

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

即使 `<PackageOutputPath>` 是選擇性的，請在此範例中使用它。 請確定您已設定：`<PackageOutputPath>./nupkg</PackageOutputPath>`。

接下來，為您的應用程式建立 NuGet 套件。

```console
dotnet pack
```

`botsay.1.0.0.nupkg` 檔案是在資料夾 (由 `botsay.csproj` 檔案中的 `<PackageOutputPath>` XML 值識別) 中建立的，在此範例中是 `./nupkg` 資料夾。 這可讓您輕鬆地安裝和測試。 當您想要公開發行工具時，請將它上傳至 [https://www.nuget.org](https://www.nuget.org)。

既然您已經有了套件，請從該套件安裝工具： 

```console
dotnet tool install --global --add-source ./nupkg botsay
```

`--add-source` 參數會告訴 .NET Core CLI 暫時使用 `./nupkg` 資料夾 (我們的 `<PackageOutputPath>` 資料夾) 作為 NuGet 套件的額外來源摘要。 如需安裝通用工具的詳細資訊，請參閱 [.NET Core 通用工具概觀][global-tool-info]。

如果安裝成功，則會顯示一則訊息，其中顯示用來呼叫此工具的命令以及安裝的版本，類似於下例範例：

```
You can invoke the tool using the following command: botsay
Tool 'botsay' (version '1.0.0') was successfully installed.
```

您現在應該可以輸入 `botsay` 並且取得工具的回應。

> [!NOTE]
> 如果安裝成功，但是您無法使用 `botsay` 命令，您需要開啟新的終端機以重新整理路徑。

## <a name="remove-the-tool"></a>移除工具

一旦您完成工具的實驗，可以使用下列命令來將它移除：

```console
dotnet tool uninstall -g botsay
```

[global-tool-info]: global-tools.md

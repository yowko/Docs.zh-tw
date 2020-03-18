---
title: 使用 CLI 開始使用 .NET Core
description: 一個分步教程，演示如何使用 .NET Core CLI 在 Windows、Linux 或 macOS 上開始使用 .NET Core。
author: thraka
ms.author: adegeo
ms.date: 12/05/2019
ms.technology: dotnet-cli
ms.custom: updateeachrelease
ms.openlocfilehash: fe69521a6ac88055e3e8c8502a7e19a72667dbef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240853"
---
# <a name="get-started-with-net-core-using-the-net-core-cli"></a>使用 .NET 核心 CLI 開始使用 .NET 核心

本文將介紹如何使用 .NET Core CLI 開始開發在 Windows、Linux 和 macOS 上工作的 .NET 核心應用。

如果您不熟悉 .NET 核心 CLI，請參閱[.NET 核心 CLI 概述](../tools/index.md)。

## <a name="prerequisites"></a>必要條件

- [.NET 核心 SDK 3.1](https://dotnet.microsoft.com/download)或更高版本。
- 您偏好的文字編輯器或程式碼編輯器。

## <a name="hello-console-app"></a>嗨，主控台應用程式！

您可以從 dotnet/samples GitHub 存放庫[檢視或下載範例程式碼](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild)。 如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。

開啟命令提示字元，並建立名為 *Hello* 的資料夾。 導航到您創建的資料夾並鍵入以下內容。

```dotnetcli
dotnet new console
dotnet run
```

讓我們快速逐步解說︰

01. `dotnet new console`

    [dotnet new](../tools/dotnet-new.md)創建最新的*Hello.csproj*專案檔案，該檔具有構建主控台應用所需的依賴項。 它還創建一個*Program.cs，* 一個基本檔，包含應用程式的進入點。

    *你好.csproj*：

    [!code-xml[Hello.csproj](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Hello.csproj)]

    專案檔會指定還原相依性和建置程式所需的所有內容。

    - 該`<OutputType>`元素指定我們正在構建一個可執行檔，換句話說是主控台應用程式。
    - 該`<TargetFramework>`元素指定我們針對的 .NET 實現。 在進階案例中，您可以指定多個目標架構，並在單一作業中建置這全部的架構。 在本教程中，我們將堅持僅為 .NET Core 3.1 構建。

    *Program.cs*：

    [!code-csharp[Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Program.cs)]

    程式是透過 `using System` 來啟動，這表示「將 `System` 命名空間中的所有內容帶入這個檔案的範圍內」。 命名`System`空間包括類`Console`。

    然後，我們會定義稱為 `Hello` 的命名空間。 您可以將其變更為任何所需的位置。 命名的`Program`類在命名空間中定義，`Main`該方法採用名為 的`args`字串陣列。 此陣列包含運行程式時傳入的參數清單。 因為它是，這個陣列不使用，程式只是寫文本"你好世界！ 到主控台。 稍後，我們將變更程式碼以便使用此引數。

    `dotnet new`調用[點網](../tools/dotnet-restore.md)隱式還原。 `dotnet restore` 呼叫 [NuGet](https://www.nuget.org/) (.NET 套件管理員)，以還原相依性的樹狀結構。 NuGet 會分析 Hello.csproj** 檔案、下載檔案中所述的相依性 (或從您電腦上的快取抓取)，並寫入 obj/project.assets.json** 檔案，該檔案是編譯及執行範例的必要項目。

02. `dotnet run`

    [dotnet 運行](../tools/dotnet-run.md)調用[dotnet 生成](../tools/dotnet-build.md)以確保生成目標已生成，然後調用`dotnet <assembly.dll>`以運行目標應用程式。

    ```dotnetcli
    dotnet run
    ```

    您將獲得以下輸出。

    ```console
    Hello World!
    ```

    或者，您也可以運行`dotnet build`以編譯代碼，而無需運行生成主控台應用程式。 這將導致基於專案名稱的編譯應用程式（作為 DLL 檔）。 在這種情況下，創建的檔案名為*Hello.dll*。 此應用可以在 Windows`dotnet bin\Debug\netcoreapp3.1\Hello.dll`上運行（用於`/`非 Windows 系統）。

    ```dotnetcli
    dotnet bin\Debug\netcoreapp3.1\Hello.dll
    ```

    您將獲得以下輸出。

    ```console
    Hello World!
    ```

    編譯應用時，將和 創建`Hello.dll`特定于作業系統的可執行檔。 在 Windows 上，`Hello.exe`這將是 ;在Linux或macOS上，這將是`hello`。 使用上面的示例，檔案名為`Hello.exe`或`Hello`。 您可以直接運行該可執行檔。

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a>修改程式

讓我們稍微變更程式。 斐波那契數位很有趣，所以讓我們添加，也使用參數來問候運行應用程式的人。

01. 以下列程式碼取代 *Program.cs* 檔案的內容：

    [!code-csharp[Fibonacci](~/samples/snippets/core/tutorials/cli-create-console-app/fibonacci-msbuild/csharp/Program.cs)]

02. 運行[點網生成](../tools/dotnet-build.md)以編譯更改。

03. 運行將參數傳遞給應用的程式。 使用 命令`dotnet`運行應用時，將添加到`--`末尾。 右側的任何內容`--`都將作為參數傳遞給應用。 在下面的示例中，該值`John`將傳遞給應用。

    ```dotnetcli
    dotnet run -- John
    ```

    您將獲得以下輸出。

    ```console
    Hello John!
    Fibonacci Numbers 1-15:
    1: 0
    2: 1
    3: 1
    4: 2
    5: 3
    6: 5
    7: 8
    8: 13
    9: 21
    10: 34
    11: 55
    12: 89
    13: 144
    14: 233
    15: 377
    ```

就這麼簡單！ 您可以修改*Program.cs*任何你喜歡的方式。

## <a name="working-with-multiple-files"></a>使用多個檔案

單個檔對於簡單的一次性程式是可以的，但如果您要構建一個更複雜的應用程式，則專案上可能會有多個代碼檔。 請藉由快取某些 Fibonacci 值，再新增一些遞迴功能，從先前的 Fibonacci 範例開始建置。

01. 使用下列程式碼在 *Hello* 目錄中新增名為 *FibonacciGenerator.cs* 的檔案：

    [!code-csharp[Fibonacci Generator](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/FibonacciGenerator.cs)]

02. 變更 *Program.cs* 檔案中的 `Main` 方法，以具現化新的類別並呼叫其方法，如下列範例所示：

    [!code-csharp[New Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/Program.cs)]

03. 運行[點網生成](../tools/dotnet-build.md)以編譯更改。

04. 通過執行[點網運行](../tools/dotnet-run.md)來運行你的應用。

    ```dotnetcli
    dotnet run
    ```

    您將獲得以下輸出。

    ```console
    0
    1
    1
    2
    3
    5
    8
    13
    21
    34
    55
    89
    144
    233
    377
    ```

## <a name="publish-your-app"></a>發佈您的應用程式

準備好分發應用後，請使用[dotnet 發佈](../tools/dotnet-publish.md)命令在_bin\\調試\\netcoreapp3.1\\發佈\\_（用於`/`非 Windows 系統）生成_發佈_資料夾。 您可以將 _publish_  資料夾的內容散發到其他平台，只要那些平台已安裝 dotnet 執行階段。

```dotnetcli
dotnet publish
```

您將獲得類似于以下內容的輸出。

```console
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

上述輸出可能因當前資料夾和作業系統而異，但輸出應類似。

您可以使用 [dotnet](../tools/dotnet.md) 命令來執行已發佈的應用程式：

```dotnetcli
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll
```

您將獲得以下輸出。

```console
Hello World!
```

如本文開頭所述，與`Hello.dll`創建作業系統特定的可執行檔一起創建。 在 Windows 上，`Hello.exe`這將是 ;在Linux或macOS上，這將是`hello`。 使用上面的示例，檔案名為`Hello.exe`或`Hello`。 您可以直接運行此已發佈的可執行檔。

```console
.\bin\Debug\netcoreapp3.1\publish\Hello.exe

Hello World!
```

## <a name="conclusion"></a>結論

就這麼簡單！ 現在，您可以開始使用這裡學到的基本概念，建立您自己的程式。

## <a name="see-also"></a>另請參閱

- [使用 .NET 核心 CLI 組織和測試專案](testing-with-cli.md)
- [使用 .NET 核心 CLI 發佈 .NET 核心應用](../deploying/deploy-with-cli.md)
- [.NET 核心應用程式部署](../deploying/index.md)

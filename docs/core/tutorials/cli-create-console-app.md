---
title: 使用 CLI 開始使用 .NET Core
description: 逐步教學課程示範如何使用 .NET Core CLI 在 Windows、Linux 或 macOS 上開始使用 .NET Core。
author: thraka
ms.author: adegeo
ms.date: 12/05/2019
ms.technology: dotnet-cli
ms.custom: updateeachrelease
ms.openlocfilehash: 6e1c7881aa415ea54307d80214001a2f0fe5b4a6
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920471"
---
# <a name="get-started-with-net-core-using-the-net-core-cli"></a>使用 .NET Core CLI 開始使用 .NET Core

本文將說明如何開始開發使用 .NET Core CLI 在 Windows、Linux 和 macOS 上工作的 .NET Core 應用程式。

如果您不熟悉 .NET Core CLI，請參閱[.NET Core CLI 總覽](../tools/index.md)。

## <a name="prerequisites"></a>必要條件：

- [.NET Core SDK 3.1](https://dotnet.microsoft.com/download)或更新版本。
- 您選擇的文字編輯器或程式碼編輯器。

## <a name="hello-console-app"></a>嗨，主控台應用程式！

您可以從 dotnet/samples GitHub 存放庫[檢視或下載範例程式碼](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild)。 如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。

開啟命令提示字元，並建立名為 *Hello* 的資料夾。 巡覽至您已建立的資料夾，並鍵入下列內容：

```dotnetcli
dotnet new console
dotnet run
```

讓我們快速逐步解說︰

01. `dotnet new console`

    [dotnet new](../tools/dotnet-new.md)會以建立主控台應用程式所需的相依性，建立最新的*Hello .csproj*專案檔案。 它也會建立一個*Program.cs*，這是一個基本檔案，其中包含應用程式的進入點。
    
    您*好，.csproj*：
    
    [!code-xml[Hello.csproj](~/samples/core/console-apps/HelloMsBuild/Hello.csproj)]
    
    專案檔會指定還原相依性和建置程式所需的所有內容。
    
    - `<OutputType>` 元素指定我們要建立可執行檔，也就是主控台應用程式。
    - `<TargetFramework>` 元素會指定我們的目標 .NET 實作為目標。 在進階案例中，您可以指定多個目標架構，並在單一作業中建置這全部的架構。 在本教學課程中，我們將只針對 .NET Core 3.1 進行建立。
    
    *Program.cs*：
    
    [!code-csharp[Program.cs](~/samples/core/console-apps/HelloMsBuild/Program.cs)]
    
    程式是透過 `using System` 來啟動，這表示「將 `System` 命名空間中的所有內容帶入這個檔案的範圍內」。 `System` 命名空間包含 `Console` 類別。
    
    然後，我們會定義稱為 `Hello` 的命名空間。 您可以將其變更為任何所需的位置。 名為 `Program` 的類別是在該命名空間內定義，而 `Main` 方法會接受名為 `args`的字串陣列。 此陣列包含執行程式時傳入的引數清單。 就像這樣，此陣列不會使用，而且程式只會寫入文字 "Hello World！" 到主控台。 稍後，我們將變更程式碼以便使用此引數。
    
    `dotnet new` 會以隱含方式呼叫[dotnet restore](../tools/dotnet-restore.md) 。 `dotnet restore` 呼叫 [NuGet](https://www.nuget.org/) (.NET 套件管理員)，以還原相依性的樹狀結構。 NuGet 會分析 Hello.csproj 檔案、下載檔案中所述的相依性 (或從您電腦上的快取抓取)，並寫入 obj/project.assets.json 檔案，該檔案是編譯及執行範例的必要項目。

02. `dotnet run`

    [dotnet run](../tools/dotnet-run.md)會呼叫[dotnet 組建](../tools/dotnet-build.md)，以確保組建目標已建立，然後呼叫 `dotnet <assembly.dll>` 以執行目標應用程式。
    
    ```console
    dotnet run

    Hello World!
    ```
    
    或者，您也可以執行 `dotnet build` 來編譯器代碼，而不需執行組建主控台應用程式。 這會根據專案的名稱，以 DLL 檔案的形式產生已編譯的應用程式。 在此情況下，所建立的檔案會命名為*Hello .dll*。 此應用程式可以在 Windows 上使用 `dotnet bin\Debug\netcoreapp3.1\Hello.dll` 執行（使用非 Windows 系統的 `/`）。
    
    ```console
    dotnet bin\Debug\netcoreapp3.1\Hello.dll

    Hello World!
    ```
    
    當編譯應用程式時，會與 `Hello.dll`一併建立作業系統特定的可執行檔。 在 Windows 上，這會是 `Hello.exe`;在 Linux 或 macOS 上，這會是 `hello`。 在上述範例中，檔案會以 `Hello.exe` 或 `Hello`命名。 您可以直接執行該可執行檔。

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a>修改程式

讓我們稍微變更程式。 斐波里的數位很有趣，因此讓我們新增它，並使用引數來歡迎執行應用程式的人員。

01. 以下列程式碼取代 *Program.cs* 檔案的內容：

    [!code-csharp[Fibonacci](~/samples/core/console-apps/fibonacci-msbuild/Program.cs)]

02. 執行[dotnet build](../tools/dotnet-build.md)以編譯變更。

03. 執行程式，將參數傳遞至應用程式。 當您使用 `dotnet` 命令來執行應用程式時，請將 `--` 新增至結尾。 `--` 右邊的任何專案都會當做參數傳遞至應用程式。 在下列範例中，`John` 的值會傳遞至應用程式。

    ```console
    $ dotnet run -- John
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

就是這麼容易！ 您可以用您喜歡的任何方式修改*Program.cs* 。

## <a name="working-with-multiple-files"></a>使用多個檔案

單一檔案適用于簡單的一次性程式，但如果您要建立更複雜的應用程式，您的專案可能會有多個程式碼檔案。 請藉由快取某些 Fibonacci 值，再新增一些遞迴功能，從先前的 Fibonacci 範例開始建置。

01. 使用下列程式碼在 *Hello* 目錄中新增名為 *FibonacciGenerator.cs* 的檔案：

    [!code-csharp[Fibonacci Generator](~/samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

02. 變更 *Program.cs* 檔案中的 `Main` 方法，以具現化新的類別並呼叫其方法，如下列範例所示：

    [!code-csharp[New Program.cs](~/samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

03. 執行[dotnet build](../tools/dotnet-build.md)以編譯變更。

04. 執行[dotnet run](../tools/dotnet-run.md)來執行您的應用程式。 以下顯示程式輸出：

    ```console
    $ dotnet run
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

## <a name="publish-your-app"></a>發行您的應用程式

準備好散發應用程式之後，請使用[dotnet publish](../tools/dotnet-publish.md)命令來產生_bin\\debug\\netcoreapp 3.1_的_publish_資料夾，\\發佈\\（針對非 Windows 系統使用 `/`）。 您可以將 _publish_  資料夾的內容散發到其他平台，只要那些平台已安裝 dotnet 執行階段。

```console
dotnet publish
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

上述輸出可能會根據您目前的資料夾和作業系統而有所不同，但輸出應該類似。

您可以使用 [dotnet](../tools/dotnet.md) 命令來執行已發佈的應用程式：

```console
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll

Hello World!
```

如同本文開頭所述，作業系統特定的可執行檔是與 `Hello.dll`一併建立的。 在 Windows 上，這會是 `Hello.exe`;在 Linux 或 macOS 上，這會是 `hello`。 在上述範例中，檔案會以 `Hello.exe` 或 `Hello`命名。 您可以直接執行這個已發行的可執行檔。

```console
.\bin\Debug\netcoreapp3.1\publish\Hello.exe

Hello World!
```

## <a name="conclusion"></a>結論

就是這麼容易！ 現在，您可以開始使用這裡學到的基本概念，建立您自己的程式。

## <a name="see-also"></a>請參閱

- [使用 .NET Core CLI 組織和測試專案](testing-with-cli.md)
- [使用 .NET Core CLI 發佈 .NET Core 應用程式](../deploying/deploy-with-cli.md)
- [.NET Core 應用程式部署](../deploying/index.md)

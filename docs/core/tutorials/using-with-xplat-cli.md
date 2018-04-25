---
title: 從使用 CLI 開始使用 .NET Core
description: 本逐步教學課程說明如何使用 .NET Core 命令列介面 (CLI) 在 Windows、Linux 或 macOS 上開始使用 .NET Core。
keywords: .NET Core, CLI
author: cartermp
ms.author: mairaw
ms.date: 03/08/2017
ms.topic: get-started-article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 41632e63-d5c6-4427-a09e-51dc1116d45f
ms.workload:
- dotnetcore
ms.openlocfilehash: c5082806c907a6c6d4f51bf77e54deee08de3d8b
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="getting-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a>使用命令列在 Windows/Linux/macOS 上開始使用 .NET Core

本主題將示範如何使用 .NET Core CLI 工具在電腦上開始開發跨平台應用程式。

如果您不熟悉 .NET Core CLI 工具組，請參閱 [.NET Core SDK 概觀](../tools/index.md)。

## <a name="prerequisites"></a>必要條件

- [.NET Core SDK 1.0](https://www.microsoft.com/net/download/core)。
- 您選擇的文字編輯器或程式碼編輯器。

## <a name="hello-console-app"></a>嗨，主控台應用程式！

您可以從 dotnet/samples GitHub 存放庫[檢視或下載範例程式碼](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild)。 如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。

開啟命令提示字元，並建立名為 *Hello* 的資料夾。 巡覽至您已建立的資料夾，並鍵入下列內容：

```
$ dotnet new console
$ dotnet restore
$ dotnet run
```

讓我們快速逐步解說︰

1. `$ dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md) 使用建置主控台應用程式時所需的相依性，來建立最新的 `Hello.csproj` 專案檔。  它也會建立 `Program.cs`，這個基本檔案包含了應用程式的進入點。
   
   `Hello.csproj`：

   [!code[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]   

   專案檔會指定還原相依性和建置程式所需的所有內容。

   * `OutputType` 標記會指定我們正在建置可執行檔，亦即主控台應用程式。
   * `TargetFramework` 標記會指定做為目標的 .NET 實作。 在進階案例中，您可以指定多個目標架構，並在單一作業中建置這全部的架構。 在本教學課程中，我們將著重於僅針對 .NET Core 1.0 來建置。

   `Program.cs`：

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]   

   程式是透過 `using System` 來啟動，這表示「將 `System` 命名空間中的所有內容帶入這個檔案的範圍內」。 `System` 命名空間會包含像是 `string` 的基本結構或數字類型。

   然後，我們會定義稱為 `Hello` 的命名空間。 您可以將其變更為任何所需的位置。 名為 `Program` 的類別是定義於該命名空間內，其中含有可接受字串陣列作為其引數的 `Main` 方法。 這個陣列包含呼叫已編譯的程式時傳入的引數清單。 事實上，並未使用這個陣列︰所有程式所做的只是將 "Hello World!" 寫入 到主控台。 稍後，我們將變更程式碼以便使用此引數。

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

2. `$ dotnet restore`

   [`dotnet restore`](../tools/dotnet-restore.md) 呼叫 [NuGet](https://www.nuget.org/) (.NET 套件管理員)，以還原相依性的樹狀結構。 NuGet 會分析 *Hello.csproj* 檔案、下載檔案中所述的相依性 (或從您電腦上的快取抓取)，並寫入 *obj/project.assets.json* 檔案。  必須要有 *project.assets.json* 檔案才能夠編譯並執行。
   
   *project.assets.json* 檔案是一組持續性且完整的 NuGet 相依性圖形，也包含了描述應用程式的其他資訊。  其他工具，例如 [`dotnet build`](../tools/dotnet-build.md) 和 [`dotnet run`](../tools/dotnet-run.md)，會讀取這個檔案，以便它們能用正確的 NuGet 相依性集合與繫結解析，處理原始程式碼。
   
3. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) 呼叫 [`dotnet build`](../tools/dotnet-build.md) 以確保建置目標已經建置好，然後呼叫 `dotnet <assembly.dll>` 執行目標應用程式。
   
    ```
    $ dotnet run
    Hello World!
    ```

    或者，您也可以執行 [`dotnet build`](../tools/dotnet-build.md) 來編譯程式碼，而不執行建置主控台應用程式。 這會產生編譯成 DLL 檔案的應用程式，您可以在 Windows 上使用 `dotnet bin\Debug\netcoreapp1.0\Hello.dll` (在非 Windows 系統上則使用 `/`) 來執行此應用程式。 您也可以指定應用程式的引數，您將於稍後看到該主題。

    ```
    $ dotnet bin\Debug\netcoreapp1.0\Hello.dll
    Hello World!
    ```

    在進階案例中，可以建置應用程式做為一組獨立的平台專屬檔案，您可以將其部署到不需安裝 .NET Core 的電腦上並加以執行。 如需詳細資訊，請參閱 [.NET Core 應用程式部署](../deploying/index.md)。

### <a name="augmenting-the-program"></a>擴充程式

讓我們稍微變更程式。 Fibonacci 數字很有趣，因此讓我們也新增該數字，以使用引數來歡迎執行應用程式的人員。

1. 以下列程式碼取代 *Program.cs* 檔案的內容：

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]   

2. 執行 [`dotnet build`](../tools/dotnet-build.md) 以編譯變更。

3. 執行將參數傳遞至應用程式的程式：

   ```
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

就是這麼容易！  您可以隨意擴充 `Program.cs`。

## <a name="working-with-multiple-files"></a>使用多個檔案

單一檔案很適合用於簡單的一次性程式，但如果您要建置更複雜的應用程式，您可能會在專案中使用多個原始程式檔。讓我們從上一個 Fibonacci 範例中快取一些 Fibonacci 值並新增一些遞迴功能，來建置此應用程式。 

1. 使用下列程式碼在 *Hello* 目錄中新增名為 *FibonacciGenerator.cs* 的檔案：

   [!code-csharp[Fibonacci Generator](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]   

2. 變更 *Program.cs* 檔案中的 `Main` 方法，以具現化新的類別並呼叫其方法，如下列範例所示：

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. 執行 [`dotnet build`](../tools/dotnet-build.md) 以編譯變更。

4. 藉由執行 [`dotnet run`](../tools/dotnet-run.md) 來執行您的應用程式。 以下顯示程式輸出：

   ```
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

就是這麼容易！ 現在，您可以開始使用這裡學到的基本概念，建立您自己的程式。

請注意，本教學課程中所示用於執行應用程式的命令和步驟，僅供開發階段期間使用。 準備好部署應用程式之後，您將需要檢視不同的 .NET Core 應用程式[部署策略](../deploying/index.md)及 [`dotnet publish`](../tools/dotnet-publish.md) 命令。

## <a name="see-also"></a>另請參閱

[使用 .NET Core CLI 工具組織和測試專案](testing-with-cli.md)

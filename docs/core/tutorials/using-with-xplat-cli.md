---
title: 使用 CLI 開始使用 .NET Core
description: 本逐步教學課程說明如何使用 .NET Core 命令列介面 (CLI) 在 Windows、Linux 或 macOS 上開始使用 .NET Core。
author: thraka
ms.author: adegeo
ms.date: 08/07/2019
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: b5ef70967c8404dc5ce5b816bb9a1c3b1d7e4230
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117354"
---
# <a name="get-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a>使用命令列開始在 Windows/Linux/macOS 上使用 .NET Core

本主題將示範如何使用 .NET Core CLI 工具在電腦上開始開發跨平台應用程式。

如果您不熟悉 .NET Core CLI 工具組，請參閱 [.NET Core SDK 概觀](../tools/index.md)。

## <a name="prerequisites"></a>必要條件

- [.NET Core SDK 2.1](https://dotnet.microsoft.com/download)或更新版本。
- 您選擇的文字編輯器或程式碼編輯器。

## <a name="hello-console-app"></a>嗨，主控台應用程式！

您可以從 dotnet/samples GitHub 存放庫[檢視或下載範例程式碼](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild)。 如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。

開啟命令提示字元，並建立名為 *Hello* 的資料夾。 巡覽至您已建立的資料夾，並鍵入下列內容：

```dotnetcli
dotnet new console
dotnet run
```

讓我們快速逐步解說︰

1. `dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md) 使用建置主控台應用程式時所需的相依性，來建立最新的 `Hello.csproj` 專案檔。  它也會建立 `Program.cs`，這個基本檔案包含了應用程式的進入點。

   `Hello.csproj`：

   [!code[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]

   專案檔會指定還原相依性和建置程式所需的所有內容。

   - `OutputType` 標記會指定我們正在建置可執行檔，亦即主控台應用程式。
   - `TargetFramework` 標記會指定做為目標的 .NET 實作。 在進階案例中，您可以指定多個目標架構，並在單一作業中建置這全部的架構。 在本教學課程中，我們將著重於僅針對 .NET Core 2.1 來建置。

   `Program.cs`：

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]

   程式是透過 `using System` 來啟動，這表示「將 `System` 命名空間中的所有內容帶入這個檔案的範圍內」。 `System` 命名空間會包含像是 `string` 的基本結構或數字類型。

   然後，我們會定義稱為 `Hello` 的命名空間。 您可以將其變更為任何所需的位置。 名為 `Program` 的類別是定義於該命名空間內，其中含有可接受字串陣列作為其引數的 `Main` 方法。 這個陣列包含呼叫已編譯的程式時傳入的引數清單。 事實上，並未使用這個陣列︰所有程式所做的只是將 "Hello World!" 寫入 到主控台。 稍後，我們將變更程式碼以便使用此引數。

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

   `dotnet new` 會隱含地呼叫 [`dotnet restore`](../tools/dotnet-restore.md)。 `dotnet restore` 呼叫 [NuGet](https://www.nuget.org/) (.NET 套件管理員)，以還原相依性的樹狀結構。 NuGet 會分析 Hello.csproj 檔案、下載檔案中所述的相依性 (或從您電腦上的快取抓取)，並寫入 obj/project.assets.json 檔案，該檔案是編譯及執行範例的必要項目。

   > [!IMPORTANT]
   > 如果您使用 .NET Core 1.x 版本的 SDK，則必須在呼叫 `dotnet new` 之後自行呼叫 `dotnet restore`。

2. `dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) 呼叫 [`dotnet build`](../tools/dotnet-build.md) 以確保建置目標已經建置好，然後呼叫 `dotnet <assembly.dll>` 執行目標應用程式。

    ```console
    $ dotnet run
    Hello World!
    ```

    或者，您也可以執行 [`dotnet build`](../tools/dotnet-build.md) 來編譯程式碼，而不執行建置主控台應用程式。 這會產生編譯成 DLL 檔案的應用程式，您可以在 Windows 上使用 `dotnet bin\Debug\netcoreapp2.1\Hello.dll` (在非 Windows 系統上則使用 `/`) 來執行此應用程式。 您也可以指定應用程式的引數，您將於稍後看到該主題。

    ```console
    $ dotnet bin\Debug\netcoreapp2.1\Hello.dll
    Hello World!
    ```

    在進階案例中，可以建置應用程式做為一組獨立的平台專屬檔案，您可以將其部署到不需安裝 .NET Core 的電腦上並加以執行。 如需詳細資訊，請參閱 [.NET Core 應用程式部署](../deploying/index.md)。

### <a name="augmenting-the-program"></a>擴充程式

讓我們稍微變更程式。 Fibonacci 數字很有趣，因此讓我們也新增該數字，以使用引數來歡迎執行應用程式的人員。

1. 以下列程式碼取代 *Program.cs* 檔案的內容：

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]

2. 執行 [`dotnet build`](../tools/dotnet-build.md) 以編譯變更。

3. 執行將參數傳遞至應用程式的程式：

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

就是這麼容易！  您可以隨意擴充 `Program.cs`。

## <a name="working-with-multiple-files"></a>使用多個檔案

單一檔案適用於簡單的一次性程式，但如果您要建置更複雜的應用程式，可能在專案上要具備多個原始程式檔。
請藉由快取某些 Fibonacci 值，再新增一些遞迴功能，從先前的 Fibonacci 範例開始建置。

1. 使用下列程式碼在 *Hello* 目錄中新增名為 *FibonacciGenerator.cs* 的檔案：

   [!code-csharp[Fibonacci Generator](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

2. 變更 *Program.cs* 檔案中的 `Main` 方法，以具現化新的類別並呼叫其方法，如下列範例所示：

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. 執行 [`dotnet build`](../tools/dotnet-build.md) 以編譯變更。

4. 藉由執行 [`dotnet run`](../tools/dotnet-run.md) 來執行您的應用程式。 以下顯示程式輸出：

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

一旦您準備好散發您的應用程式，請使用 [`dotnet publish`](../tools/dotnet-publish.md) 命令在 _bin\\debug\\netcoreapp2.1\\publish\\_ 中產生 _publish_ 資料夾 (針對非 Windows 系統，請使用 `/`)。 您可以將 _publish_  資料夾的內容散發到其他平台，只要那些平台已安裝 dotnet 執行階段。

您可以使用 [dotnet](../tools/dotnet.md) 命令來執行已發佈的應用程式：

```console
$ dotnet bin\Debug\netcoreapp2.1\publish\Hello.dll
Hello World!
```

## <a name="conclusion"></a>結論

就是這麼容易！ 現在，您可以開始使用這裡學到的基本概念，建立您自己的程式。

## <a name="see-also"></a>另請參閱

- [使用 .NET Core CLI 工具組織和測試專案](testing-with-cli.md)
- [使用 CLI 發佈 .NET Core 應用程式](../deploying/deploy-with-cli.md)
- [深入了解應用程式部署](../deploying/index.md)

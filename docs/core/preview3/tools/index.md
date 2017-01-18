---
title: ".NET Core 命令列介面 (CLI) 工具"
description: "何謂命令列介面 (CLI) 和其主要功能的概觀"
keywords: "CLI, CLI 工具, .NET, .NET Core"
author: blackdwarf
ms.author: mairaw
manager: wpickett
ms.date: 10/06/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: b70e9ac0-c8be-49f7-9332-95ab93e0e7bc
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: d9e689524a3100f1c5c129bdf13ed691a850ad2e

---

# <a name="net-core-command-line-interface-tools"></a>.NET Core 命令列介面工具

.NET Core 命令列介面 (CLI) 是新的基礎跨平台工具鏈，適用於開發 .NET Core 應用程式。 它是「基礎」，原因是它是在其上建置其他較高階工具 (例如整合式開發環境 (IDE)、編輯器和建置 Orchestrator 的主要層。 

它也預設為跨平台，而且每個支援平台上都有相同的介面區。 這表示，當您了解如何使用工具時，即可從任何支援平台透過相同的方式來使用它。 

## <a name="installation"></a>安裝
使用任何工具時，第一件事都是要取得適合電腦的工具。 您可以根據自己的案例，使用原生安裝程式來安裝 CLI，或使用安裝殼層指令碼。

原生安裝程式主要是為了開發人員電腦而設計。 CLI 是使用每個支援平台的原生安裝機制所散發 (例如 Ubuntu 上的 DEB 套件或 Windows 上的 MSI 套件組合)。 這些安裝程式會視需要安裝並設定環境，以讓使用者在安裝後可立即使用 CLI。 不過，它們也需要電腦的系統管理權限。 您可以檢視 [.NET Core 使用者入門頁面](https://aka.ms/dotnetcoregs)上的安裝指示。

另一方面來看，安裝指令碼則不需要系統管理權限。 不過，它們也不會在電腦上安裝任何必要條件；您必須手動安裝所有必要條件。 指令碼大部分用於設定組建伺服器，或您想要安裝工具但沒有系統管理權限時 (請確實注意上述先決條件警告)。 如需詳細資訊，請參閱[安裝指令碼參考主題](dotnet-install-script.md)。 如果您對如何在持續整合 (CI) 組建伺服器設定 CLI 感興趣，則可以查看 [CI 伺服器的 CLI](using-ci-with-cli.md) 主題。 

根據預設，CLI 會以並存 (SxS) 方式進行安裝。 這表示在任何指定時間，單一電腦上可同時存在多個版本的 CLI 工具。 [驅動程式](#driver)小節會詳細說明如何使用正確的版本。 

### <a name="what-commands-come-in-the-box"></a>方塊中會有什麼命令？
預設會安裝下列命令：

* [new](dotnet-new.md)
* [restore](dotnet-restore.md)
* [run](dotnet-run.md)
* [build](dotnet-build.md)
* [test](dotnet-test.md)
* [publish](dotnet-publish.md)
* [pack](dotnet-pack.md)

也有方法可以根據專案來匯入更多命令，以及新增專屬命令。 [擴充性](#extensibility)小節會更詳細說明這個項目。 

## <a name="working-with-the-cli"></a>使用 CLI

在更加深入之前，請先從一萬英尺的視野確認如何使用 CLI。 下列範例利用 CLI 標準安裝中的數個命令，來初始化新的簡單主控台應用程式、還原相依性、建置應用程式，然後執行它。 

```console
dotnet new
dotnet restore
dotnet build --output /stuff
dotnet /stuff/new.dll
```

如上述範例所見，有一種使用 CLI 工具的模式。 在該模式內，我們可以識別每個命令的三個主要部分︰

1. [驅動程式 ("dotnet")](#driver)
2. [命令，或稱「動詞」](#the-verb)
3. [命令引數](#the-arguments)

### <a name="driver"></a>驅動程式
驅動程式命名為 [dotnet](dotnet.md)。 它是您叫用的第一個部分。 驅動程式有兩個責任︰

1. 執行可攜式應用程式
2. 執行動詞

用法取決於命令列上所指定的內容。 在第一個案例中，您將指定 `dotnet` 使用下列類似方式執行的可攜式應用程式 DLL：`dotnet /path/to/your.dll`。 

在第二個案例中，驅動程式嘗試叫用指定的命令。 這會啟動 CLI 命令執行程序。 首先，驅動程式決定您想要的工具版本。 您可以在 [global.json](global-json.md) 檔案中，使用 `version` 屬性指定版本。 如果無法使用，則驅動程式會尋找磁碟上安裝的最新版工具，並使用該版本。 決定版本之後，它會執行命令。 

### <a name="the-verb"></a>「動詞」
動詞只是執行動作的命令。 `dotnet build` 會建置程式碼。 `dotnet publish` 會發行程式碼。 動詞會實作為根據慣例所命名的主控台應用程式：`dotnet-{verb}`。 所有邏輯都是在代表動詞的主控台應用程式中實作。 

### <a name="the-arguments"></a>引數
您在命令列上傳遞的引數就是正在叫用之實際動詞/命令的引數。 例如，當您輸入 `dotnet publish --output publishedapp` 時，會將 `--output` 引數傳遞給 `publish` 命令。 

## <a name="types-of-application-portability"></a>應用程式可攜性的類型
CLI 可透過兩種主要方式讓應用程式具有可攜性︰

1. 可在安裝 .NET Core 的任何位置執行的完全可攜式應用程式
2. 獨立部署

您可以在 [.NET Core 應用程式部署](../deploying/index.md)主題中深入了解這兩項。 

## <a name="migration-from-preview-3projectjson"></a>從 Preview 3/project.json 移轉
如果您使用 Preview 2 工具和 project.json 專案，您可以查閱 [dotnet migrate](dotnet-migrate.md) 命令文件以熟悉命令以及如何移轉專案。 

> **注意：**`dotnet migrate` 命令目前不會移轉 Preview 2 之前版本的 project.json 檔案。 

## <a name="extensibility"></a>擴充性
當然，並非您可以在工作流程中使用的工具都是核心 CLI 工具的一部分。 不過，.NET Core CLI 具有擴充性模型，可讓您指定專案的額外工具。 您可以在 [.NET Core CLI 擴充性模型](extensibility.md)主題中深入了解。

## <a name="summary"></a>總結
這是最重要 CLI 功能的簡短概觀。 您可以使用這個網站上的參考和概念性主題深入了解。 您也可以使用其他資源︰
* [dotnet/CLI](https://github.com/dotnet/cli/) GitHub 存放庫
* [使用者入門指示](https://aka.ms/dotnetcoregs/)



<!--HONumber=Nov16_HO3-->



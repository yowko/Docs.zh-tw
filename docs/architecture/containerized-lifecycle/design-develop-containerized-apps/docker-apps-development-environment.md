---
title: Docker 應用程式的開發環境
description: 了解可支援 Docker 開發生命週期的最重要開發工具選項。
ms.date: 02/15/2019
ms.openlocfilehash: 35236e75f47e830d0970ca9cfd074d9a69e6f85c
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214299"
---
# <a name="development-environment-for-docker-apps"></a>Docker 應用程式的開發環境

## <a name="development-tools-choices-ide-or-editor"></a>開發工具選擇：IDE 或編輯器

不論您偏好使用完整且強大的 IDE，還是輕量型的敏捷式編輯器，Microsoft 都能支援您開發 ASP.NET Core 應用程式。

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>Visual Studio Code 和 Docker CLI (適用於 Mac、Linux 和 Windows 的跨平台工具)

如果您偏好使用支援任何開發語言的輕量型、跨平台編輯器，您可以使用 Visual Studio Code 和 Docker CLI。 這些產品提供簡單但強大的體驗，這對簡化開發人員工作流程來說非常重要。 藉由安裝「適用於 Mac 的 Docker」或「適用於 Windows 的 Docker」(開發環境)，Docker 開發人員可以使用單一 Docker CLI 來建置 Windows 或 Linux (執行階段環境) 的應用程式。 此外，Visual Studio Code 支援 Docker 的延伸模組 (內含適用於 Dockerfile 的 IntelliSense)，以及可從編輯器執行 Docker 命令的捷徑工作。

> [!NOTE]
> 若要下載 Visual Studio Code，請前往 <https://code.visualstudio.com/download>。
>
> 若要下載適用於 Mac 和 Windows 的 Docker，請前往 <https://www.docker.com/products/docker>。

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a>具備 Docker 工具的 Visual Studio (Windows 開發電腦)

我們建議您使用已啟用內建 Docker 工具的 Visual Studio 2017 (或更新版本)。 使用 Visual Studio，您可以直接在所選 Docker 環境中開發、執行及驗證應用程式。 請按 F5 鍵直接在 Docker 主機中對您的應用程式 (單一容器或多個容器) 進行偵錯，或按 Ctrl+F5 來編輯及重新整理您的應用程式，而不需要重建容器。 這是 Windows 開發人員用以建立 Linux 或 Windows 之 Docker 容器的最簡單且最強大選擇。

### <a name="visual-studio-for-mac-mac-development-machine"></a>Visual Studio for Mac (Mac 開發電腦)

您可以在開發以 Docker 為基礎的應用程式時，使用 [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)。 相較於 Visual Studio Code for Mac，Visual Studio for Mac 提供更豐富的 IDE。

## <a name="language-and-framework-choices"></a>語言和架構選擇

您可以使用 Microsoft 工具　搭配大部分的現代語言來開發 Docker 應用程式。 下列是初始清單，但不僅限於此：

- .NET Core 與 ASP.NET Core
- Node.js
- 移至
- Java
- Ruby
- Python

基本上，您可以使用 Linux 或 Windows 中 Docker 所援的任何現代語言。

>[!div class="step-by-step"]
>[上一頁](deploy-azure-kubernetes-service.md)
>[下一頁](docker-apps-inner-loop-workflow.md)

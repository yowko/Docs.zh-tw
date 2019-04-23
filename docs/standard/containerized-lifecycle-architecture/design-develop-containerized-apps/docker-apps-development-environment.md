---
title: Docker 應用程式的開發環境
description: 了解最重要的開發工具選項可支援 Docker 開發生命週期。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 3a2fcbe3b9380083622b6ce72cea4bab17d7c2ea
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767936"
---
# <a name="development-environment-for-docker-apps"></a>Docker 應用程式的開發環境

## <a name="development-tools-choices-ide-or-editor"></a>開發工具選擇：IDE 或編輯器

不論您偏好使用完整且功能強大的 IDE，還是輕量型的敏捷式編輯器中，如果 Microsoft 擁有您分憂解勞談到開發 Docker 應用程式。

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>Visual Studio Code 和 Docker CLI （適用於 Mac、 Linux 和 Windows 的跨平台工具）

如果您想支援任何開發語言的輕量型、 跨平台編輯器時，您可以使用 Visual Studio Code 和 Docker CLI。 這些產品提供簡單但強大的體驗，也就是很重要的簡化開發人員工作流程。 藉由安裝 「 Docker for Mac"或"Docker for Windows 」 （開發環境），Docker 開發人員可以使用單一 Docker CLI，來建置 Windows 或 Linux （執行階段環境） 的應用程式。 此外，Visual Studio Code 支援 Docker 具有 IntelliSense 的 Dockerfiles 和捷徑工作從編輯器執行 Docker 命令延伸模組。

> [!NOTE]
>
> 若要下載 Visual Studio Code，請移至<https://code.visualstudio.com/download>。
>
> 若要下載適用於 Mac 和 Windows 的 Docker，請移至<https://www.docker.com/products/docker>。

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a>Visual Studio 中使用 Docker 工具 （Windows 開發電腦）

我們建議您使用 Visual Studio 2017 （或更新版本） 以啟用內建 Docker 工具。 您可以使用 Visual Studio，開發、 執行及驗證您的應用程式，直接在所選的 Docker 環境中。 按下 F5 以偵錯您的應用程式 （單一容器或多個容器） 直接在 Docker 主機，或按 Ctrl + F5 編輯和重新整理您的應用程式，而不需要重建容器。 這是最簡單且最強大的選擇來建立 Linux 或 Windows 的 Docker 容器的 Windows 開發人員。

### <a name="visual-studio-for-mac-mac-development-machine"></a>Visual Studio for Mac （Mac 開發電腦）

您可以使用[Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)開發以 Docker 為基礎的應用程式時。 Visual Studio for Mac 提供更豐富的 IDE，相較於 Visual Studio Code for mac。

## <a name="language-and-framework-choices"></a>語言和架構選項

您可以開發 Docker 應用程式使用 Microsoft 工具與最新的語言。 以下是初始的清單，但不是限於它：

- .NET Core 與 ASP.NET Core
- Node.js
- 移至
- Java
- Ruby
- Python

基本上，您可以使用現代的語言支援在 Linux 或 Windows 的 Docker。

>[!div class="step-by-step"]
>[上一頁](deploy-azure-kubernetes-service.md)
>[下一頁](docker-apps-inner-loop-workflow.md)

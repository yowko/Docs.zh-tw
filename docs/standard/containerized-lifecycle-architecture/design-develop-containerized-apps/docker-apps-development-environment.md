---
title: Docker 應用程式的開發環境
description: 了解最重要的開發工具選項可支援 Docker 開發生命週期。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 1d22b45a8eee9198d337df9f0b8b4b78371fa31a
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219993"
---
# <a name="development-environment-for-docker-apps"></a>Docker 應用程式的開發環境

## <a name="development-tools-choices-ide-or-editor"></a>開發工具選擇：IDE 或編輯器

不論您偏好使用完整且功能強大的 IDE，還是輕量型的敏捷式編輯器中，如果 Microsoft 擁有您分憂解勞談到開發 Docker 應用程式。

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>Visual Studio Code 和 Docker CLI （適用於 Mac、 Linux 和 Windows 的跨平台工具）

如果您想支援任何開發語言的輕量型、 跨平台編輯器時，您可以使用 Visual Studio Code 和 Docker CLI。 這些產品提供簡單但強大的體驗，也就是很重要的簡化開發人員工作流程。 藉由安裝 「 Docker for Mac"或"Docker for Windows 」 （開發環境），Docker 開發人員可以使用單一 Docker CLI，來建置 Windows 或 Linux （執行階段環境） 的應用程式。 此外，Visual Studio Code 支援 Docker 具有 IntelliSense 的 Dockerfiles 和捷徑工作從編輯器執行 Docker 命令延伸模組。

> [!NOTE]
> 若要下載 Visual Studio Code，請移至<https://code.visualstudio.com/download>。

若要下載適用於 Mac 和 Windows 的 Docker，請移至<https://www.docker.com/products/docker>。

### <a name="visual-studio-with-docker-tools"></a>Visual Studio 中使用 Docker 工具

當您使用 Visual Studio 2015，您就可以安裝附加元件工具 [Docker Tools for Visual Studio]。 Visual Studio 2017，Docker 工具有內建的已。 在這兩種情況下，您可以開發、 執行及驗證您的應用程式，直接在所選的 Docker 環境中。 F5 應用程式 （單一容器或多個容器） 直接在 Docker 主機並偵錯，或按 Ctrl + F5 編輯和重新整理您的應用程式，而不需要重建容器。 這是 Windows 開發人員建立 Linux 或 Windows 的 Docker 容器的最簡單且功能更強大的選擇。

> [!NOTE]
> 若要下載 Visual Studio Docker 工具，請移至<https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>。

## <a name="language-and-framework-choices"></a>語言和架構選項

您可以開發 Docker 應用程式及現今大部分語言的 Microsoft 工具。 以下是初始的清單，但不是限於它：

-   .NET Core 與 ASP.NET Core
-   Node.js
-   Golang
-   Java
-   Ruby
-   Python

基本上，您可以使用現代的語言支援在 Linux 或 Windows 的 Docker。

>[!div class="step-by-step"]
>[上一頁](deploy-azure-kubernetes-service.md)
>[下一頁](docker-apps-inner-loop-workflow.md)
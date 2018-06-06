---
title: Docker 應用程式的開發環境
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 4adbdd7099dfc1c5ef13d5bbb4370ae2f14aba1e
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696776"
---
# <a name="development-environment-for-docker-apps"></a>Docker 應用程式的開發環境

## <a name="development-tools-choices-ide-or-editor"></a>開發工具選擇：IDE 或編輯器

不論您偏好使用完整且功能強大的 IDE 或是套輕量型且敏捷式軟體開發編輯器中，如果 Microsoft 有您涵蓋談到開發 Docker 應用程式。

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>Visual Studio 程式碼和 Docker CLI （如 Mac、 Linux 及 Windows 的跨平台工具）

如果您想支援任何開發語言的輕量型、 跨平台編輯器，您可以使用 Visual Studio 程式碼和 Docker CLI。 這些產品，提供簡單但強大體驗，這相當重要的開發人員工作流程可簡化程序。 藉由安裝"Docker for Mac"或"Docker for Windows"（開發環境），Docker 開發人員可以使用單一的 Docker CLI 建置應用程式的 Windows 或 Linux （執行階段環境）。 此外，Visual Studio 程式碼支援對具有 IntelliSense 的 Dockerfiles 和快顯工作從編輯器執行 Docker 命令的 Docker 擴充功能。

> [!NOTE]
> 若要下載 Visual Studio 程式碼，請移至<https://code.visualstudio.com/download>。

若要下載 Mac 和 Windows Docker，請移至<https://www.docker.com/products/docker>。

### <a name="visual-studio-with-docker-tools"></a>Visual Studio 和 Docker 工具

當您使用 Visual Studio 2015，您就可以安裝附加元件工具 [Visual Studio 的 Docker 工具]。 針對 Visual Studio 2017，Docker 工具來自內建的已。 在這兩種情況下，您可以開發、 執行和驗證您的應用程式，直接在所選的 Docker 環境中。 F5 應用程式 （單一容器或多個容器） 直接在 Docker 主機並偵錯，或按 Ctrl + F5 鍵來編輯和重新整理您的應用程式，而不必重建容器。 這是 Windows 開發人員建立 Docker 容器的 Linux 或 Windows 的最簡單且功能更強大的選擇。

> [!NOTE]
> 若要下載 Visual Studio 的 Docker 工具，請移至<https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>。

## <a name="language-and-framework-choices"></a>語言和架構選項

您可以開發 Docker 應用程式和與大多數最新型的程式設計語言的 Microsoft 工具。 以下是初始的清單，但不是限於它：

-   .NET core 與 ASP.NET Core
-   Node.js
-   Golang
-   Java
-   Ruby
-   Python

基本上，您可以使用現代 Docker 的 Linux 或 Windows 所支援的語言。


>[!div class="step-by-step"]
[上一個] (協調-高的延展性-availability.md) [下一步] (docker-應用程式-內部-迴圈-workflow.md)

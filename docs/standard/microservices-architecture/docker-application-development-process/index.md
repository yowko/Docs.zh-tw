---
title: Docker 應用程式的開發程序
description: 容器化 .NET 應用程式的 .NET 微服務架構 | Docker 應用程式的開發程序
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 881817f4f1007edad85eefb9002d56764cbf2a02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574780"
---
# <a name="development-process-for-docker-based-applications"></a>Docker 應用程式的開發程序

*依您喜歡的方式來開發容器化 .NET 應用程式，可以是 Visual Studio 和 Visual Studio Tools for Docker 導向的 IDE，或是 Docker CLI 和 Visual Studio Code 導向的 CLI/編輯器。*

## <a name="development-environment-for-docker-apps"></a>Docker 應用程式的開發環境

### <a name="development-tool-choices-ide-or-editor"></a>開發工具選擇：IDE 或編輯器

不論您偏好使用完整且強大的 IDE，還是輕量型的敏捷式編輯器，Microsoft 都有相關工具可供您用來開發 Docker 應用程式。

**Visual Studio (適用於 Windows)**. 若要開發以 Docker 為基礎的應用程式，請使用隨附已內建 Docker 工具的 Visual Studio 2017 或更新版本。 Docker 工具可讓您直接在目標 Docker 環境中開發、執行和驗證應用程式。 您可以按 F5 鍵，直接在 Docker 主機中執行並偵錯您的應用程式 (單一容器或多個容器)，或按 CTRL+F5 來編輯及重新整理您的應用程式，而不需要重建容器。 這是以 Docker 為基礎之應用程式的最強大開發選擇。

**Visual Studio for Mac**. 它是在 macOS 上執行的 IDE (即 Xamarin Studio 的演進)，並支援以 Docker 為基礎的應用程式開發。 針對在 Mac 電腦上工作同時想要使用功能強大之 IDE 的開發人員，這應該是偏好選項。

**Visual Studio Code 和 Docker CLI**。 如果您偏好使用支援任何開發語言之輕量型且跨平台的編輯器，您可以使用 Microsoft Visual Studio Code (VS Code) 和 Docker CLI。 這是適用於 Mac、Linux 和 Windows 的跨平台開發方法。

藉由安裝 [Docker Community Edition (CE)](https://www.docker.com/community-edition) 工具，您可以使用單一 Docker CLI 來建置 Windows 和 Linux 應用程式。 此外，Visual Studio Code 支援 Docker 的延伸模組 (例如適用於 Dockerfile 的 IntelliSense)，以及可從編輯器執行 Docker 命令的捷徑工作。

### <a name="additional-resources"></a>其他資源

-   **Visual Studio Tools for Docker**
    [*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)

-   **Visual Studio Code**。 官方網站。
    [*https://code.visualstudio.com/download*](https://code.visualstudio.com/download)

-   **適用於 Mac 和 Windows 的 Docker Community Edition (CE)**
    [*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>Docker 容器的 .NET 語言和 Framework

如本指南稍早章節所述，開發 Docker 容器化 .NET 應用程式時，您可以使用 .NET Framework、.NET Core 或開放原始碼 Mono 專案。 當目標設為 Linux 或 Windows 容器時，您可以根據所使用的 .NET Framework，以 C\#、F\# 或 Visual Basic 進行開發。 如需 .NET 語言的詳細資訊，請參閱部落格文章 [The .NET Language Strategy](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/) (.NET 語言策略)。


>[!div class="step-by-step"]
[上一個] (../architect-microservice-container-applications/using-azure-service-fabric.md) [下一個] (docker-app-development-workflow.md)

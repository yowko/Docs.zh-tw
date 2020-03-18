---
title: 基於 Docker 的應用程式的開發過程
description: 獲取開發基於 Docker 的應用程式的選項的高級概述。 使用您選擇的 Windows 視覺工作室、適用于 Mac 的視覺化工作室或多平臺支援（Windows、macOS 和 Linux）的視覺化工作室代碼。
ms.date: 01/30/2020
ms.openlocfilehash: 799aa6fc742a8fb763ec5a7ae3cf3f70f89bed6d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "77502724"
---
# <a name="development-process-for-docker-based-applications"></a>基於 Docker 的應用程式的開發過程

*開發容器化 .NET 應用程式，以您喜歡的方式開發，無論是整合式開發環境 （IDE），還是以 Docker 或 CLI/編輯器為重點的開發人員工作室和視覺化工作室工具，以 Docker CLI 和 Visual Studio 代碼為重點。*

## <a name="development-environment-for-docker-apps"></a>Docker 應用程式的開發環境

### <a name="development-tool-choices-ide-or-editor"></a>開發工具選擇：IDE 或編輯器

不論您偏好使用完整且強大的 IDE，還是輕量型的敏捷式編輯器，Microsoft 都有相關工具可供您用來開發 Docker 應用程式。

**Visual Studio (適用於 Windows)。** 基於 Docker 的 .NET Core 3.1 應用程式開發與 Visual Studio 需要 Visual Studio 2019 版本 16.4 或更高版本。 Visual Studio 2019 附帶了已內置的 Docker 工具。 Docker 工具可讓您直接在目標 Docker 環境中開發、執行和驗證應用程式。 您可以按 F5 鍵，直接在 Docker 主機中執行並偵錯您的應用程式 (單一容器或多個容器)，或按 CTRL+F5 來編輯及重新整理您的應用程式，而不需要重建容器。 這是以 Docker 為基礎之應用程式的最強大開發選擇。

**適用于 Mac 的視覺工作室。** 這是一個IDE，Xamarin工作室的演變，運行在macOS。 對於 .NET Core 3.1 開發，它需要版本 8.4 或更高版本。 對於在 macOS 機器中工作的開發人員來說，這應該是首選選擇，他們也希望使用功能強大的 IDE。

**Visual Studio Code 和 Docker CLI**。 如果您更喜歡支援任何開發語言的羽量級跨平臺編輯器，則可以使用 Visual Studio 代碼和 Docker CLI。 這是一種適用于 macOS、Linux 和 Windows 的跨平臺開發方法。 此外，Visual Studio Code 支援 Docker 的延伸模組 (例如適用於 Dockerfile 的 IntelliSense)，以及可從編輯器執行 Docker 命令的捷徑工作。

透過安裝 [Docker Desktop Community Edition (CE)](https://hub.docker.com/search/?type=edition&offering=community)，您可以使用單一 Docker CLI 來建置 Windows 和 Linux 應用程式。

### <a name="additional-resources"></a>其他資源

- **視覺工作室**。 官方網站。 \
  [https://visualstudio.microsoft.com/vs/](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

- **視覺工作室代碼**。 官方網站。 \
  <https://code.visualstudio.com/download>

- **用於 Windows 社區版的 Docker 桌面 （CE）** \
  [https://hub.docker.com/editions/community/docker-ce-desktop-windows](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

- **用於 Mac 社區版的 Docker 桌面 （CE）** \
  [https://hub.docker.com/editions/community/docker-ce-desktop-mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>Docker 容器的 .NET 語言和 Framework

如本指南稍早章節所述，開發 Docker 容器化 .NET 應用程式時，您可以使用 .NET Framework、.NET Core 或開放原始碼 Mono 專案。 當目標設為 Linux 或 Windows 容器時，您可以根據所使用的 .NET Framework，以 C\#、F\# 或 Visual Basic 進行開發。 如需 .NET 語言的詳細資訊，請參閱部落格文章 [The .NET Language Strategy](https://devblogs.microsoft.com/dotnet/the-net-language-strategy/) (.NET 語言策略)。

>[!div class="step-by-step"]
>[上一個](../architect-microservice-container-applications/scalable-available-multi-container-microservice-applications.md)
>[下一個](docker-app-development-workflow.md)

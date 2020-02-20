---
title: 以 Docker 為基礎之應用程式的開發流程
description: 取得開發以 Docker 為基礎的應用程式之選項的高階總覽。 針對多平臺支援（Windows、macOS 和 Linux）使用您選擇的 Windows、Visual Studio for Mac 或 Visual Studio Code Visual Studio。
ms.date: 01/30/2020
ms.openlocfilehash: 799aa6fc742a8fb763ec5a7ae3cf3f70f89bed6d
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77502724"
---
# <a name="development-process-for-docker-based-applications"></a>以 Docker 為基礎之應用程式的開發流程

*以您喜歡的方式開發容器化 .NET 應用程式，整合式開發環境（IDE）著重于 docker 的 Visual Studio 和 Visual Studio 工具，或是以 Docker CLI 和 Visual Studio Code 為焦點的 CLI/編輯器。*

## <a name="development-environment-for-docker-apps"></a>Docker 應用程式的開發環境

### <a name="development-tool-choices-ide-or-editor"></a>開發工具選擇：IDE 或編輯器

不論您偏好使用完整且強大的 IDE，還是輕量型的敏捷式編輯器，Microsoft 都有相關工具可供您用來開發 Docker 應用程式。

**Visual Studio (適用於 Windows)。** 以 Docker 為基礎的 .NET Core 3.1 應用程式開發使用 Visual Studio 需要 Visual Studio 2019 16.4 或更新版本。 Visual Studio 2019 隨附已內建的 Docker 工具。 Docker 工具可讓您直接在目標 Docker 環境中開發、執行和驗證應用程式。 您可以按 F5 鍵，直接在 Docker 主機中執行並偵錯您的應用程式 (單一容器或多個容器)，或按 CTRL+F5 來編輯及重新整理您的應用程式，而不需要重建容器。 這是以 Docker 為基礎之應用程式的最強大開發選擇。

**Visual Studio for Mac。** 它是一個 IDE，Xamarin Studio 的演進，在 macOS 中執行。 針對 .NET Core 3.1 開發，它需要8.4 版或更新版本。 對於在同時想要使用功能強大之 IDE 的 macOS 電腦上工作的開發人員而言，這應該是慣用的選擇。

**Visual Studio Code 和 Docker CLI**。 如果您偏好支援任何開發語言的輕量和跨平臺編輯器，您可以使用 Visual Studio Code 和 Docker CLI。 這是適用于 macOS、Linux 和 Windows 的跨平臺開發方法。 此外，Visual Studio Code 支援 Docker 的延伸模組 (例如適用於 Dockerfile 的 IntelliSense)，以及可從編輯器執行 Docker 命令的捷徑工作。

透過安裝 [Docker Desktop Community Edition (CE)](https://hub.docker.com/search/?type=edition&offering=community)，您可以使用單一 Docker CLI 來建置 Windows 和 Linux 應用程式。

### <a name="additional-resources"></a>其他資源

- **Visual Studio**。 官方網站。 \
  [https://visualstudio.microsoft.com/vs/](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

- **Visual Studio Code** \(英文\)。 官方網站。 \
  <https://code.visualstudio.com/download>

- **適用於 Windows Community Edition (CE) 的 Docker Desktop** \
  [https://hub.docker.com/editions/community/docker-ce-desktop-windows](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

- **適用於 Mac Community Edition (CE) 的 Docker Desktop** \
  [https://hub.docker.com/editions/community/docker-ce-desktop-mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>Docker 容器的 .NET 語言和 Framework

如本指南稍早章節所述，開發 Docker 容器化 .NET 應用程式時，您可以使用 .NET Framework、.NET Core 或開放原始碼 Mono 專案。 當目標設為 Linux 或 Windows 容器時，您可以根據所使用的 .NET Framework，以 C\#、F\# 或 Visual Basic 進行開發。 如需 .NET 語言的詳細資訊，請參閱部落格文章 [The .NET Language Strategy](https://devblogs.microsoft.com/dotnet/the-net-language-strategy/) (.NET 語言策略)。

>[!div class="step-by-step"]
>[上一頁](../architect-microservice-container-applications/scalable-available-multi-container-microservice-applications.md)
>[下一頁](docker-app-development-workflow.md)

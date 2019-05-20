---
title: 選擇在 Docker 容器使用 .NET Core 的時機
description: 適用於容器化 .NET 應用程式的.NET 微服務架構 | 選擇在 Docker 容器使用 .NET Core 的時機
ms.date: 09/11/2018
ms.openlocfilehash: 54ed1b4bbb16352b8c99204383f85ffb25d62be7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644351"
---
# <a name="when-to-choose-net-core-for-docker-containers"></a>選擇在 Docker 容器使用 .NET Core 的時機

.NET Core 的模組性和輕量性質使其非常適用於容器。 部署和建立容器時，使用 .NET Core 時的映像大小，會遠小於使用 .NET Framework 時的大小。 相對來說，若要在容器使用.NET Framework，您的映像必須以 Windows Server Core 映像為基礎，而這會比用於 .NET Core 的 Windows Nano Server 或 Linux 映像還要繁重得多。

此外，.NET Core 可跨平台，因此您可以用 Linux 或 Windows 容器映像來部署伺服器應用程式。 不過，如果您使用傳統的.NET Framework，則只能部署以 Windows Server Core 為基礎的映像。

下列詳細說明選擇 .NET Core 的理由。

## <a name="developing-and-deploying-cross-platform"></a>跨平台開發和部署

如果您的目標是擁有一個可在 Docker (Linux 和 Windows) 支援的多個平台上執行的應用程式 (Web 應用程式或服務)，正確的選擇顯然會是.NET Core，因為 .NET Framework 僅支援 Windows。

.NET Core 也支援 macOS 作為開發平台。 不過，當您在 Docker 主機部署容器時，就目前來說，該主機必須以 Linux 或 Windows 為基礎。 例如在開發環境中，您可以使用在 Mac 上執行的 Linux VM。

[Visual Studio](https://www.visualstudio.com/vs/) 提供適用於 Windows 的整合式開發環境 (IDE)，並支援 Docker 開發。

[Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/) 是在 macOS 上執行的 IDE (即 Xamarin Studio 的演進)，並支援 Docker 型應用程式開發。 針對在 Mac 電腦上工作同時想要使用功能強大之 IDE 的開發人員，這應該是偏好選項。

您也可以在 macOS、Linux 和 Windows 上使用 [Visual Studio Code](https://code.visualstudio.com/) (VS Code)。 VS Code 支援 .NET Core，包括 IntelliSense 和偵錯。 因為 VS Code 是輕量型的編輯器，您可以在 Mac 上搭配 Docker CLI 和 [.NET Core 命令列介面 (CLI)](../../../core/tools/index.md) 加以使用，來開發容器化應用程式。 您還可以透過大多數協力廠商編輯器如 Sublime、Emacs、vi 及開放原始碼 Omnisharp 專案 (提供 IntelliSense 支援)，來將目標設定為 .NET Core。

除了 IDE 和編輯器，您也可以在所有支援的平台使用 [.NET Core CLI](../../../core/tools/index.md) 工具。

## <a name="using-containers-for-new-green-field-projects"></a>在新 (「綠地區」) 專案使用容器

儘管容器也可以用來將 Web 應用程式或服務裝入容器中 (遵循任何架構模式)，但通常會與微服務架構搭配使用。 .NET Framework 可用於 Windows 容器，但 .NET Core 的模組性和輕量性質使其更適合容器和微服務架構。 建立和部署容器時，使用 .NET Core 時的映像大小，會遠小於使用 .NET Framework 時的大小。

## <a name="creating-and-deploying-microservices-on-containers"></a>在容器上建立及部署微服務

您可以透過一般處理序，使用傳統的.NET Framework 來建置微服務型應用程式 (不含容器)。 如此一來，因為.NET Framework 已跨處理序安裝和共用，處理序即為輕量的，而且可快速啟動。 不過，如果您使用容器，傳統 .NET Framework 的映像也會以 Windows Server Core 為基礎，而這對於容器上的微服務方法而言過於沉重。

相較之下，如果您使用以容器基礎的微服務導向系統，.NET Core 會是最佳選項，因為 .NET Core 是輕量的。 此外，其相關的容器映像 (無論是 Linux 映像或 Windows Nano 映像) 都很精簡、小型，使容器負荷低、可快速啟動。

微服務意味著儘可能愈小愈好：在啟動時負荷極低、佔用空間小、限定環境小、只需要投注一小部分心力 (檢查 DDD，[網域驅動設計](https://en.wikipedia.org/wiki/Domain-driven_design))，而且能夠快速啟動和停止。 基於這些需求，您會需要使用小型且可快速具現化的容器映像，如 .NET Core 容器映像。

微服務架構也可讓您跨越服務界限混用技術。 如此一來，就能夠讓新的微服務逐步移轉到 .NET Core，與其他微服務或透過 Node.js、Python、Java、GoLang 或其他技術開發的服務結合使用。

## <a name="deploying-high-density-in-scalable-systems"></a>在可擴充的系統中部署高密度

當您的容器型系統需要最佳密度、細微性和效能時，.NET Core 和 ASP.NET Core 就是最好的選擇。 在傳統的 .NET Framework 中，ASP.NET Core 的速度可勝過 ASP.NET 10 倍，並且在像 Java servlet、Go 和 Node.js 等微服務領域中領先其他熱門的業界技術。

這對於微服務架構特別重要，您可以在其中執行數百個微服務 (容器)。 透過 Linux 或 Windows Nano 上的 ASP.NET Core 映像 (以 .NET Core 執行階段為基礎)，您可以大幅減少伺服器或 VM 的數量來執行系統，最終節省基礎架構和託管的成本。

>[!div class="step-by-step"]
>[上一頁](general-guidance.md)
>[下一頁](net-framework-container-scenarios.md)

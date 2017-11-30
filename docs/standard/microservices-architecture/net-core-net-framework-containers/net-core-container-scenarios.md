---
title: "選擇.NET Core 的 Docker 容器的時機"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |選擇.NET Core 的 Docker 容器的時機"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: b7e2322bab7937c41d4659fefef11c8937d5eae7
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="when-to-choose-net-core-for-docker-containers"></a>選擇.NET Core 的 Docker 容器的時機

.NET Core 的模組化和輕量型本質可讓您更適合的容器。 當您部署並啟動容器時，它的影像是遠比以.NET Framework 的.NET core。 相反地，若要使用.NET Framework 的容器，您必須依據您的映像 Windows Server Core 映像，也就是比 Windows Nano Server 或 Linux 映像，您使用適用於.NET Core 很高。

此外，.NET Core 是跨平台，因此您可以部署以 Linux 或 Windows 容器映像的伺服器應用程式。 不過，如果您使用傳統的.NET Framework，您可以只部署以在 Windows Server Core 基礎映像。

以下是原因的選擇.NET Core 的更詳細的說明。

## <a name="developing-and-deploying-cross-platform"></a>開發和部署跨平台

很明顯地，如果您的目標是讓適當的選擇支援 Docker （Linux 和 Windows） 的多個平台可以執行的應用程式 （web 應用程式或服務） 是.NET Core 因為只支援.NET Framework 的 Windows。

.NET core 也支援 macOS 做為開發平台。 不過，當您部署容器 Docker 主機時，該主機必須 （目前） 為基礎 Linux 或 Windows。 例如，在開發環境中，您可以使用在 mac 上執行的 Linux VM

[Visual Studio](https://www.visualstudio.com/)提供 Windows 整合式的開發環境 (IDE)，並且支援 Docker 開發。 

[Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/)的 IDE Xamarin Studio，在 macOS 中執行的演進，並且自 mid 2017 支援 Docker。

您也可以使用[Visual Studio Code](https://code.visualstudio.com/) (VS Code) macOS、 Linux 及 Windows 上。 VS Code 完全支援.NET Core，包括 IntelliSense 和偵錯。 因為 VS 程式碼是輕量型的編輯器，您可以用它來開發 Docker CLI 搭配使用的 Mac 上的容器化應用程式和[.NET Core 命令列介面 (CLI) 工具](https://docs.microsoft.com/dotnet/core/tools/?tabs=netcore2x)。 您也可以使用最第三方編輯器，例如適文字、 Emacs、 vi 和開放原始碼 OmniSharp 專案中，以針對.NET 語言會提供 IntelliSense 支援目標.NET Core。 除了 Ide 和編輯器中，您可以使用.NET 核心 CLI 所有支援平台。

## <a name="using-containers-for-new-green-field-projects"></a>使用新的 ("綠色-field") 專案的容器

容器常用於搭配 microservices 架構中，但是也可以使用以 web 應用程式或服務，請依照下列任何架構模式化。 您可以使用.NET Framework 上 Windows 容器，而在模組化和.NET Core 的輕量級性質讓容器和 microservices 架構完美。 當您建立和部署容器時，它的影像是遠比以.NET Framework 的.NET core。

## <a name="creating-and-deploying-microservices-on-containers"></a>建立及部署 microservices 容器

您可以使用傳統的.NET Framework 建置 microservices 基礎 （不含容器） 的應用程式使用一般的處理程序。 這樣一來，因為.NET Framework 已安裝並跨處理序，共用處理序較小，而且快速啟動。 不過，如果您使用的容器，傳統的.NET Framework 的映像也根據 Windows Server Core，因此在容器上 microservices 方法過重。

相反地，.NET Core 是最佳的候選項目，如果因為.NET Core 是輕量採用此 microservices 導向的系統容器中，為基礎。 此外，Linux 映像或 Windows Nano 映像，其相關的容器映像為 「 精實 」 和小型讓容器光線和快速啟動。

微服務是要盡量小： 時，能夠 light 向上微調，以具有較小的指紋，有小型繫結內容中，若要表示的考量，在小區域，並能夠啟動和停止快速。 如需這些需求，您會想要使用小型和快速產生的容器映像，例如.NET Core 容器映像。

Microservices 架構也可讓您跨服務界限混合技術。 這可讓工作連同其他 microservices 或 Node.js、 Python、 Java、 GoLang 或其他技術與開發服務的新 microservices 的漸進式移轉到.NET Core。

## <a name="deploying-high-density-in-scalable-systems"></a>在可調整的系統中部署高密度

當您容器為基礎的系統需求的最佳可能密度，資料粒度和效能時，.NET Core 與 ASP.NET Core 是最好的選擇。 ASP.NET Core 速度最多十倍比在傳統的.NET Framework 中，ASP.NET，則會發生其他業界技術，用於 microservices，例如 Java servlet、 移至及 Node.js。

這是特別有關 microservices 架構，您可以在其中有數百個 microservices （容器） 執行。 您可以使用 ASP.NET Core 映像 （根據.NET 核心執行階段） 在 Linux 或 Windows Nano 上，執行您的系統更低的數字的伺服器或 Vm，直到最終基礎結構中儲存成本和裝載。


>[!div class="step-by-step"]
[上一個](一般-guidance.md) [下一步] (net-framework 的容器-scenarios.md)

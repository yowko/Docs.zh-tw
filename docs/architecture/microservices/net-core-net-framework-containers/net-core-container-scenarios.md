---
title: 針對 Docker 容器選擇 .NET 5 的時機
description: 容器化 .NET 應用程式的 .NET 微服務架構 |選擇 .NET for Docker 容器的時機
ms.date: 01/13/2021
ms.openlocfilehash: 61909c91d795582af499456c65ae0d7b4f2911e2
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189274"
---
# <a name="when-to-choose-net-for-docker-containers"></a>選擇 .NET for Docker 容器的時機

.NET 5 的模組化和輕量本質讓容器更完美。 當您部署和啟動容器時，其映射的映射遠比使用 .NET Framework 的 .NET 5 還小。 相反地，若要使用容器的 .NET Framework，您必須以 Windows Server Core 映射作為映射的基礎，這比您用於 .NET 5 的 Windows Nano Server 或 Linux 映射高出許多。

此外，.NET 5 可跨平臺使用，因此您可以使用 Linux 或 Windows 容器映射來部署伺服器應用程式。 不過，如果您使用傳統的.NET Framework，則只能部署以 Windows Server Core 為基礎的映像。

以下是為何選擇 .NET 5 的詳細說明。

## <a name="developing-and-deploying-cross-platform"></a>跨平台開發和部署

很明顯地，如果您的目標是要讓應用程式 (web 應用程式或服務) 可在 Docker (Linux 和 Windows) 所支援的多個平臺上執行，則正確的選擇是 .NET 5，因為 .NET Framework 只支援 Windows。

.NET 5 也支援 macOS 作為開發平臺。 不過，當您在 Docker 主機部署容器時，就目前來說，該主機必須以 Linux 或 Windows 為基礎。 例如在開發環境中，您可以使用在 Mac 上執行的 Linux VM。

[Visual Studio](https://www.visualstudio.com/vs/) 提供適用於 Windows 的整合式開發環境 (IDE)，並支援 Docker 開發。

[Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/) 是在 macOS 上執行的 IDE (即 Xamarin Studio 的演進)，並支援 Docker 型應用程式開發。 這項工具應該是在 Mac 電腦中工作的開發人員慣用的選擇，也想要使用強大的 IDE。

您也可以在 macOS、Linux 和 Windows 上使用 [Visual Studio Code](https://code.visualstudio.com/) 。 Visual Studio Code 完全支援 .NET 5，包括 IntelliSense 和調試。 因為 VS Code 是輕量的編輯器，所以您可以使用它來開發電腦上的容器化應用程式，並搭配 Docker CLI 和 [.NET cli](../../../core/tools/index.md)。 您也可以使用大部分協力廠商編輯器（例如 Sublime、Emacs、vi 及開放原始碼 OmniSharp 專案）將目標設為 .NET 5，這也會提供 IntelliSense 支援。

除了 Ide 和編輯器，您也可以針對所有支援的平臺使用 [.NET CLI](../../../core/tools/index.md) 。

## <a name="using-containers-for-new-green-field-projects"></a>在新 (「綠地區」) 專案使用容器

儘管容器也可以用來將 Web 應用程式或服務裝入容器中 (遵循任何架構模式)，但通常會與微服務架構搭配使用。 您可以在 Windows 容器上使用 .NET Framework，但 .NET 5 的模組化和輕量本質可讓容器和微服務架構成為最理想的。 建立和部署容器時，使用 .NET Core 時的映像大小，會遠小於使用 .NET Framework 時的大小。

## <a name="create-and-deploy-microservices-on-containers"></a>在容器上建立和部署微服務

您可以透過一般處理序，使用傳統的.NET Framework 來建置微服務型應用程式 (不含容器)。 如此一來，因為.NET Framework 已跨處理序安裝和共用，處理序即為輕量的，而且可快速啟動。 不過，如果您使用容器，傳統 .NET Framework 的映像也會以 Windows Server Core 為基礎，而這對於容器上的微服務方法而言過於沉重。 不過，團隊還在尋求提升 .NET Framework 使用者體驗的機會。 最近， [Windows Server Core 容器映射的大小已縮減為 >40%](https://devblogs.microsoft.com/dotnet/we-made-windows-server-core-container-images-40-smaller)。

另一方面，如果您要採用以容器為基礎的微服務導向系統，.NET 5 是最好的選擇，因為 .NET 5 是輕量的。 此外，其相關的容器映射（適用于 Linux 或 Windows Nano Server）都是精簡且較小的映射，讓容器輕量並快速開始。

微服務意味著儘可能愈小愈好：在啟動時負荷極低、佔用空間小、限定環境小、只需要投注一小部分心力 (檢查 DDD，[網域驅動設計](https://en.wikipedia.org/wiki/Domain-driven_design))，而且能夠快速啟動和停止。 針對這些需求，您會想要使用小型和快速具現化的容器映射，例如 .NET 5 容器映射。

微服務架構也可讓您跨越服務界限混用技術。 這種方法可針對新的微服務逐步遷移至 .NET 5，以搭配其他微服務或使用以 Node.js、Python、JAVA、GoLang 或其他技術所開發的服務。

## <a name="deploying-high-density-in-scalable-systems"></a>在可擴充的系統中部署高密度

當您以容器為基礎的系統需要最佳的密度、細微性和效能時，.NET 和 ASP.NET Core 是您的最佳選擇。 ASP.NET Core 在傳統 .NET Framework 中的速度最高可快10倍，並且會引導微服務的其他熱門產業技術，例如 JAVA servlet、Go 和 Node.js。

這種方法特別適用于微服務架構，您可以在其中擁有數百個微服務 (容器) 執行。 使用 ASP.NET Core 映射 (以 Linux 或 Windows Nano 上的 .NET) 執行時間為基礎，您可以使用較低數目的伺服器或 Vm 來執行系統，最終節省基礎結構和裝載的成本。

>[!div class="step-by-step"]
>[上一個](general-guidance.md) 
>[下一步](net-framework-container-scenarios.md)

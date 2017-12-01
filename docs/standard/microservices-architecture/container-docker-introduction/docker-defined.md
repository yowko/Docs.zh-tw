---
title: "Docker 是什麼？"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |Docker 是什麼？"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: aa9cb379628fa91e5dc5b1b529f92db98fa59305
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="what-is-docker"></a>Docker 是什麼？

[Docker](https://www.docker.com/)是[開放原始碼專案](https://github.com/docker/docker)自動化應用程式的部署，做為可攜式且足可以在雲端或內部部署執行的容器。 Docker 也有[公司](https://www.docker.com/)會升級，而且這項技術的發展。 Docker 可與雲端，Linux 和 Windows 廠商，包括 Microsoft 的共同作業。

![](./media/image2.png)

**圖 2-2**。 Docker 部署混合式雲端的所有層級的容器

Docker 映像容器原生 Linux 及 Windows 上執行。 只在 Windows 主機上執行的 Windows 映像，並只在 Linux 主機上執行 Linux 映像。 在伺服器或 VM 主機。

您可以在 Windows、 Linux 或 macOS 開發。 在開發電腦執行的 Docker 主機的 Docker 映像部署所在，包括應用程式和其相依性。 在 Linux 或 macOS，您可以使用 Linux 的基礎，因此可以建立僅針對 Linux 容器映像的 Docker 主機。（macOS 上，您可以編輯的程式碼或執行 Docker CLI，但自撰寫本文時，容器請勿直接在 macOS 上執行）。在 Windows 上您可以建立 Linux 或 Windows 容器映像。

在 Windows 或 macOS [Docker Community Edition (CE)](https://www.docker.com/community-edition)裝載在開發環境中的容器，並提供額外的開發人員工具。 [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition)由 IT 團隊建置、 出貨，而且執行大型的業務關鍵應用程式。 ~ 這兩項產品會安裝必要的 VM （Docker 主機） 來裝載容器。 ~ 

[Windows 容器](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview)兩種類型的執行階段工作：

-   Windows Server 容器提供透過程序和命名空間隔離技術的應用程式隔離。 Windows Server 容器與容器主機和主機上執行的所有容器與容器共用核心。

-   HYPER-V 容器，在 Windows Server 容器提供高度最佳化的虛擬機器中執行每個容器的隔離上展開。 在此組態中，容器主機的核心不會與 HYPER-V 容器，提供更好的隔離共用。 HYPER-V 容器允許未受信任的和*惡意的多租用戶*相同主機上執行的應用程式。 HYPER-V 容器中的啟動時間和密度比 Windows Server 容器有稍微較少的效率。

這些容器的映像會建立並運作方式都相同。 但在容器的建立方式不同。 如需詳細資訊，請參閱[HYPER-V 容器](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview)。

## <a name="comparing-docker-containers-with-virtual-machines"></a>比較與虛擬機器的 Docker 容器

圖 2-3 顯示比較 Vm 和 Docker 容器。

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **虛擬機器****Docker 容器** 
                                                                                                                                                                                        
  ![](./media/image3.png)                                                                                                                                ![](./media/image4.png)
                                                                                                                                                                                        
  虛擬機器包含應用程式、 必要的程式庫或二進位檔，以及完整的客體作業系統。 完整的虛擬化需要比得以更多資源。 容器包括應用程式及其所有相依性。 不過，容器會將作業系統核心分享其他容器。 做為隔離的處理序使用者空間中的容器是在主機作業系統上執行。 除非在 HYPER-V 容器中，每個容器執行特殊的虛擬機器，每個容器內的位置。
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**圖 2-3**。 傳統的虛擬機器至 Docker 容器的比較

因為容器需要少很多的資源 （例如，它們不需要在完整作業系統），它們快速開頭，而且可以輕易地部署。 資源使用率低允許更高的密度。 您可以在相同的硬體單元上執行更多服務，並降低成本。

在相同的核心結果較少的隔離，提供的 Vm 上執行。

映像的主要目標是，它會使環境 （相依性） 相同跨不同的部署。 這表示您可以進行偵錯您的電腦上，然後將它部署到另一部電腦，以保證在相同的環境。

容器映像是封裝的應用程式或服務，然後以可靠且可重現的方式部署它的方法。 您可以說 Docker 有不只一種技術，但也原理和處理程序。

Docker 開發人員不說 「 ﹐ 我的電腦，為何不在生產環境中？ 」 他們說"執行 docker"。 Docker 封裝應用程式可以在任何支援的 Docker 環境上執行。 Docker 已封裝應用程式上所有部署目標 （開發、 品管暫存、 生產環境） 一致的方式執行。

>[!div class="step-by-step"]
[上一個](index.md) [下一步] (docker terminology.md)

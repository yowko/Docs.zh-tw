---
title: 什麼是 Docker？
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 什麼是 Docker？
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 06dd5199b8dbc42ce3e9ae35bc5c3673d01cb4de
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106797"
---
# <a name="what-is-docker"></a>什麼是 Docker？

[Docker](https://www.docker.com/) 是[開放原始碼專案](https://github.com/docker/docker)，將應用程式自動化部署為可攜式且可自足的容器，在雲端或內部部署上執行。 Docker 也是升級及發展這項技術的[公司](https://www.docker.com/)。 Docker 與雲端、Linux 和 Windows 廠商共同作業，包括 Microsoft。

![](./media/image2.png)

**圖 2-2**。 Docker 將容器部署在混合式雲端的所有圖層

Docker 映像容器以原生方式在 Linux 及 Windows 上執行。 Windows 映像只在 Windows 主機上執行，Linux 映像只在 Linux 主機上執行。 主機是伺服器或 VM。

您可以在 Windows、Linux 或 macOS 上開發。 開發電腦執行的 Docker 主機是 Docker 映像部署所在，包括應用程式及其相依性。 在 Linux 或 macOS，您要使用 Linux 架構的 Docker 主機，只能建立用於 Linux 容器的映像。(您可以在 macOS 上編輯程式碼或執行 Docker CLI，但截至撰稿時，容器仍不能直接在 macOS 上執行。)您可以在 Windows 上建立適用於 Linux 或 Windows 容器的映像。

在 Windows 或 macOS 上，[Docker Community Edition (CE)](https://www.docker.com/community-edition) 裝載部署環境中的容器，並提供其他開發人員工具。 建置、出貨及執行大型業務關鍵應用程式的 IT 小組使用 [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition)。 ~這兩項產品都會安裝必要的 VM (Docker 主機) 以裝載容器。~ 

[Windows 容器](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview)使用兩種執行階段：

-   Windows Server 容器透過程序和命名空間隔離技術，提供應用程式隔離。 與 Windows Server 容器共用核心的對象為容器主機以及在此主機上執行的所有容器。

-   Hyper-V 容器可在 Windows Server 容器提供的隔離上展開，方法是在高度最佳化的虛擬機器中執行每個容器。 在此組態中，容器主機的核心不會與 Hyper-V 容器共用，以提供更好的隔離。 Hyper-V 容器允許未受信任的和「惡意的多租用戶」應用程式在相同的主機上執行。 Hyper-V 容器的啟動時間和密度，效率略遜於 Windows Server 容器。

這些容器映像的建立及運作方式都相同。 只容器建立方式有異。 如需詳細資料，請參閱 [Hyper-V 容器](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview)。

## <a name="comparing-docker-containers-with-virtual-machines"></a>比較 Docker 容器與虛擬機器

圖 2-3 比較 VM 和 Docker 容器。

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **虛擬機器**                                                                                                                                                                  **Docker 容器**
                                                                                                                                                                                        
  ![](./media/image3.png)                                                                                                                                ![](./media/image4.png)
                                                                                                                                                                                        
  虛擬機器包含應用程式、必要的程式庫或二進位檔，以及完整的客體作業系統。 完整的虛擬化比容器化需要更多資源。 容器包括應用程式及其所有相依性。 不過，容器會與其他容器共用作業系統核心。 容器在主機作業系統上當作使用者空間的隔離處理序執行。 Hyper-V 容器除外，因為每個容器都是在每個容器的特殊虛擬機器內部執行。
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**圖 2-3**。 傳統虛擬機器與 Docker 容器的比較

因為容器只需要很少的資源 (例如，它們不需要完整的作業系統)，所以可快速輕易地部署。 低資源使用率造就更高的密度。 您可以在相同的硬體單元上執行更多服務，並降低成本。

在相同的核心上執行，隔離會比 VM 所提供的少。

映像的主要目標是跨不同的部署建立相同的環境 (相依性)。 這表示您可以在自己的電腦上對它進行偵錯，再將它部署到另一部電腦，保證有相同的環境。

容器映像是一種封裝應用程式或服務，再以可靠且可重現的方式來部署它的方法。 您可以這麼認為：Docker 不只是一項技術，更是哲學與過程。

Docker 開發人員不會說：「電腦上行得通，為什麼生產環境行不通？」 他們會說：「Docker 上可以執行。」 Docker 封裝的應用程式可以在任何受支援的 Docker 環境中執行。 Docker 封裝的應用程式在所有部署目標 (開發、品管、暫存、生產環境) 中都能以一致的方式執行。

>[!div class="step-by-step"]
[上一頁](index.md)
[下一頁](docker-terminology.md)

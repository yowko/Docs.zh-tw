---
title: 什麼是 Docker？
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: 2dfff13f00d4ea0e57161c21d7773eead41c28ee
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105381"
---
# <a name="what-is-docker"></a>什麼是 Docker？

[Docker](https://www.docker.com/)是[開放原始碼專案](https://github.com/docker/docker)自動化應用程式的部署，做為可攜式且足可雲端或內部部署中執行的容器 (請參閱圖 1-2）。 Docker 也有[公司](https://www.docker.com/)的升級，並開發這項技術，在與雲端，Linux 和 Windows 廠商，包括 Microsoft 的共同作業工作。

![](./media/image2.png)

圖 1-2: Docker 部署混合式雲端的所有層級的容器

Docker 映像容器可以原生 Linux 及 Windows 上執行。 不過，Windows 映像可以只在 Windows 主機上執行，而且 Linux 映像可以只在 Linux 主機，這表示主機伺服器或 VM 上執行。

開發人員可以在 Windows、 Linux 或 macOS 使用開發環境。 在開發電腦上開發人員會執行的 docker 映像部署，包括應用程式和其相依性的 Docker 主機。 開發人員在 Linux 上或在 Mac 上使用 Linux 為基礎的 Docker 主機，而且可以建立 Linux 容器的影像。 (在 Mac 上工作的開發人員可以編輯的程式碼，或執行 Docker 命令列介面\[CLI\]從 macOS，但是，撰寫本文時，容器無法執行直接在 macOS。)在 Windows 合作的開發人員可以 for Linux 或 Windows 容器建立映像。

若要裝載在開發環境中的容器，並提供額外的開發人員工具，Docker 隨附[Docker Community Edition (CE)](https://www.docker.com/community-edition) Windows 或 macOS。 這些產品會安裝必要的 VM （Docker 主機） 來裝載容器。 Docker 也會出現[Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition)，這針對企業開發所設計，並且由 IT 團隊建置、 出貨，而且在生產中執行大型的業務關鍵應用程式。

若要執行[Windows 容器](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview)，有兩種類型的執行階段：

-   **Windows Server 容器** 此執行階段提供透過程序和命名空間隔離技術的應用程式隔離。 與 Windows Server 容器共用核心的對象為容器主機以及在此主機上執行的所有容器。

-   **HYPER-V 容器** 這會展開，Windows Server 容器提供高度最佳化的 VM 中執行每個容器的隔離。 在此組態中，容器主機的核心不會與 Hyper-V 容器共用，以提供更好的隔離。

這些容器的映像建立相同的方式和功能相同。 不同之處在於從映像建立容器時，執行 HYPER-V 容器需要額外的參數。 如需詳細資料，請參閱 [Hyper-V 容器](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview)。

## <a name="comparing-docker-containers-with-vms"></a>比較與 Vm 的 Docker 容器

圖 1-3 顯示比較 Vm 和 Docker 容器。

因為容器需要少很多的資源 （例如，它們不需要在完整作業系統），它們是容易部署而且快速啟動。 這可讓您擁有更高的密度，這表示，您可以執行更多服務在相同的硬體單元，藉此降低成本。

在相同的核心上執行的副作用，您可以達到比 Vm 更少隔離。

映像的主要目標是跨不同的部署建立相同的環境 (相依性)。 這表示您可以在自己的電腦上對它進行偵錯，再將它部署到另一部電腦，保證有相同的環境。

容器映像是封裝的應用程式或服務，並將它部署可靠且可重現的方式的方法。 在這一方面，Docker 不是一種技術，它也是基本概念和程序。

當使用 Docker 時，您將無法聽到說出的開發人員、"﹐ 我的電腦，為何不在生產環境中？ 」 他們可以只需說，"執行 docker"因為封裝的 Docker 應用程式可以執行任何支援的 Docker 環境，而且它會執行它要設定所有的部署目的地 （開發、 品管暫存、 生產等。） 的方式。

![](./media/image3.png)

圖 1-3： 的傳統 Vm 至 Docker 容器的比較


>[!div class="step-by-step"]
[上一頁](index.md)
[下一頁](docker-terminology.md)

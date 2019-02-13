---
title: 什麼是 Docker？
description: 取得深入了解 Docker，簡單的比喻可以幫助您。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: c8300c964dfce0cc8e39478cc10ed7589dbca2c9
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56218550"
---
# <a name="what-is-docker"></a>什麼是 Docker？

[Docker](https://www.docker.com/)已[開放原始碼專案](https://github.com/docker/docker)自動化應用程式部署為可攜式且自給自足的容器，可以執行在雲端或內部部署 (請參閱 圖 1-2）。 Docker 也是[公司](https://www.docker.com/)升級及開發這項技術，與雲端、 Linux 和 Windows 廠商，包括 Microsoft 的合作。

![](./media/image2.png)

圖 1-2:Docker 將容器部署在混合式雲端的所有圖層

Docker 映像容器可以原生方式在 Linux 及 Windows 上執行。 不過，Windows 映像可以只在 Windows 主機上執行，而且只在 Linux 主機，這表示主機伺服器或 VM 上可以執行的 Linux 映像。

開發人員可以使用 Windows、Linux 或 macOS 上的開發環境。 開發電腦上，開發人員會執行的 docker 映像部署，包括應用程式和其相依性的 Docker 主機。 在 Linux 或 Mac 上工作的開發人員會使用 Linux 型的 Docker 主機，他們只能建立適用於 Linux 容器的映像。 (在 Mac 上工作的開發人員可以編輯程式碼，或執行 Docker 命令列介面\[CLI\]從 macOS，但，撰寫本文時，容器無法執行直接在 macOS 上。)在 Windows 上工作的開發人員可以建立適用於 Linux 或 Windows 容器的映像。

為了在開發環境中裝載容器並且提供其他開發人員工具，Docker 提供適用於 Windows 或 macOS 的 [Docker Community Edition (CE)](https://www.docker.com/community-edition)。 這些產品都會安裝必要的 VM (Docker 主機) 以裝載容器。 Docker 也提供 [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition)，這是專為企業開發所設計的，由在生產環境中建置、交付及執行大型商務關鍵性應用程式的 IT 小組來使用。

若要執行 [Windows 容器](/virtualization/windowscontainers/about/)，有兩種執行階段：

-   **Windows Server 容器** 此執行階段會提供透過程序和命名空間隔離技術的應用程式隔離。 與 Windows Server 容器共用核心的對象為容器主機以及在此主機上執行的所有容器。

-   **HYPER-V 容器** 這在高度最佳化的 VM 中執行每個容器，Windows Server 容器所提供的隔離上展開。 在此組態中，容器主機的核心不會與 Hyper-V 容器共用，以提供更好的隔離。

這些容器的映像會建立相同的方式和功能相同。 不同之處在於如何從映像建立容器時，執行 HYPER-V 容器，需要額外的參數。 如需詳細資料，請參閱 [Hyper-V 容器](/virtualization/windowscontainers/about/)。

## <a name="comparing-docker-containers-with-vms"></a>比較使用 Vm 的 Docker 容器

圖 1-3 顯示比較 Vm 和 Docker 容器。

因為容器只需要很少的資源 （例如，他們不需要完整的作業系統），可輕鬆地部署和快速啟動。 這項功能可讓您擁有更高的密度，這表示您可以在相同的硬體單元，藉此降低成本上執行更多服務。

在相同核心上執行的副作用，您可以達到比 Vm 更少隔離。

映像的主要目標是跨不同的部署建立相同的環境 (相依性)。 這表示您可以在自己的電腦上對它進行偵錯，再將它部署到另一部電腦，保證有相同的環境。

容器映像會用來在封裝的應用程式或服務，並將其部署可靠且可重現的方式。 在這方面，Docker 不只一種技術，也更是哲學與處理程序。

使用 Docker 時，您將無法聽到開發人員說，「 它能用在我的電腦上為何不在生產環境中？ 」 它們可以直接說 「 Docker 上可以執行，「 因為任何支援的 Docker 環境中，您可以執行封裝的 Docker 應用程式，而且它會執行其所有的部署目的地 （開發、 品管、 暫存、 生產等。） 在目標的方式。

![](./media/image3.png)

圖 1-3:傳統 Vm 的 Docker 容器的比較

>[!div class="step-by-step"]
>[上一頁](index.md)
>[下一頁](docker-terminology.md)

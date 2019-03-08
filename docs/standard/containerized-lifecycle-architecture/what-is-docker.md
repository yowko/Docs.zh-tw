---
title: 什麼是 Docker？
description: 取得深入了解 Docker，簡單的比喻可以幫助您。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: fbb91466a86c7082e89d0ac4a3673ad83ab39b88
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57680122"
---
# <a name="what-is-docker"></a>什麼是 Docker？

[Docker](https://www.docker.com/) 是[開放原始碼專案](https://github.com/docker/docker)，將應用程式自動化部署為可攜式且可自足的容器，在雲端或內部部署上執行。 Docker 也是一家升級及發展這項技術的[公司](https://www.docker.com/)，並且與雲端、Linux 和 Windows 廠商 (包括 Microsoft) 合作。

![Docker 容器可以在任何位置執行，例如客戶資料中心的內部部署、外部服務提供者或雲端 (在 Azure 上)。](./media/image2.png)

**圖 1-2**。 Docker 將容器部署在混合式雲端的所有圖層

Docker 映像容器可以原生方式在 Linux 及 Windows 上執行。 不過，Windows 映像只能在 Windows 主機上執行，而 Linux 映像可以在 Linux 主機和 Windows 主機上執行 (目前是使用 Hyper-V Linux VM)，其中主機是指伺服器或 VM。

開發人員可以使用 Windows、Linux 或 macOS 上的開發環境。 在開發電腦上，開發人員執行的 Docker 主機是 Docker 映像部署所在，包括應用程式及其相依性。 開發人員在 Linux 或 Mac 上使用的是以 Linux 為基礎的 Docker 主機，而且只可以建立適用於 Linux 容器映像。 （在 Mac 上工作的開發人員可以編輯程式碼或執行 Docker 命令列介面 (CLI) 從 macOS，但不撰寫本文時，直接在 macOS 上執行容器）。在 Windows 上工作的開發人員可以建立適用於 Linux 或 Windows 容器的映像。

為了在開發環境中裝載容器並且提供其他開發人員工具，Docker 提供適用於 Windows 或 macOS 的 [Docker Community Edition (CE)](https://www.docker.com/community-edition)。 這些產品都會安裝必要的 VM (Docker 主機) 以裝載容器。 Docker 也提供 [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition)，這是專為企業開發所設計的，由在生產環境中建置、交付及執行大型商務關鍵性應用程式的 IT 小組來使用。

若要執行 [Windows 容器](/virtualization/windowscontainers/about/)，有兩種執行階段：

- **Windows Server 容器**提供透過程序和命名空間隔離技術的應用程式隔離。 與 Windows Server 容器共用核心的對象為容器主機以及在此主機上執行的所有容器。

- **HYPER-V 容器**擴充 Windows Server 容器所提供的高度最佳化的虛擬機器中執行每個容器的隔離能力。 在此組態中，容器主機的核心不會與 Hyper-V 容器共用，以提供更好的隔離。

這些容器的映像建立，而且一樣運作方式。 不同之處在於如何從映像建立容器時，執行 HYPER-V 容器，需要額外的參數。 如需詳細資料，請參閱 [Hyper-V 容器](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container)。

## <a name="comparing-docker-containers-with-virtual-machines"></a>比較 Docker 容器與虛擬機器

圖 1-3 顯示比較 Vm 和 Docker 容器。

![針對 VM，在主機伺服器中有三個基礎層，從下到上分別是：基礎結構、主機作業系統和 Hypervisor，每部 VM 在頂端都具有各自的作業系統和所有必要的程式庫。 相反地，如 Docker 主機伺服器只有在基礎結構和 OS，並在上面的是，容器引擎，可會保留容器隔離，但共用的基底的作業系統服務。](./media/image3.png)

**圖 1-3**。 傳統虛擬機器與 Docker 容器的比較

因為容器只需要很少的資源 (例如，它們不需要完整的作業系統)，所以容易部署且會快速啟動。 這可讓您擁有更高的密度，這表示可讓您在相同硬體單位上執行更多服務，藉此降低成本。

在相同核心上執行的副作用是隔離程度比 VM 低。

映像的主要目標是確保相同的環境 （相依性），跨不同的部署。 這表示您可以用來進行偵錯您的電腦上，然後再將它部署到另一部電腦，保證相同的環境。

容器映像是一種封裝應用程式或服務，再以可靠且可重現的方式來部署它的方法。 您可以這麼認為：Docker 不只是一項技術，更是哲學與過程。

使用 Docker 時，您不會聽到開發人員說：「機器上行得通，為什麼生產環境行不通？」 他們可以只是說: 「 Docker 上可以執行 「、 因為封裝的 Docker 應用程式可執行任何支援的 Docker 環境中，並在所有部署目標上執行它所要的方式 (例如開發、 品管、 預備及生產)。

## <a name="a-simple-analogy"></a>簡單的比喻

也許簡單的比喻可以協助您掌握 Docker 的核心概念。

讓我們暫時回到 1950 年。 沒有任何的文書處理器，而且在各處使用影印機 （那種）。

假設您負責根據需求來快速發送大批信件，並使用信紙和信封，將信件實際投遞到每個客戶的地址 (當時並沒有電子郵件)。

慢慢地，您了解到這些信件的內容是大量段落的組合，只是根據信件目的從中挑選和編排需要的段落，因此您設計一個系統，可以快速地發送信件來提高效率。

系統很簡單：

1. 您開始準備一疊透明紙張，每一張紙都包含一個段落。

2. 若要發送一批信件，您就挑選具有所需段落的紙張，然後將其堆疊並且排列整齊，讓它們整潔易讀。

3. 最後，您將這個組合放入影印機中，然後按下開始以產生所需數量的信件。

因此，工作精簡了，這就是 Docker 的核心概念。

Docker 中的每一層都是在執行命令 (例如安裝程式) 之後，檔案系統上所發生的變更結果集。

因此，當您在複製層之後「查看」檔案系統時，會看到檔案整體，包含安裝程式的層。

您可以將映像當作是準備要在「電腦」(已安裝作業系統) 中安裝的輔助唯讀硬碟。

同樣地，您可以將容器當作是已安裝映像硬碟的「電腦」。 容器，就像電腦一樣，可以開啟或關閉。

>[!div class="step-by-step"]
>[上一頁](index.md)
>[下一頁](docker-terminology.md)

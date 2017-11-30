---
title: "在生產環境中執行組成和 microservices 為基礎的應用程式"
description: "Microsoft 平台和工具與 Docker 容器化應用程式生命週期"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: e7a2788098aa731699cbb201c7177e7578907673
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a>在生產環境中執行組成和 microservices 為基礎的應用程式

由多個 microservices 組成的應用程式需要部署到 orchestrator 叢集，以簡化部署的複雜性，並將其從 IT 的觀點可行。 與 orchestrator 的叢集，不會很難部署和向外延展複雜 microservices 應用程式。

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a>簡介 orchestrators、 排程器，以及容器叢集

稍早在本電子書，我們引進*叢集*和*排程器*，討論的軟體架構和開發的一部分。 Docker 叢集的範例為 Docker Swarm 和 Mesosphere Datacenter 作業系統 (DC/OS)。 這兩種可以執行 Microsoft Azure 容器服務所提供的基礎結構的一部分。

當應用程式會向外延展跨多個主機系統時，會變成吸引人能夠管理每個主機系統和提取出基礎平台的複雜性。 這就是精確 orchestrators 和排程器提供的內容。 讓我們看這裡簡短查看：

-   **排程器*** *「 排程 」 是指系統管理員可以載入到建立如何執行特定的容器主機系統上的服務檔案的能力。 通常會以稱為排程啟動 Docker 叢集中的容器。 雖然排程的載入服務定義中的較通用的意義上，特定的動作是指排程器負責將連結到主機的 init 系統管理服務中任何所需的容量。

叢集的排程器有多個目標： 有效率地使用叢集的資源，請使用使用者提供位置條件約束，排程應用程式快速不讓它們留在暫止狀態，需要某種程度的"公平性，「 正在強固的錯誤，並一律可供使用。

-   **協調流程*** *平台擴充至的主機叢集上部署的複雜、 multicontainer 工作負載的生命週期管理功能。 藉由抽象化主機基礎結構，協調流程工具可讓使用者將整個叢集視為單一部署目標。

協調流程程序包含工具和可以自動化初始放置或部署每個容器; 從應用程式管理的各個層面的平台將容器移到不同的主機，根據其主機的健全狀況或效能;版本控制和輪流更新，以及健全狀況監視縮放比例和容錯移轉，支援的函式等等。

協調流程是廣泛的詞彙，意指容器排程、 叢集管理，以及可能在佈建其他主機。

Orchestrators 和排程器所提供的功能是以開發並從從頭開始建立非常複雜，因此您通常會想要讓廠商所提供的協調流程解決方案。


>[!div class="step-by-step"]
[上一個](index.md) [下一步] (管理-生產-docker-environments.md)

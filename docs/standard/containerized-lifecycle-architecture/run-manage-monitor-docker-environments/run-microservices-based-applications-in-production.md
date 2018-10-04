---
title: 在生產環境中執行撰寫和以微服務為基礎的應用程式
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 18e6cb1fb5f496b66c89cb8e009a67894b8a76ad
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580283"
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a>在生產環境中執行撰寫和以微服務為基礎的應用程式

由多個微服務組成的應用程式需要部署到 orchestrator 叢集，以簡化部署的複雜性，並使其從 IT 觀點來看變為可用。 協調器叢集，不會很難部署和向外延展的複雜的微服務應用程式。

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a>Orchestrator、 排程器及容器叢集簡介

稍早在本電子書，我們引進了*叢集*並*排程器*，討論的軟體架構設計和開發的一部分。 Docker Swarm 和 Mesosphere Datacenter Operating System (DC/OS)，就會是 Docker 叢集的範例。 這兩種都可以執行 Microsoft Azure Container Service 所提供的基礎結構的一部分。

當應用程式會向外延展跨多個主機系統時，能夠管理每個主機系統，並抽離基礎平台的複雜性會成為吸引人。 這就是精確地協調器和排程器提供的內容。 以下讓我們簡短看：

- **排程器**： 「 排程 」 指的是系統管理員可以載入到建立如何執行特定的容器主機系統上的服務檔案的能力。 啟動 Docker 叢集中的容器，通常稱為排程。 雖然排程是指特定的動作，載入服務定義中，更一般的意義而言，排程器負責連結到主機的 init 系統，來管理服務中任何所需的容量。

   叢集排程器有多個目標： 有效率地使用叢集的資源，請使用使用者提供的放置條件約束，排程應用程式快速不將它們保留在擱置狀態，需要某種程度的 「 公平起見，「 正在強固的錯誤，以及可使用。

- **協調流程**。 平台擴充為複雜、 多容器的主機叢集上部署的工作負載的生命週期管理功能。 藉由抽象化主機基礎結構，協調流程工具可讓使用者將在整個叢集中視為單一部署目標。

   協調流程程序包含工具和可以自動化初始放置或每個容器; 部署的應用程式管理的各個層面的平台將容器移至不同的主控件，取決於其主機的健康狀態或效能;版本控制和輪流更新，以及健全狀況監視支援縮放比例和容錯移轉，函式更多選擇。

   協調流程是一個廣義的詞彙，指的是容器排程、 叢集管理，以及可能在佈建其他主機。

協調器和排程器所提供的功能會很複雜，開發並從頭建立，並因此您通常會想要讓廠商所提供的協調流程解決方案的使用。


>[!div class="step-by-step"]
[上一頁](index.md)
[下一頁](manage-production-docker-environments.md)

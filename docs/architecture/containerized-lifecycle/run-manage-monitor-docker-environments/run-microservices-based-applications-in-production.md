---
title: 在生產環境中執行已撰寫和以微服務為基礎的應用程式
description: 了解在生產環境中執行容器型應用程式的主要元件
ms.date: 02/15/2019
ms.openlocfilehash: 69df3d39a00b91cbe59c96e5fcab841a60943bcc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68672915"
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a>在生產環境中執行已撰寫和以微服務為基礎的應用程式

由多個微服務組成的應用程式確實需要部署至協調器叢集，以簡化部署的複雜性，並使其從 IT 觀點看來成為可行。 如果沒有協調器叢集，將難以部署及相應放大複雜的微服務應用程式。

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a>協調器、排程器及容器叢集簡介

本電子書中稍早介紹了「叢集」  和「排程器」  ，作為軟體架構設計和開發討論的一部分。 Kubernetes 和 Service Fabric 是 Docker 叢集的範例。 這兩個協調器都可以作為 Microsoft Azure Kubernetes Service 所提供基礎結構的一部分執行。

當應用程式跨多個主機系統相應放大時，管理每個主機系統和抽離基礎平台複雜性的能力會具有吸引力。 這正是協調器和排程器可提供的功能。 讓我們看看簡要介紹：

- **排程器**： 「排程」是指系統管理員將服務檔案載入主機系統的能力，該主機系統會確定如何執行特定容器。 在 Docker 叢集中啟動容器通常稱為排程。 雖然排程意指載入服務定義的特定動作，但以更一般的意義而言，排程器負責連結到主機的 init 系統，以所需的容量來管理服務。

   叢集排程器有多個目標：有效率地使用叢集資源、使用使用者提供的放置條件約束、快速排程應用程式以使其不處於擱置狀態、具有某種程度的「公平性」、較能承受錯誤，以及一律可用。

- **協調器**。 平台將生命週期管理功能擴充至部署在主機叢集上複雜的多容器工作負載。 藉由將主機基礎結構抽象化，協調器工具可為使用者提供將整個叢集視為單一部署目標的方法。

   協調流程程序涉及可從每個容器初始放置或部署中自動化應用程式管理之各個層面自動化的工具和平台；根據主機的健康狀態或效能，將容器移至不同的主機；版本控制和復原更新以及支援調整和容錯移轉的健康狀態監視功能；以及其他更多功能。

   協調流程是一個廣義的詞彙，意指容器排程、叢集管理及可能的額外主機佈建。

協調器和排程器所提供的功能很難從頭開發與建立，因此您通常希望使用廠商提供的協調流程解決方案。

>[!div class="step-by-step"]
>[上一頁](index.md)
>[下一頁](manage-production-docker-environments.md)

---
title: SOA 應用程式
description: 請記住容器也可以是 SOA 應用程式的實用的部署選項。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 4fd39e075c5730cf7fddb0138cdb5267a914c91f
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221260"
---
# <a name="soa-applications"></a>SOA 應用程式

SOA 已過度使用的詞彙和不同的意義很多不同的人。 但該結構的架構，藉由將它分解 （通常為 HTTP 服務） 可以分類在不同類型的多個服務中的應用程式的最小值和作為共同點，SOA，或服務導向、 平均值，例如子系統或者，您也可以在其他情況下，做為層。

現在，您可以部署這些服務做為 Docker 容器，以解決部署相關的問題，因為所有相依性都包含在容器映像。 但是，當您需要向外延展 soa 都極為，您可能會遇到挑戰，如果您要部署根據的單一執行個體。 這是 Docker 叢集軟體或 orchestrator 將會幫助您。 我們將探討這一節中的更詳細地探討微服務方法時。

在一天結束時，容器叢集解決方案都適用於這兩種傳統的 SOA 架構，或在更進階的微服務架構，在其中每個微服務擁有其資料模型。 而且，多虧有多個資料庫，您也可以向外延展的資料層，而不是使用由 SOA 服務所共用的單體式資料庫。 不過，討論將資料分割是純粹的相關架構和設計。

>[!div class="step-by-step"]
>[上一頁](state-and-data-in-docker-applications.md)
>[下一頁](orchestrate-high-scalability-availability.md)
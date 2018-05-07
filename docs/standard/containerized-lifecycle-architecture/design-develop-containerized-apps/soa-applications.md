---
title: SOA 應用程式
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 37313c4eb437b6b7a362456a7d1ee3b3aecb6020
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="soa-applications"></a>SOA 應用程式

SOA 已過度的詞彙，使用許多不同的項目對不同的人。 但最小值及共同分母、 SOA，或服務方向、 平均數該結構的應用程式將它分解 （通常為 HTTP 服務） 可以在不同的類型分類的多個服務的架構，例如子系統或者，在其他情況下，做為層。

現在，您可以部署這些服務做為 Docker 容器的可解決與部署相關的問題，因為所有的相依性，但包括容器映像。 不過，當您需要向外延展 SOAs，您可能會遇到的挑戰如果您要部署根據的單一執行個體。 這是 Docker，叢集軟體或 orchestrator 將會幫助您。 我們會探討這在下一節中更詳細地介紹 microservices 方法。

在一天結束時，容器叢集解決方案適合用於這兩種傳統 SOA 的架構，或用於更進階的 microservices 架構中的每個微服務擁有其資料模型。 此外，由於多個資料庫，您也可以向外延展資料層，而不是使用整合型 SOA 服務所共用的資料庫。 不過，將資料分割的相關討論即將純粹架構和設計。


>[!div class="step-by-step"]
[上一個] (state-and-data-in-docker-applications.md) [下一步] (協調-高的延展性-availability.md)

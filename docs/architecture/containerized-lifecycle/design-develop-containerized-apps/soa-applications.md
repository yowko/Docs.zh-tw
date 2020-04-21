---
title: SOA 應用程式
description: 請記住，容器也是 SOA 應用程式的實用部署選項。
ms.date: 02/15/2019
ms.openlocfilehash: f8619cb50a7d90b911db9ff2c8ef37c3c5fde210
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738391"
---
# <a name="service-oriented-applications"></a>服務導向應用程式

服務導向架構 (SOA) 這個詞彙的使用有點過於氾濫，因此對不同人有不同的意義。 但其中關於 SOA 的共同點是：您將應用程式分解為若干服務 (通常是 HTTP 服務) 來建構應用程式的架構，而這些服務又歸為不同類型，例如子系統或層 (在某些情況下)。

現在，您可以將這些服務部署為 Docker 容器以解決部署相關問題，因為所有相依性都包含在容器映像中。 但是，如果您是根據單一執行個體進行部署，當您需要擴充 SOA 時可能會遇到困難。 您可以使用 Docker 叢集軟體或協調器來解決這個挑戰。 下一節探討微服務方法時，我們會詳細說明協調器。

Docker 容器十分適用 (但不是必要) 於傳統服務導向架構和更進階的微服務架構。

綜觀各方面條件來看，針對傳統 SOA 架構以及更進階的微服務架構 (其中每個微服務擁有其資料模型) 均適用容器叢集解決方案。 得益於多個資料庫,您還可以橫向擴展數據層,而不是使用 SOA 服務共用的單片資料庫。 不過，我們只會單純就架構和設計面來探討資料分割。

>[!div class="step-by-step"]
>[前一個](state-and-data-in-docker-applications.md)
>[下一個](orchestrate-high-scalability-availability.md)

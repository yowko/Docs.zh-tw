---
title: SOA 應用程式
description: 請記住，容器也是 SOA 應用程式的實用部署選項。
ms.date: 08/06/2020
ms.openlocfilehash: 5cc616eaf3be31ae704320df6ec54deed9529989
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915256"
---
# <a name="service-oriented-applications"></a>服務導向應用程式

服務導向架構 (SOA) 這個詞彙的使用有點過於氾濫，因此對不同人有不同的意義。 但其中關於 SOA 的共同點是：您將應用程式分解為若干服務 (通常是 HTTP 服務) 來建構應用程式的架構，而這些服務又歸為不同類型，例如子系統或層 (在某些情況下)。

現在，您可以將這些服務部署為 Docker 容器以解決部署相關問題，因為所有相依性都包含在容器映像中。 但是，如果您是根據單一執行個體進行部署，當您需要擴充 SOA 時可能會遇到困難。 您可以使用 Docker 叢集軟體或協調器來解決這個挑戰。 當您探索微服務方法時，您將會在下一節中更詳細地瞭解協調器。

Docker 容器十分適用 (但不是必要) 於傳統服務導向架構和更進階的微服務架構。

綜觀各方面條件來看，針對傳統 SOA 架構以及更進階的微服務架構 (其中每個微服務擁有其資料模型) 均適用容器叢集解決方案。 由於有多個資料庫，您也可以將資料層向外延展，而不是使用 SOA 服務所共用的單一資料庫。 不過，我們只會單純就架構和設計面來探討資料分割。

>[!div class="step-by-step"]
>[上一個](state-and-data-in-docker-applications.md) 
>[下一步](orchestrate-high-scalability-availability.md)

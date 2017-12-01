---
title: "索引鍵的心得"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |索引鍵的心得"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: b557d0b641bfe95c025cadb13f82c3f8927f4bc8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="key-takeaways"></a>索引鍵的心得

為摘要和重要心得下, 面是本指南從最重要的結論。

**使用容器的優點。** 容器基礎的解決方案提供節省成本的重要優點，因為容器是因缺乏實際執行環境中的相依性的部署問題的解決方案。 容器會大幅改善 DevOps 與實際執行的作業。

**容器會普遍。** Docker 容器也變得既定的標準容器產業，支援 Windows 和 Linux 的生態系統中最重要的供應商。 這包括 Microsoft、 Amazon AWS、 Google、 和 IBM。 在不久的將來，Docker 可能會在雲端和內部部署資料中心廣泛運用。

**做為一個單位的部署容器。** Docker 容器會變成標準的任何伺服器端應用程式或服務的部署單位。

**Microservices。** Microservices 架構成為分散式和大型或複雜關鍵任務應用程式的基礎多個獨立的子系統獨立服務的形式慣用的方法。 在微服務基礎架構中，服務可能是開發、 測試、 版本設定，部署，以及獨立; 擴充的集合建置的應用程式這可包括任何相關的自主資料庫。

**網域導向設計和 SOA。** 從服務導向架構 (SOA) 和網域導向設計 (DDD) 衍生 microservices 架構模式。 當您設計和開發環境與發展成形特定網域的商務規則的 microservices 時，務必考慮帳戶 DDD 方法和模式。

**Microservices 挑戰。** Microservices 提供許多強大的功能，例如獨立部署、 強式子系統界限和技術多樣化。 不過，它們也會引發許多新的挑戰，分散式應用程式開發相關，例如分散和獨立的資料模型、 彈性和之間的通訊 microservices、 最終一致性，操作的複雜性而產生的彙總來自多個 microservices 的記錄和監視資訊。 含有這些層面導入較高層級的複雜性較傳統的整合應用程式。 如此一來，只有特定案例適用的微服務為基礎的應用程式。 這些包括多個發展子系統; 大型且複雜的應用程式在這些情況下，值得投資在更複雜的軟體架構中，因為它會提供更長期的靈活度和維護應用程式。

**任何應用程式的容器。** 容器 microservices，方便，但不排除它們。 容器也可以搭配整合的應用程式，包括傳統的.NET Framework 為基礎，透過 Windows 容器的現代化的舊版應用程式。 使用 Docker，例如解決部署到實際執行的許多問題及提供先進的開發和測試環境的優點適用於許多不同類型的應用程式。

**IDE 與 CLI。** 與 Microsoft 工具，您可以開發容器化的.NET 應用程式使用您慣用的方法。 您可以使用 Docker CLI 和 Visual Studio 程式碼開發與 CLI 和編輯器為基礎的環境。 或者，您可以對 Docker，使用 IDE 的方法與 Visual Studio 和它的獨特功能，例如，像能夠偵錯多個容器應用程式。

**具有恢復功能雲端應用程式。** 在雲端為基礎的系統和分散式的系統一般情況下，有一定是部分失敗的風險。 由於用戶端和服務是不同的處理序 （容器），服務可能無法在用戶端的要求能夠及時回應。 例如，服務可能會向部分失敗，或進行維護;服務可能是多載，而且速度極為緩慢到回應要求。或者，它可能只是無法存取一小段時間因為網路問題。 因此，以雲端為基礎的應用程式必須不怕失敗，而且已有一種策略來回應這些失敗。 這些策略可以包含的重試原則 （重新傳送訊息或重試要求），以避免指數實作斷路器模式載入的重複要求。 基本上，以雲端為基礎的應用程式必須有彈性的機制，可能是自訂的或雲端基礎結構，例如從 orchestrators 或服務匯流排的高階架構為基礎。

**安全性。** 容器和 microservices 我們現代化世界可以公開新的弱點。 根據基本的應用程式的安全性驗證和授權;實作這些存在多個方式。 不過，容器的安全性包含導致原本就是更安全的應用程式的其他重要元件。 問題通常也需要認證、 語彙基元、 密碼及其他類型的機密資訊，建立更安全的應用程式的關鍵項目擁有安全的方式，與其他應用程式和系統通訊的 — 通常指的是應用程式密碼。 安全的解決方案必須遵循安全性最佳作法，例如加密傳輸; 中的機密資料加密在靜止; 的密碼並避免無意間洩漏時最終的應用程式使用的密碼。 這些密碼必須儲存並保持安全的地方。 為了協助提高安全性，您可以充分利用您所選擇的 orchestrator 基礎結構，或 Azure 金鑰保存庫，以及提供應用程式程式碼以使用它的方式類似的雲端基礎結構。

**Orchestrators。** 容器基礎 orchestrators 像 Azure 容器服務 （Kubernetes、 Mesos DC/OS 和 Docker Swarm） 和 Azure Service Fabric 中提供的項目是不可或缺，針對任何可實際執行的微服務為基礎的應用程式及任何多容器應用程式大幅增加複雜度、 延展性需求與常數的演進。 本指南已導入，orchestrators 並且在微服務及容器解決方案中的角色。 如果您的應用程式需要移動您朝複雜的容器化應用程式，您會發現它有助於找出的深入了解 orchestrators 其他資源

>[!div class="step-by-step"]
[上一個](secure-net-microservices-web-applications/azure-key-vault-protects-secrets.md)

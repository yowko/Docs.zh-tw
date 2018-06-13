---
title: 當 Service fabric 部署 Windows 容器
description: 現代化現有的.NET 應用程式與 Azure 雲端和 Windows 容器 |當 Service fabric 部署 Windows 容器
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: c41db8b37c883f9369a6b8d1f8bccbc0535f504c
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "33957908"
---
# <a name="when-to-deploy-windows-containers-to-service-fabric"></a>當 Service fabric 部署 Windows 容器

應用程式為基礎的 Windows 容器快速將需要使用移開更進一步 IaaS Vm 所傳來的平台。 這是自動化的延展性和高延展性，並取得帶來顯著的改善功能部署中，讓完整的管理經驗升級，版本控制、 復原、 和健全狀況監視。 您可以達成這些目標，與 orchestrator Azure Service Fabric，可在 Microsoft Azure 雲端，但也在內部，或甚至另一個雲端。

許多組織的提升，而且移位原因有兩個現有的整合應用程式容器：

-   成本大幅降低，可能是因為彙總及移除現有的硬體，或是從執行的應用程式在更高的密度。

-   開發和作業之間的一致部署合約。

遵循成本大幅降低了解，以及很可能所有組織都追趕該目標。 一致部署較難評估，但同樣為重要。 一致部署合約告知的開發人員可自行選擇使用它們，符合的技術，作業小組會取得一種方法來部署和管理應用程式。 本合約可不需要處理的許多不同的技術，複雜度的作業，或強制僅適用於某些技術的開發人員的麻煩。 基本上，每個應用程式容器化獨立的部署映像中。

某些組織會繼續種加 microservices （雲端原生應用程式），但其他許多組織會在此停止 （雲端最佳化應用程式）。 如所示圖 4-8，這些組織不會移動至 microservices 架構，因為它們可能不需要。 在任何情況下，就已取得，使用容器，再加上 Service Fabric 提供的完整管理經驗，包括部署、 升級的優點、 版本控制、 復原、 和健全狀況監視。

> ![拿起，然後移到 Service Fabric 應用程式](./media/image8.png)
>
> **圖 4 到 8。** 拿起，然後移到 Service Fabric 應用程式

Service Fabric 金鑰方法是以重複使用現有的程式碼和提起移位。 因此，您可以藉由使用 Windows 容器移轉目前的.NET Framework 應用程式，並將其部署 Service fabric。 將您更輕鬆地將種，最後，藉由新增新 microservices。

當比較其他 orchestrators Service Fabric，務必反白顯示 Service Fabric 這成熟在執行 windows 應用程式和服務。 Windows 服務和應用程式，包括年第 1 層，關鍵任務的產品，從 Microsoft Service Fabric 已經執行。 它是第一次的 orchestrator，來公開上市的 Windows 容器。 其他容器，例如 Kubernetes、 DC/OS，和 Docker Swarm，是成熟 linux，但較不成熟比服務網狀架構的 Windows 架構應用程式與 Windows 容器。

Service Fabric 的最終目標是減少使用 microservices 方法建置的應用程式的複雜性。 最後，您會想 microservices 特定類型的應用程式，以避免昂貴的重新設計。 您可以從小型專案開始和調整其規模需要時，服務已被取代，加入新的服務，發展客戶使用您的應用程式。 有許多即將讓大部分的開發人員更容易實行 microservices 解決其他問題。 如果您目前只提起，移位的應用程式使用 Windows 容器，但是您正考慮加入 microservices 未來根據容器，這是 Service Fabric 成問題。

>[!div class="step-by-step"]
[上一頁](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[下一頁](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)

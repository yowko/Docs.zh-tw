---
title: 將 Windows 容器部署到 Service Fabric 的時機
description: 將現有的.NET 應用程式使用 Azure 雲端和 Windows 容器現代化 |將 Windows 容器部署到 Service Fabric 的時機
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 01d76f325480c7cf09fef36b02589a602e3ee11e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129502"
---
# <a name="when-to-deploy-windows-containers-to-service-fabric"></a>將 Windows 容器部署到 Service Fabric 的時機

Windows 容器為基礎的應用程式快速必須使用走了更進一步地從 IaaS Vm 適用的平台。 這是自動化的增強的延展性和高延展性，並獲得明顯的改進，在部署中，完整的管理體驗中升級，版本控制、 復原、 和健全狀況監視。 如果要達成這些目標，即可使用 Azure Service Fabric 中，可在 Microsoft Azure 雲端，但也在內部，或甚至是其他雲端中的 orchestrator。

許多組織將現有單體式應用程式到容器的原因有二： 式

-   降低成本，可能是因為彙整和移除現有的硬體，或是從執行的應用程式在更高的密度。

-   開發與作業之間的一致性部署合約。

追求降低成本是可理解的而且可能所有組織都追尋此目標。 一致性部署較難以評估，但同樣重要。 一致性部署合約會說，開發人員可以自由選擇要使用的技術，營運小組取得單一的方式來部署和管理應用程式。 本 「 合約 」 可以減輕必須處理許多不同的技術複雜性的作業，或強制只能使用某些技術的開發人員的痛苦。 基本上，每個應用程式容器化的自封式的部署映像中。

某些組織會繼續現代化加微服務 （雲端原生應用程式），但許多其他組織也在此告一段落 （雲端最佳化應用程式）。 如所示的 圖 4-8，這些組織不會移動到微服務架構，因為它們可能不需要。 在任何情況下，它們已取得，使用容器，再加上 Service Fabric 提供的完整管理體驗，包括部署、 升級的優點、 版本控制、 復原、 和健全狀況監視。

> ![原形移轉到 Service Fabric 應用程式](./media/image8.png)
>
> **圖 4-8。** 原形移轉到 Service Fabric 應用程式

Service Fabric 的主要方法是重複使用現有的程式碼和撤銷並轉移。 因此，您可以藉由使用 Windows 容器移轉目前的.NET Framework 應用程式，並將其部署至 Service Fabric。 它會是您更輕鬆地進行現代化，最後，藉由新增新的微服務。

比較時 Service Fabric 與其他協調者，務必反白顯示 Service Fabric 是成熟，在執行以 Windows 為基礎的應用程式和服務。 以 Windows 為基礎的服務和應用程式，包括第 1 層的關鍵任務的產品，從 Microsoft 多年來已經執行 Service Fabric。 它是第一次的 orchestrator，來適用於 Windows 容器已正式運作。 Kubernetes、 DC/OS 和 Docker Swarm 等其他容器是在 Linux 中，但較不成熟的 Windows Service Fabric 應用程式和 Windows 容器比更進步。

Service Fabric 的終極目標是減少使用微服務方法建置應用程式的複雜性。 最後，您會想微服務的特定類型的應用程式，以避免昂貴的重新設計。 您可以從小規模開始、 需要時調整、 淘汰服務、 加入新的服務，及發展客戶使用您的應用程式。 有許多其他尚待解決為了讓微服務更易於為大部分開發人員的問題。 如果您目前只是將式應用程式與 Windows 容器，但您想要新增未來根據容器的微服務，這是 Service Fabric 甜蜜點。

>[!div class="step-by-step"]
>[上一頁](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
>[下一頁](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
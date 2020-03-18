---
title: 提升現有 .NET 應用並將其轉移到 Azure IaaS（雲基礎架構就緒）
description: 使用 Azure 雲和 Windows 容器對現有 .NET 應用程式進行現代化改造。
ms.date: 04/28/2018
ms.openlocfilehash: c7638a034dbb27baea1b097bdb66175bfb5a71f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "73089640"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a>提升現有 .NET 應用並將其轉移到 Azure IaaS（雲基礎架構就緒）

> 願景：作為第一步，為了降低本地投資和硬體和網路維護總成本，只需在雲中重新託管現有應用程式即可。

在*瞭解如何*將現有應用程式作為服務 （IaaS） 平臺遷移到 Azure 基礎結構之前，請務必分析要直接遷移到 Azure 中的 IaaS*的原因。* 此現代化成熟度級別的方案實質是開始在雲中使用 VM，而不是繼續使用當前本地基礎結構。

需要分析的另一點是 *，為什麼*您可能希望遷移到純 IaaS 雲，而不只是在 Azure 中添加更高級的託管服務。 首先確定哪些情況可能需要 IaaS。

圖 2-1 將雲基礎架構就緒應用程式定位在現代化成熟度級別：

![定位雲基礎架構就緒應用程式](./media/image2-1.png)

**圖 2-1。** 定位雲基礎架構就緒應用程式

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>為什麼將現有的 .NET Web 應用程式遷移到 Azure IaaS

遷移到雲的主要原因，即使在初始 IaaS 級別，也是為了實現成本降低。 通過使用更多託管基礎結構服務，您的組織可以降低其在硬體維護、伺服器或 VM 配置和部署以及基礎結構管理方面的投資。

在決定將應用移動到雲中後，選擇 IaaS 而不是像 PaaS 等更高級選項的主要原因很簡單，IaaS 環境將更為熟悉。 遷移到與當前本地環境類似的環境提供了較低的學習曲線，使其成為通往雲的最快路徑。

但是，以最快的路徑訪問雲並不意味著您將從在雲中運行應用程式中獲得最大好處。 在已經引入的雲優化和雲原生成熟度級別，任何組織都將從雲遷移中獲得最重要的好處。

也很明顯，應用程式將來在雲中運行時更容易實現現代化和重新構建，甚至在 IaaS 上也是如此。 應用程式資料移轉已經實現。 此外，您的組織將獲得在雲中工作所需的技能，並轉向在"雲文化中"運營。

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>何時遷移到 IaaS 而不是 PaaS

下一節將討論主要基於 PaaS 平臺和服務的雲優化應用程式。 這些應用從遷移到雲中為您提供最大的好處。

如果目標只是將現有應用程式移動到雲中，請首先確定不需要大量修改即可在 Azure 應用服務中運行的現有應用程式。 這些應用應該是雲優化的首批候選應用。

然後，對於仍無法移動到 Windows 容器和 PaaS 的應用（如應用服務或 Azure Kubernetes 服務等協調器），將這些應用遷移到簡單的普通 VM （IaaS）。

但是，請記住，與在 Azure 中使用 PaaS 服務相比，正確配置、保護和維護 VM 需要更多的時間和 IT 專業知識。 如果正在考慮 Azure 虛擬機器，請確保考慮到修補、更新和管理 VM 環境所需的持續維護工作。 Azure 虛擬機器是 IaaS。

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>使用 Azure 遷移分析現有應用程式並將其遷移到 Azure

遷移到雲並不一定困難。 但是，許多組織很難開始工作-要深入瞭解環境以及應用程式、工作負載和資料之間的緊密相互依賴性。 如果沒有這種可見度，就很難規劃前進的道路。 如果沒有有關成功遷移所需的詳細資訊，則無法在組織內進行正確的對話。 您對潛在的成本優勢瞭解不足，或者工作負載是否可以只是提升和移動，或者成功遷移需要大量的重新工作。 難怪許多組織猶豫不決。

[Azure 遷移](https://aka.ms/azuremigrate)是一項新服務，它提供説明您遷移到 Azure 所需的指導、見解和機制。 Azure Migrate 提供：

- 本地虛擬機器的發現和評估

- 內置依賴項映射，用於高置度發現多層應用程式

- 智慧右大小調整到 Azure 虛擬機器

- 相容性報告與修復潛在問題的準則

- 與 Azure 資料庫管理服務集成，用於資料庫發現和遷移

Azure 遷移讓您確信工作負荷可以遷移，對業務的影響最小，並在 Azure 中按預期運行。 借助正確的工具和指南，您可以實現最大的投資回報，同時確保滿足關鍵性能和可靠性需求。

圖 2-2 顯示了 Azure 遷移執行的所有伺服器和應用程式連接的內置依賴關係映射。

![定位雲基礎架構就緒應用程式](./media/image2-2.png)

**圖2-2。** 定位雲基礎架構就緒應用程式

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>使用 Azure 網站恢復將現有 VM 遷移到 Azure VM

作為端到端[Azure 遷移](https://aka.ms/azuremigrate)的一部分[，Azure 網站恢復](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)是一種工具，可用於輕鬆地將 Web 應用遷移到 Azure 中的 VM。 可以使用網站恢復將本地 VM 和物理伺服器複製到 Azure，或將其複製到輔助本地位置。 您甚至可以複製在受支援的 Azure VM、本地*Hyper-V* *VM、VMware* VM 上或在 Windows 或 Linux 物理伺服器上運行的工作負載。 複寫至 Azure 可排除維護次要資料中心的成本和複雜度。

網站恢復還專門針對部分本地和部分在 Azure 上的混合環境。 網站恢復通過在 VM 和本地物理伺服器上運行的應用（如果網站出現故障時）保持可用，有助於確保業務連續性。 它複製在 VM 和物理伺服器上運行的工作負載，以便在主網站無法接通，這些工作負載在輔助位置保持可用。 當主要網站再次開始運作及執行時，它會將工作負載復原至其中。

圖 2-3 顯示了使用 Azure 網站恢復執行多個 VM 遷移。

![定位雲基礎架構就緒應用程式](./media/image2-3.png)

**圖 2-3。** 定位雲基礎架構就緒應用程式

### <a name="additional-resources"></a>其他資源

- **Azure 遷移資料表**

    <https://aka.ms/azuremigration\_datasheet>

- **Azure 遷移**

    <https://aka.ms/azuremigrate>

- **Azure 遷移中心**

    <https://azure.microsoft.com/migration/>

- **使用 Site Recovery 移轉至 Azure**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure>

- **Azure 網站恢復服務概述**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-overview>

- **將 AWS 中的 VM 遷移到 Azure VM**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure>

>[!div class="step-by-step"]
>[上一個](index.md)
>[下一個](migrate-your-relational-databases-to-azure.md) <!-- Next Chapter -->

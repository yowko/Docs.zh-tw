---
title: 將現有的 .NET 應用程式隨即轉移至 Azure IaaS (雲端基礎結構就緒)
description: 使用 Azure 雲端和 Windows 容器將現有的 .NET 應用程式現代化。
ms.date: 04/28/2018
ms.openlocfilehash: e25ddbf9b6e62c264f3f4d4580d7df3553d262ea
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660744"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a>將現有的 .NET 應用程式隨即轉移至 Azure IaaS (雲端基礎結構就緒)

> 願景：作為第一個步驟, 若要減少內部部署投資和硬體和網路維護的總成本, 只要在雲端中重新裝載現有的應用程式即可。

在深入*瞭解如何*將現有應用程式遷移至 azure 基礎結構即服務 (IaaS) 平臺之前, 請務必分析您想要直接遷移至 azure 中 IaaS 的原因。 這個現代化成熟度層級的案例基本上是開始使用雲端中的 Vm, 而不是繼續使用您目前的內部部署基礎結構。

另一個要分析的重點是, 您可能會想要遷移到純 IaaS 雲端, 而不只是在 Azure 中新增更先進的受控服務。 判斷哪些情況下可能需要 IaaS。

圖2-1 將雲端基礎結構就緒的應用程式定位在現代化成熟度層級中:

![定位雲端基礎結構就緒的應用程式](./media/image2-1.png)

> **圖 2-1。** 定位雲端基礎結構就緒的應用程式

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>為何要將現有的 .NET web 應用程式遷移至 Azure IaaS

遷移至雲端 (即使是在初始 IaaS 層級) 的主要原因, 是為了降低成本。 藉由使用更多受控基礎結構服務, 您的組織可以降低其對硬體維護、伺服器或 VM 布建和部署以及基礎結構管理的投資。

在您決定將應用程式移至雲端之後, 您可能會選擇 IaaS 而不是像 PaaS 更多的選項, 因為 IaaS 環境會比較熟悉。 移至與您目前的內部部署環境類似的環境, 可提供較低的學習曲線, 使其成為雲端最快速的路徑。

不過, 採用最快速的雲端途徑, 並不表示您可以在雲端中執行應用程式, 以獲得最大效益。 任何組織都能從已推出的雲端優化和雲端原生成熟度層級, 獲得雲端遷移的最大效益。

它也顯而易見了, 當應用程式已經在雲端中執行 (即使是在 IaaS 上) 時, 就會更容易現代化和重新架構。 已達到應用程式資料移轉。 此外, 您的組織將獲得在雲端中工作所需的技能, 並將轉變為「雲端文化」的運作。

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>遷移至 IaaS 而非 PaaS 的時機

下一節將討論大部分以 PaaS 平臺和服務為基礎的雲端優化應用程式。 這些應用程式可讓您從遷移至雲端獲得最大的好處。 

如果您的目標只是要將現有的應用程式移至雲端, 請先找出不需要進行大量修改才能在 Azure App Service 中執行的現有應用程式。 這些應用程式應該是雲端優化的第一個候選項目。 

然後, 針對仍然無法移至 Windows 容器和 PaaS 的應用程式 (例如 App Service 或協調器之類的 Azure Kubernetes Service), 請將其遷移至簡單的純虛擬機器 (IaaS)。 

但請記住, 相較于在 Azure 中使用 PaaS 服務, 正確設定、保護和維護 Vm 需要更多的時間和 IT 專業知識。 如果您考慮使用 Azure 虛擬機器, 請務必將修補、更新和管理 VM 環境所需的持續性維護工作納入考慮。 Azure 虛擬機器是 IaaS。

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>使用 Azure Migrate 來分析您現有的應用程式並將其遷移至 Azure

遷移至雲端不一定很棘手。 但許多組織都難以開始使用, 以深入瞭解環境, 以及應用程式、工作負載和資料之間的緊密相依性。 如果沒有該可見度, 就很難以規劃向前邁進的路徑。 若沒有成功遷移所需的詳細資訊, 您的組織內就不能有正確的交談。 您不知道可能的成本優勢, 或工作負載是否可以直接隨即轉移, 或需要大量的返工才能成功遷移。 不知道有許多組織都有辦法。

[Azure Migrate](https://aka.ms/azuremigrate)是一項新服務, 提供協助您遷移至 Azure 所需的指引、深入解析和機制。 Azure Migrate 提供:

- 內部部署虛擬機器的探索與評估

- 適用于多層式應用程式之高度信賴度探索的內建相依性對應

- Azure 虛擬機器的智慧型適當調整大小

- 相容性報告與補救潛在問題的指導方針

- 與 Azure 資料庫管理服務整合, 以進行資料庫探索和遷移

Azure Migrate 讓您確信您的工作負載可以不受影響而對企業進行遷移, 並在 Azure 中如預期般執行。 透過適當的工具和指引, 您可以達到最大投資報酬率, 同時確保符合重要的效能和可靠性需求。

圖2-2 顯示 Azure Migrate 所執行之所有伺服器和應用程式連接的內建相依性對應。

![定位雲端基礎結構就緒的應用程式](./media/image2-2.png)

> **圖 2-2.** 定位雲端基礎結構就緒的應用程式

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>使用 Azure Site Recovery 將您現有的 Vm 遷移至 Azure Vm

做為端對端[Azure Migrate](https://aka.ms/azuremigrate)的一部分, [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)是一項工具, 可讓您輕鬆地將 web 應用程式遷移至 Azure 中的 vm。 您可以使用 Site Recovery 將內部部署 Vm 和實體伺服器複寫至 Azure, 或將它們複寫至次要內部部署位置。 您甚至可以複寫在支援的 Azure VM、內部部署*Hyper-v* Vm、 *VMware* VM 上, 或是在 Windows 或 Linux 實體伺服器上執行的工作負載。 複寫至 Azure 可排除維護次要資料中心的成本和複雜度。

Site Recovery 也是專屬於內部部署且部分在 Azure 上的混合式環境。 Site Recovery 藉由將在 Vm 和內部部署實體伺服器上執行的應用程式維持在網站停機狀態時, 協助確保業務持續性。 它會複寫在 Vm 和實體伺服器上執行的工作負載, 如果主要網站無法使用, 它們就會在次要位置中保持可用狀態。 當主要網站再次啟動並執行時, 它會將工作負載復原至該網站。

圖2-3 顯示如何使用 Azure Site Recovery 執行多個 VM 遷移。

![定位雲端基礎結構就緒的應用程式](./media/image2-3.png)

> **圖2-3。** 定位雲端基礎結構就緒的應用程式

### <a name="additional-resources"></a>其他資源

- **Azure Migrate 資料表**

    <https://aka.ms/azuremigration\_datasheet>

- **Azure Migrate**

    <https://aka.ms/azuremigrate>

- **Azure 移轉中心**

    <https://azure.microsoft.com/migration/>

- **使用 Site Recovery 遷移至 Azure**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure>

- **Azure Site Recovery 服務總覽**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-overview>

- **將 AWS 中的 Vm 遷移至 Azure Vm**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure>

>[!div class="step-by-step"]
>[上一頁](index.md)
>[下一頁](migrate-your-relational-databases-to-azure.md) <!-- Next Chapter -->

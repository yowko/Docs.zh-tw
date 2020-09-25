---
title: '將現有的 .NET 應用程式隨即轉移到 Azure IaaS (雲端基礎結構就緒) '
description: 使用 Azure 雲端和 Windows 容器將現有的 .NET 應用程式現代化。
ms.date: 04/28/2018
ms.openlocfilehash: d610222aa6649c1b28e198c074794dd316f895ec
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172166"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a>將現有的 .NET 應用程式隨即轉移到 Azure IaaS (雲端基礎結構就緒) 

> 願景：第一個步驟是減少內部部署的投資，以及硬體和網路維護的總成本，只要在雲端重新裝載現有的應用程式即可。

在*瞭解如何*將現有的應用程式遷移至 azure 基礎結構即服務 (IaaS) 平臺之前，請務必先分析您想要直接遷移至 Azure 中 IaaS*的原因。* 這個現代化成熟度層級的案例基本上是開始使用雲端中的 Vm，而不是繼續使用您目前的內部部署基礎結構。

要分析的另一個 *重點是，* 您可能想要遷移至單純的 IaaS 雲端，而不是只在 Azure 中新增更先進的受控服務。 判斷哪些案例可能需要 IaaS。

圖2-1 將雲端基礎結構就緒的應用程式置於現代化成熟度層級：

![定位雲端基礎結構就緒的應用程式](./media/image2-1.png)

**圖2-1。** 定位雲端基礎結構就緒的應用程式

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>將現有 .NET web 應用程式遷移至 Azure IaaS 的原因

遷移至雲端的主要原因是，即使是在初始 IaaS 層級，也是為了達成成本降低。 藉由使用更多受控基礎結構服務，您的組織可以降低其硬體維護、伺服器或 VM 布建和部署的投資，以及基礎結構管理。

決定將您的應用程式移至雲端之後，您可能會選擇 IaaS 而非更先進的選項（例如 PaaS），因為 IaaS 環境將更加熟悉。 移至與您目前的內部部署環境類似的環境，可提供較低的學習曲線，讓它成為最快的雲端途徑。

不過，採用最快的雲端途徑，並不表示您在雲端中執行應用程式時，將獲得最大效益。 任何組織都能從雲端遷移中獲得最大的優勢，也就是已推出的雲端優化和雲端原生成熟度等級。

此外，當應用程式已在雲端中執行時，甚至是在 IaaS 上執行時，也會變得更容易現代化和重新架構。 已達到應用程式資料移轉。 此外，您的組織也會獲得在雲端中工作所需的技能，並讓轉變成為「雲端文化」中的運作方式。

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>何時遷移至 IaaS 而非 PaaS

接下來的幾節將討論大部分的雲端優化應用程式，這些應用程式大多是以 PaaS 平臺和服務為基礎。 這些應用程式可讓您從遷移至雲端獲得最大效益。

如果您的目標只是要將現有的應用程式移至雲端，請先找出不需要大量修改才能在 Azure App Service 中執行的現有應用程式。 這些應用程式應該是第一個雲端優化的候選項目。

然後，針對仍無法移至 Windows 容器和 PaaS 的應用程式（例如 Azure Kubernetes Service App Service 或協調器），請將這些應用程式遷移至簡單的一般 Vm (IaaS) 。

但請記住，相較于在 Azure 中使用 PaaS 服務，正確設定、保護和維護 Vm 需要更多的時間和 IT 專業知識。 如果您考慮使用 Azure 虛擬機器，請務必考慮修補、更新和管理 VM 環境所需的持續性維護工作。 Azure 虛擬機器為 IaaS。

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>使用 Azure Migrate 來分析現有的應用程式，並將其遷移至 Azure

遷移至雲端並不難。 但許多組織都不難開始著手，以深入瞭解環境，以及應用程式、工作負載和資料之間的緊密相互相關性。 如果沒有該可見度，就很難規劃轉寄途徑。 若沒有成功遷移所需的詳細資訊，您的組織就不能有正確的交談。 您並不知道可能的成本優勢，或工作負載是否可以立即轉移，或需要大量的改變才能成功遷移。 對許多組織來說，並沒有任何疑惑。

[Azure Migrate](https://aka.ms/azuremigrate) 是新的服務，可提供協助您遷移至 Azure 所需的指引、見解和機制。 Azure Migrate 提供：

- 內部部署虛擬機器的探索和評量

- 用於高度信賴探索多層式應用程式的內建相依性對應

- 對 Azure 虛擬機器進行智慧型適當大小調整

- 相容性報告以及補救潛在問題的指導方針

- 與 Azure 資料庫管理服務整合，以進行資料庫探索和遷移

Azure Migrate 可讓您安心地遷移工作負載，對企業的影響最低，並在 Azure 中如預期般執行。 使用適當的工具和指導方針，您可以獲得最大投資報酬率，同時確保符合重要的效能和可靠性需求。

圖2-2 顯示 Azure Migrate 所執行之所有伺服器和應用程式連接的內建相依性對應。

![定位雲端基礎結構就緒的應用程式](./media/image2-2.png)

**圖2-2。** 定位雲端基礎結構就緒的應用程式

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>使用 Azure Site Recovery 將現有的 Vm 遷移至 Azure Vm

作為端對端 [Azure Migrate](https://aka.ms/azuremigrate)的一部分， [Azure Site Recovery](/azure/site-recovery/site-recovery-overview) 是一種工具，可讓您輕鬆地將 web 應用程式遷移至 Azure 中的 vm。 您可以使用 Site Recovery 將內部部署 Vm 和實體伺服器複寫至 Azure，或將其複寫至次要內部部署位置。 您甚至可以複寫在支援的 Azure VM、內部部署 *Hyper-v* VM、 *VMware* Vm 或 Windows 或 Linux 實體伺服器上執行的工作負載。 複寫至 Azure 可排除維護次要資料中心的成本和複雜度。

Site Recovery 也專門針對部分在內部部署且部分在 Azure 上的混合式環境進行。 Site Recovery 有助於確保商務持續性，方法是讓在 Vm 上執行的應用程式和內部部署實體伺服器保持可用狀態（如果網站停止運作）。 它會複寫在 Vm 和實體伺服器上執行的工作負載，以便在主要網站無法使用時，仍可在次要位置中使用。 當主要網站再次開始運作及執行時，它會將工作負載復原至其中。

圖2-3 顯示如何使用 Azure Site Recovery 來執行多個 VM 遷移。

![定位雲端基礎結構就緒的應用程式](./media/image2-3.png)

**圖2-3。** 定位雲端基礎結構就緒的應用程式

### <a name="additional-resources"></a>其他資源

- **Azure Migrate 資料工作表**

    <https://aka.ms/azuremigration\_datasheet>

- **Azure Migrate**

    <https://aka.ms/azuremigrate>

- **Azure 移轉中心**

    <https://azure.microsoft.com/migration/>

- **使用 Site Recovery 移轉至 Azure**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure>

- **Azure Site Recovery 服務總覽**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-overview>

- **將 AWS 中的 Vm 遷移至 Azure Vm**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure>

>[!div class="step-by-step"]
>[上一個](index.md) 
>[下一步](migrate-your-relational-databases-to-azure.md) <!-- Next Chapter -->

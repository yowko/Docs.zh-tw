---
title: 提起並移動現有的.NET 應用程式到 Azure IaaS （基礎結構雲端）
description: 現代化現有的.NET 應用程式與 Azure 雲端與 Windows 容器。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 458b1bd1fc9fc24ce43d0926655fe0767aabc43c
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "33956444"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a>提起並移動現有的.NET 應用程式到 Azure IaaS （基礎結構雲端）

> 願景： 以降低您在內部部署投資和總成本的硬體和網路功能維護，只是重新裝載的現有應用程式在雲端中的第一個步驟。

之前*如何*若要移轉至 Azure 的基礎結構即服務 (IaaS) 平台的現有應用程式，務必分析原因*為什麼*您會想要直接與 IaaS 移轉在 Azure 中。 若要開始使用 Vm 雲端，而不是繼續使用目前的內部部署基礎結構中基本上是此現代化成熟度層級的案例。

若要分析的另一個點是*為什麼*您可能想要移轉到純虛擬的 IaaS 雲端，而非只新增更多進階在 Azure 中受管理的服務。 判斷的情況下可能會在第一次需要 IaaS。

圖 2-1 放現代化成熟度層級中的雲端基礎結構就緒應用程式：

![定位雲端基礎結構就緒應用程式](./media/image2-1.png)

> **圖 2-1。** 定位雲端基礎結構就緒應用程式

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>為什麼要移轉現有的.NET web 應用程式至 Azure IaaS

若要移轉至雲端，甚至在初始的 IaaS 層級的主要原因是達成成本大幅降低。 藉由使用更多的受管理的基礎結構服務，您的組織可以降低其硬體維護、 伺服器或 VM 佈建和部署和管理基礎結構的投資。

您決定要將您的應用程式移到雲端之後，將會更熟悉為什麼您可能會選擇 IaaS 而不是更進階的選項，例如 PaaS 只為的 IaaS 環境的主要原因。 在內部部署環境移至類似於您目前的環境，提供較低的學習曲線，使它的最快速的路徑至雲端。

不過，採用至雲端最快速的路徑並不表示您將獲得最大效益，不必在雲端中執行的應用程式。 任何組織會獲得最重要的優點，從雲端移轉已導入的雲端最佳化和原生雲端成熟度層級。

它也有變得顯而易見的應用程式可以輕易地現代化和未來 rearchitect 在雲端中，即使在 IaaS 上執行時。 已完成應用程式資料移轉。 此外，您的組織會有獲得所需的雲端中使用的技術和對排班運作 」 雲端文化特性 」。

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>當移轉到 PaaS 而不是 IaaS 至

下一節中討論大部分基礎 PaaS 平台和服務的雲端最佳化應用程式。 這些應用程式可讓您的大部分優點從移轉至雲端。 

如果您的目標是單純將現有的應用程式到雲端，首先，識別現有的應用程式不需要大幅修改 Azure App Service 中執行。 這些應用程式應該是第一個的對象雲端最佳化。 

然後，應用程式，仍無法移到 Windows 容器和 PaaS 這類應用程式服務或 Azure Service Fabric，像是 orchestrators 移轉這些簡單的純文字 vm (IaaS)。 

但是，請記住，正確地設定、 保護以及維護 Vm 需要更多的時間和相較於使用 PaaS 服務在 Azure 中的 IT 專業知識。 如果您考慮 Azure 虛擬機器，請確定您進行考量的修補程式、 更新和管理 VM 環境所需的持續性維護工作。 Azure 虛擬機器是 IaaS。

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>使用 Azure 移轉分析並移轉現有的應用程式至 Azure

移轉至雲端不一定要是困難。 但是，許多組織難開始-以進一步顯示環境中，應用程式、 工作負載和資料之間的緊密相互依存性。 能見度不足，可能很難計劃的路徑向前復原。 未成功移轉的必要條件的詳細資訊，您不能有右交談組織內。 您不知道可能成本的優點，或工作負載是否可以只增益集和-shift 或需要大幅重新作業已成功移轉。 難怪，許多組織延遲。

[Azure 移轉](https://aka.ms/azuremigrate)是一種新的服務，提供指引、 深入資訊，以及協助您移轉至 Azure 時所需的機制。 提供 azure 移轉：

- 探索及評估在內部部署虛擬機器

- 內建的相依性對應的多層應用程式的高信心探索

- 智慧型決定正確的大小到 Azure 虛擬機器

- 相容性報告與修復的潛在問題的指導方針

- 資料庫探索和移轉 Azure 資料庫管理服務整合

Azure 的移轉可讓您對於的信心，您的工作負載可以移轉與業務的影響降到最低，並如預期般在 Azure 中執行。 使用適當的工具和指引，您可以達到時以確保重大效能的投資報酬率最大，並且符合可靠性的需求。

圖 2-2 會顯示由 Azure 移轉的所有伺服器和應用程式連接的內建的相依性對應。

![定位雲端基礎結構就緒應用程式](./media/image2-2.png)

> **圖 2-2。** 定位雲端基礎結構就緒應用程式

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>使用 Azure Site Recovery，以將您現有的 Vm 移轉到 Azure Vm

做為端對端的一部分[Azure 移轉](https://aka.ms/azuremigrate)， [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)是一種工具可讓您輕鬆地將您的 web 應用程式移轉至 Azure 中的 Vm。 在內部部署 Vm 和實體伺服器複寫至 Azure，或將它們複寫至次要內部部署位置，您可以使用站台復原。 您甚至可以複寫支援的 Azure VM，在內部部署上執行的工作負載*HYPER-V* VM 上*VMware* VM，或在 Windows 或 Linux 的實體伺服器上。 複寫至 Azure 排除的成本和複雜度維護次要資料中心。

站台復原也會特別針對混合式環境的部分在內部部署和部分在 Azure。 站台復原可協助確保商務持續性會保留您在 Vm 執行的應用程式和內部部署可用的實體伺服器如果站台效能降低。 它會複寫，讓它們留可用在次要位置，如果無法使用主要站台 Vm 和實體伺服器執行的工作負載。 它會復原到主要站台時的設定而定，再次執行的工作負載。

圖 2-3 顯示使用 Azure Site Recovery 的多個 VM 的移轉作業執行。

![定位雲端基礎結構就緒應用程式](./media/image2-3.png)

> **圖 2-3。** 定位雲端基礎結構就緒應用程式

### <a name="additional-resources"></a>其他資源

- **Azure 移轉的資料工作表**

    [https://aka.ms/azuremigration\_資料工作表](https://aka.ms/azuremigration\_datasheet)

- **Azure 移轉**

    [http://azuremigrationcenter.com/](http://azuremigrationcenter.com/)

- **移轉至 Azure Site recovery**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure)

- **Azure Site Recovery 服務概觀**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-overview](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)

- **在 Azure Vm 的 AWS 移轉 Vm**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure)

>[!div class="step-by-step"]
[上一頁](index.md)
[下一頁](migrate-your-relational-databases-to-azure.md)

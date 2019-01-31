---
title: 撤銷並轉移現有的.NET 應用程式至 Azure IaaS （雲端基礎結構就緒）
description: 現代化現有的.NET 應用程式與 Azure 雲端和 Windows 容器。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 2b987d43f476f261bfdbd1b2af6ca7f792178cf8
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266620"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a>撤銷並轉移現有的.NET 應用程式至 Azure IaaS （雲端基礎結構就緒）

> 願景：第一個步驟中，若要減少您的內部部署投資與硬體和網路維護的整體成本，只要重新裝載在雲端中現有的應用程式。

進入*如何*若要移轉現有的應用程式至 Azure 的基礎結構即服務 (IaaS) 平台，務必要分析的原因*為什麼*您會想要直接到 IaaS 移轉在 Azure 中。 若要開始使用 Vm 在雲端中，而不會繼續使用目前的內部部署基礎結構基本上是這個現代化成熟度等級的案例。

若要分析的另一個點是*為什麼*您可能想要移轉至純 IaaS 雲端，而非只新增更進階的受管理的服務，在 Azure 中。 判斷的情況下可能會在一開始需要 IaaS。

圖 2-1 放置現代化成熟度等級的雲端基礎結構就緒應用程式：

![定位的雲端基礎結構就緒應用程式](./media/image2-1.png)

> **圖 2-1。** 定位的雲端基礎結構就緒應用程式

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>為什麼要移轉至 Azure IaaS 的現有.NET web 應用程式

若要移轉至雲端，即使在初始的 IaaS 層級，主要原因是為了達成降低成本。 藉由使用更多的受管理的基礎結構服務，您的組織可以降低其硬體維護、 伺服器或 VM 佈建和部署和管理基礎結構的投資。

決定您的應用程式移至雲端之後，為什麼您可能會選擇 IaaS 而不是更進階的選項，例如 PaaS 只是，IaaS 環境的主要原因將會更熟悉。 在內部部署環境移至類似於您目前的環境，提供較低的學習曲線，讓它的最快路徑至雲端。

不過，採用最快路徑到雲端並不表示您會獲得最大效益，不需要在雲端中執行的應用程式。 任何組織會獲得最大的好處，從已導入的雲端最佳化和雲端原生成熟度等級的雲端移轉。

也變得更明顯，應用程式是您更輕鬆地現代化，並在雲端中，即使在 IaaS 上執行時在未來重新架構。 應用程式資料移轉已完成。 此外，您的組織會有獲得在雲端中工作所需的技能和對排班作業系統中 「 雲端文化特性 」。

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>移轉至 IaaS 而不是，PaaS

下一節中討論大部分基礎 PaaS 平台和服務的雲端最佳化應用程式。 這些應用程式可讓您的大部分優點從移轉至雲端。 

如果您的目標是單純將現有的應用程式到雲端，首先，識別現有的應用程式不需要在 Azure App Service 中執行的大幅修改。 這些應用程式應該是第一個適合雲端最佳化。 

然後，應用程式，仍無法將移至 Windows 容器和 PaaS 例如 App Service 或 Azure Service Fabric 等協調器移轉到簡單純文字的 Vm (IaaS)。 

但請記住，正確地設定、 保護和維護 Vm 需要更多的時間和相較於在 Azure 中使用 PaaS 服務的 IT 專業知識。 如果您考慮 Azure 虛擬機器，請確定，您需要考慮修補、 更新和管理 VM 環境所需的持續性維護工作。 Azure 虛擬機器是 IaaS。

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>使用 Azure Migrate 分析並移轉您現有的應用程式至 Azure

移轉至雲端，不一定要很困難。 不過，許多組織必須努力開始建置，以取得深入了解環境中，應用程式、 工作負載和資料之間的緊密相互依存性。 能見度，它可能難以規劃路徑轉接。 沒有上要成功移轉的必要條件的詳細資訊，您不能有對話在組織內。 您不知道夠清楚的潛在成本效益，或是否可以只和轉移工作負載，或需要大幅修改一下，才能成功移轉。 難怪，許多組織不太願意。

[Azure Migrate](https://aka.ms/azuremigrate)是新的服務可提供指引、 深入解析，以及可協助您移轉至 Azure 所需的機制。 Azure Migrate 提供：

- 探索及評定內部部署虛擬機器

- 值得高度信賴的多層式應用程式的探索內建的相依性對應

- 智慧型的正確調整大小，以 Azure 虛擬機器

- 相容性報告，修復的潛在問題的指導方針

- 資料庫探索和移轉的 Azure 資料庫管理服務整合

Azure Migrate 提供信心，您的工作負載可以移轉與業務的影響降到最低，並如預期般在 Azure 中執行。 使用適當的工具和指引，就能夠同時以確保效能的重要投資報酬率上限，並符合可靠性需求。

圖 2-2 會顯示 Azure Migrate 所執行的所有伺服器和應用程式連接的內建的相依性對應。

![定位的雲端基礎結構就緒應用程式](./media/image2-2.png)

> **圖 2-2。** 定位的雲端基礎結構就緒應用程式

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>使用 Azure Site Recovery 將您現有的 Vm 移轉至 Azure Vm

做為端對端的一部分[Azure Migrate](https://aka.ms/azuremigrate)， [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)是一種工具，可用來輕鬆地將您的 web 應用程式移轉到 Azure 中 Vm。 您可以使用 Site Recovery，將內部部署 Vm 和實體伺服器複寫至 Azure，或將它們複寫至次要內部部署位置。 您甚至可以複寫在支援的 Azure VM，在內部部署執行的工作負載*HYPER-V* VM 上*VMware* VM，或在 Windows 或 Linux 實體伺服器上。 複寫至 Azure 可排除維護次要資料中心的複雜度與成本。

Site Recovery 也會針對混合式環境的部分在內部部署和部分在 Azure。 Site Recovery 可協助確保業務持續性讓您在 Vm 執行的應用程式和內部部署可用的實體伺服器如果站台無法運作。 它會複寫，讓它們仍可在次要位置如果主要站台無法使用，在 Vm 和實體伺服器執行的工作負載。 它會復原到主要站台，當它啟動時，再次執行的工作負載。

圖 2-3 會顯示執行的多個 VM 移轉，藉由使用 Azure Site Recovery。

![定位的雲端基礎結構就緒應用程式](./media/image2-3.png)

> **圖 2-3。** 定位的雲端基礎結構就緒應用程式

### <a name="additional-resources"></a>其他資源

- **Azure Migrate Datasheet**

    [https://aka.ms/azuremigration\_datasheet](https://aka.ms/azuremigration\_datasheet)

- **Azure Migrate**

    [https://aka.ms/azuremigrate](https://aka.ms/azuremigrate)

- **Azure 移轉中心**

    [https://azure.microsoft.com/migration/](https://azure.microsoft.com/migration/)

- **使用 Site Recovery 移轉至 Azure**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure)

- **Azure Site Recovery 服務概觀**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-overview](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)

- **在 Azure Vm 的 AWS Vm 移轉**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure)

>[!div class="step-by-step"]
>[上一頁](index.md)
>[下一頁](migrate-your-relational-databases-to-azure.md)

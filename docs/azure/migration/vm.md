---
title: 將 ASP.NET Web 應用程式遷移至 Azure VM
description: 了解如何從內部部署將 ASP.NET Web 應用程式移轉至 Azure 虛擬機器。
ms.topic: how-to
ms.date: 06/20/2020
ms.openlocfilehash: 940243310c5e6ed13d2a42c8d9d87244200479f5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171555"
---
# <a name="migrate-an-aspnet-web-application-to-an-azure-virtual-machine"></a>將 ASP.NET Web 應用程式移轉至 Azure 虛擬機器

此文件說明了如何從內部部署將 ASP.NET Web 應用程式移轉至 Azure 虛擬機器。

## <a name="quickstart"></a>快速入門

了解如何建立虛擬機器，並將您的應用程式發佈到該虛擬機器中：[發佈至 Azure VM](https://tutorials.visualstudio.com/aspnet-vm/intro)

## <a name="get-started"></a>開始使用

這些教學課程會示範建立 (或移轉) 虛擬機器的步驟，如何將 Web 應用程式發佈至其中，以及 Azure 中其他可能需要用以支援應用程式的工作。

- 使用下列其中一個選項，在 Azure 中為您的 ASP.NET 應用程式建立虛擬機器：
  - [為 ASP.NET 應用程式建立新的虛擬機器](https://go.microsoft.com/fwlink/?linkid=863237)
  - [遷移現有的內部部署 VMWare 虛擬機器](/azure/migrate/tutorial-migrate-vmware)
  - [遷移現有的內部部署 Hyper-v 虛擬機器](/azure/migrate/tutorial-migrate-hyper-v)
- [使用 Visual Studio 發佈您的應用程式](https://go.microsoft.com/fwlink/?linkid=863240)
- [建立 VM 的安全虛擬網路](/azure/virtual-network/virtual-network-get-started-vnet-subnet)
- [建立應用程式的 CI/CD 管線](/vsts/build-release/apps/cd/deploy-webdeploy-iis-deploygroups)
- [為高可用性和延展性移至虛擬機器擴展集](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)

## <a name="considerations"></a>考量

### <a name="benefits"></a>優點

虛擬機器提供了從內部部署將應用程式移轉至雲端最簡單的路徑。 可讓您複寫應用程式在內部部署中使用的相同環境，且不需維護自己的資料中心。 虛擬機器擴展集針對在虛擬機器中執行的應用程式提供高可用性和延展性。

### <a name="virtual-machine-size"></a>虛擬機器大小

針對您的工作負載選擇最佳化的虛擬機器大小和類型。 如需詳細資訊，請參閱 [Azure 中的 Windows 虛擬機器大小](/azure/virtual-machines/windows/sizes)。

### <a name="maintenance"></a>維護

正如同內部部署機器，您必須負責維護和更新虛擬機器 <sup>&#42;</sup>。 如果您的應用程式可以在平台即服務 (PaaS) 環境中執行，如 [Azure App Service](/azure/app-service/) 或[容器](/azure/app-service/containers/)，則將會移除這項需求。

*<sup>&#42;</sup>[虛擬機器擴展集的自動作業系統升級](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade)目前可提供預覽服務。*

### <a name="virtual-networks"></a>虛擬網路

Azure 虛擬網路可讓您：

- 建置可控制的混合式基礎結構
- 使用自己的 IP 位址與 DNS 伺服器
- 為您的應用程式建立隔離且高度安全的環境
- 使用其中一種[連線選項](/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti)將 VM 連線至內部部署網路
- 使用 [ExpressRoute](https://azure.microsoft.com/services/expressroute/) 將您的虛擬機器整合到內部部署網路

請參閱[虛擬網路文件](/azure/virtual-network/)以開始使用

### <a name="active-directory"></a>Active Directory

許多應用程式使用 Active Directory 進行驗證和身分識別管理。

- Azure AD Connect 可讓您整合內部部署目錄與 Azure Active Directory。 若要開始，請參閱[整合您的內部部署目錄與 Azure Active Directory](/azure/active-directory/connect/active-directory-aadconnect)。
- 或者，[ExpressRoute](https://azure.microsoft.com/services/expressroute/) 可讓應用程式存取您的內部部署 Active Directory。

### <a name="sql-databases"></a>SQL Database

如果您的應用程式正在使用內部部署資料庫，則預設應用程式將無法與其通話。 您可以：

- 設定混合式網路，讓應用程式存取您在內部部署執行的資料庫。
- 將資料庫移轉至 Azure。 如需詳細資訊，請參閱將 [您的 SQL Server 資料庫移轉至 Azure](sql.md)。

### <a name="high-availability-and-scalability"></a>高可用性和延展性

#### <a name="virtual-machine-scale-sets"></a>虛擬機器擴展集

若您想要確定應用程式為高可用性且可以調整，可以將 VM 映像移轉到 Azure 虛擬機器擴展集來改善應用程式的可用性和延展性。 VM 擴展集可讓您使用已設定的現有 VM，或設定組建管線來建立應用程式的映射。

若要開始，請參閱[在虛擬機器擴展集上部署您的應用程式](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)。

#### <a name="centralized-logging"></a>集中式記錄

在多個執行個體中執行應用程式時，請考慮將您的記錄儲存在集中位置，如 [Azure 儲存體](/azure/storage/)。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [將 SQL Server 資料庫移轉至 Azure](sql.md)

---
title: 將ASP.NET Web 應用移到 Azure VM
description: 了解如何從內部部署將 ASP.NET Web 應用程式移轉至 Azure 虛擬機器。
ms.topic: how-to
ms.date: 11/15/2017
ms.openlocfilehash: cc9477de92e6105762636ed3a2241949e69ac8ea
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "82072120"
---
# <a name="migrate-an-aspnet-web-application-to-an-azure-virtual-machine"></a>將 ASP.NET Web 應用程式移轉至 Azure 虛擬機器

此文件說明了如何從內部部署將 ASP.NET Web 應用程式移轉至 Azure 虛擬機器。

## <a name="quickstart"></a>快速入門

了解如何建立虛擬機器，並將您的應用程式發佈到該虛擬機器中：[發佈至 Azure VM](https://tutorials.visualstudio.com/aspnet-vm/intro)

## <a name="get-started"></a>開始使用

這些教學課程會示範建立 (或移轉) 虛擬機器的步驟，如何將 Web 應用程式發佈至其中，以及 Azure 中其他可能需要用以支援應用程式的工作。

- 使用以下選項之一在 Azure 中為 Azure 中的 ASP.NET 應用程式建立虛擬機器:
  - [為 ASP.NET 應用程式建立新的虛擬機器](https://go.microsoft.com/fwlink/?linkid=863237)
  - [移轉現有的本地 VMWare 虛擬機器](https://docs.microsoft.com/azure/migrate/tutorial-migrate-vmware)
  - [移轉現有的本地超 V 虛擬機器](https://docs.microsoft.com/azure/migrate/tutorial-migrate-hyper-v)
- [使用 Visual Studio 發佈您的應用程式](https://go.microsoft.com/fwlink/?linkid=863240)
- [建立 VM 的安全虛擬網路](https://docs.microsoft.com/azure/virtual-network/virtual-network-get-started-vnet-subnet)
- [建立應用程式的 CI/CD 管線](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-webdeploy-iis-deploygroups)
- [為高可用性和延展性移至虛擬機器擴展集](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)

## <a name="considerations"></a>考量

### <a name="benefits"></a>優點

虛擬機器提供了從內部部署將應用程式移轉至雲端最簡單的路徑。 可讓您複寫應用程式在內部部署中使用的相同環境，且不需維護自己的資料中心。 虛擬機器擴展集針對在虛擬機器中執行的應用程式提供高可用性和延展性。

### <a name="virtual-machine-size"></a>虛擬機器大小

針對您的工作負載選擇最佳化的虛擬機器大小和類型。 有關詳細資訊,請參閱[Azure 中 Windows 虛擬機器的大小](https://docs.microsoft.com/azure/virtual-machines/windows/sizes)。

### <a name="maintenance"></a>維護

正如同內部部署機器，您必須負責維護和更新虛擬機器 <sup>&#42;</sup>。 如果您的應用程式可以在平台即服務 (PaaS) 環境中執行，如 [Azure App Service](https://docs.microsoft.com/azure/app-service/) 或[容器](https://docs.microsoft.com/azure/app-service/containers/)，則將會移除這項需求。

*<sup>&#42;</sup>[虛擬機器擴展集的自動作業系統升級](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade)目前可提供預覽服務。*

### <a name="virtual-networks"></a>虛擬網路

Azure 虛擬網路可讓您：

- 建置可控制的混合式基礎結構
- 使用自己的 IP 位址與 DNS 伺服器
- 為應用程式建立一個孤立且高度安全的環境
- 使用其中一種[連線選項](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti)將 VM 連線至內部部署網路
- 使用 [ExpressRoute](https://azure.microsoft.com/services/expressroute/) 將您的虛擬機器整合到內部部署網路

請參閱[虛擬網路文件](https://docs.microsoft.com/azure/virtual-network/)以開始使用

### <a name="active-directory"></a>Active Directory
許多應用程式使用 Active Directory 進行驗證和身分識別管理。

- Azure AD Connect 可讓您整合內部部署目錄與 Azure Active Directory。 若要開始，請參閱[整合您的內部部署目錄與 Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)。
- 或者，[ExpressRoute](https://azure.microsoft.com/services/expressroute/) 可讓應用程式存取您的內部部署 Active Directory。

### <a name="sql-databases"></a>SQL Database

如果您的應用程式正在使用內部部署資料庫，則預設應用程式將無法與其通話。 您可以：

- 設定混合式網路，讓應用程式存取您在內部部署執行的資料庫。
- 將資料庫移轉至 Azure。 有關詳細資訊,請參閱將[SQL Server 資料庫遷移到 Azure](sql.md)。

### <a name="high-availability-and-scalability"></a>高可用性和延展性

#### <a name="virtual-machine-scale-sets"></a>虛擬機器擴展集
若您想要確定應用程式為高可用性且可以調整，可以將 VM 映像移轉到 Azure 虛擬機器擴展集來改善應用程式的可用性和延展性。 VM Scale 集提供了使用已配置的現有 VM 的能力,或設置生成管道以使用應用程式生成映射。

若要開始，請參閱[在虛擬機器擴展集上部署您的應用程式](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)。

#### <a name="centralized-logging"></a>集中式記錄
在多個執行個體中執行應用程式時，請考慮將您的記錄儲存在集中位置，如 [Azure 儲存體](https://docs.microsoft.com/azure/storage/)。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [將 SQL Server 資料庫移轉至 Azure](sql.md)
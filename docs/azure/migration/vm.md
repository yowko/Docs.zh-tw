---
title: 將 ASP.NET Web 應用程式遷移至 Azure VM
description: 了解如何從內部部署將 ASP.NET Web 應用程式移轉至 Azure 虛擬機器。
ms.topic: how-to
ms.date: 06/20/2020
ms.openlocfilehash: 5ef340d020b72bebe46fe598fe68e7d02d0c0363
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174240"
---
# <a name="migrate-an-aspnet-web-application-to-an-azure-virtual-machine"></a><span data-ttu-id="8ad82-103">將 ASP.NET Web 應用程式移轉至 Azure 虛擬機器</span><span class="sxs-lookup"><span data-stu-id="8ad82-103">Migrate an ASP.NET Web application to an Azure Virtual Machine</span></span>

<span data-ttu-id="8ad82-104">此文件說明了如何從內部部署將 ASP.NET Web 應用程式移轉至 Azure 虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="8ad82-104">This document provides an overview of how to migrate an ASP.NET web application from on-premises to an Azure Virtual Machine.</span></span>

## <a name="quickstart"></a><span data-ttu-id="8ad82-105">快速入門</span><span class="sxs-lookup"><span data-stu-id="8ad82-105">Quickstart</span></span>

<span data-ttu-id="8ad82-106">了解如何建立虛擬機器，並將您的應用程式發佈到該虛擬機器中：[發佈至 Azure VM](https://tutorials.visualstudio.com/aspnet-vm/intro)</span><span class="sxs-lookup"><span data-stu-id="8ad82-106">Learn how to create a virtual machine and publish your app to it: [Publish to an Azure VM](https://tutorials.visualstudio.com/aspnet-vm/intro)</span></span>

## <a name="get-started"></a><span data-ttu-id="8ad82-107">開始使用</span><span class="sxs-lookup"><span data-stu-id="8ad82-107">Get Started</span></span>

<span data-ttu-id="8ad82-108">這些教學課程會示範建立 (或移轉) 虛擬機器的步驟，如何將 Web 應用程式發佈至其中，以及 Azure 中其他可能需要用以支援應用程式的工作。</span><span class="sxs-lookup"><span data-stu-id="8ad82-108">These tutorials demonstrate the steps to create (or migrate) a virtual machine, publish your web application to it, and other tasks that may be required to support your application in Azure.</span></span>

- <span data-ttu-id="8ad82-109">使用下列其中一個選項，在 Azure 中為您的 ASP.NET 應用程式建立虛擬機器：</span><span class="sxs-lookup"><span data-stu-id="8ad82-109">Create a virtual machine for your ASP.NET application in Azure using one of the following options:</span></span>
  - [<span data-ttu-id="8ad82-110">為 ASP.NET 應用程式建立新的虛擬機器</span><span class="sxs-lookup"><span data-stu-id="8ad82-110">Create a new virtual machine for ASP.NET Applications</span></span>](https://go.microsoft.com/fwlink/?linkid=863237)
  - [<span data-ttu-id="8ad82-111">遷移現有的內部部署 VMWare 虛擬機器</span><span class="sxs-lookup"><span data-stu-id="8ad82-111">Migrate an existing on-premises VMWare virtual machine</span></span>](/azure/migrate/tutorial-migrate-vmware)
  - [<span data-ttu-id="8ad82-112">遷移現有的內部部署 Hyper-v 虛擬機器</span><span class="sxs-lookup"><span data-stu-id="8ad82-112">Migrate an existing on-premises Hyper-V virtual machine</span></span>](/azure/migrate/tutorial-migrate-hyper-v)
- [<span data-ttu-id="8ad82-113">使用 Visual Studio 發佈您的應用程式</span><span class="sxs-lookup"><span data-stu-id="8ad82-113">Publish your app using Visual Studio</span></span>](https://go.microsoft.com/fwlink/?linkid=863240)
- [<span data-ttu-id="8ad82-114">建立 VM 的安全虛擬網路</span><span class="sxs-lookup"><span data-stu-id="8ad82-114">Create a secure virtual network for your VMs</span></span>](/azure/virtual-network/virtual-network-get-started-vnet-subnet)
- [<span data-ttu-id="8ad82-115">建立應用程式的 CI/CD 管線</span><span class="sxs-lookup"><span data-stu-id="8ad82-115">Create a CI/CD pipeline for your application</span></span>](/vsts/build-release/apps/cd/deploy-webdeploy-iis-deploygroups)
- [<span data-ttu-id="8ad82-116">為高可用性和延展性移至虛擬機器擴展集</span><span class="sxs-lookup"><span data-stu-id="8ad82-116">Move to a VM scale set for high availability and scalability</span></span>](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)

## <a name="considerations"></a><span data-ttu-id="8ad82-117">考量事項</span><span class="sxs-lookup"><span data-stu-id="8ad82-117">Considerations</span></span>

### <a name="benefits"></a><span data-ttu-id="8ad82-118">優點</span><span class="sxs-lookup"><span data-stu-id="8ad82-118">Benefits</span></span>

<span data-ttu-id="8ad82-119">虛擬機器提供了從內部部署將應用程式移轉至雲端最簡單的路徑。</span><span class="sxs-lookup"><span data-stu-id="8ad82-119">Virtual machines offer the easiest path to migrate an application from on-premises to the cloud.</span></span> <span data-ttu-id="8ad82-120">可讓您複寫應用程式在內部部署中使用的相同環境，且不需維護自己的資料中心。</span><span class="sxs-lookup"><span data-stu-id="8ad82-120">They enable you to replicate the same environment your application uses on-premises, while removing the need to maintain your own data centers.</span></span> <span data-ttu-id="8ad82-121">虛擬機器擴展集針對在虛擬機器中執行的應用程式提供高可用性和延展性。</span><span class="sxs-lookup"><span data-stu-id="8ad82-121">Virtual Machine Scale Sets provide high availability and scalability for applications running in Virtual Machines.</span></span>

### <a name="virtual-machine-size"></a><span data-ttu-id="8ad82-122">虛擬機器大小</span><span class="sxs-lookup"><span data-stu-id="8ad82-122">Virtual Machine Size</span></span>

<span data-ttu-id="8ad82-123">針對您的工作負載選擇最佳化的虛擬機器大小和類型。</span><span class="sxs-lookup"><span data-stu-id="8ad82-123">Choose the virtual machine size and type that is best optimized for your workload.</span></span> <span data-ttu-id="8ad82-124">如需詳細資訊，請參閱[Azure 中的 Windows 虛擬機器大小](/azure/virtual-machines/windows/sizes)。</span><span class="sxs-lookup"><span data-stu-id="8ad82-124">For more information, see [Sizes for Windows virtual machines in Azure](/azure/virtual-machines/windows/sizes).</span></span>

### <a name="maintenance"></a><span data-ttu-id="8ad82-125">維護</span><span class="sxs-lookup"><span data-stu-id="8ad82-125">Maintenance</span></span>

<span data-ttu-id="8ad82-126">正如同內部部署機器，您必須負責維護和更新虛擬機器 <sup>&#42;</sup>。</span><span class="sxs-lookup"><span data-stu-id="8ad82-126">Just like an on-premises machine, you are responsible for maintaining and updating the virtual machine<sup>&#42;</sup>.</span></span> <span data-ttu-id="8ad82-127">如果您的應用程式可以在平台即服務 (PaaS) 環境中執行，如 [Azure App Service](/azure/app-service/) 或[容器](/azure/app-service/containers/)，則將會移除這項需求。</span><span class="sxs-lookup"><span data-stu-id="8ad82-127">If your application can run in a Platform as a Service (PaaS) environment such as [Azure App Service](/azure/app-service/) or in a [container](/azure/app-service/containers/), that will remove this need.</span></span>

<span data-ttu-id="8ad82-128">*<sup>&#42;</sup>[虛擬機器擴展集的自動作業系統升級](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade)目前可提供預覽服務。*</span><span class="sxs-lookup"><span data-stu-id="8ad82-128">*<sup>&#42;</sup>[Automatic OS upgrades for virtual machine scale sets](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade) is currently available as a Preview service.*</span></span>

### <a name="virtual-networks"></a><span data-ttu-id="8ad82-129">虛擬網路</span><span class="sxs-lookup"><span data-stu-id="8ad82-129">Virtual Networks</span></span>

<span data-ttu-id="8ad82-130">Azure 虛擬網路可讓您：</span><span class="sxs-lookup"><span data-stu-id="8ad82-130">Azure Virtual Networks enable you to:</span></span>

- <span data-ttu-id="8ad82-131">建置可控制的混合式基礎結構</span><span class="sxs-lookup"><span data-stu-id="8ad82-131">Build a hybrid infrastructure that you control</span></span>
- <span data-ttu-id="8ad82-132">使用自己的 IP 位址與 DNS 伺服器</span><span class="sxs-lookup"><span data-stu-id="8ad82-132">Bring your own IP addresses and DNS servers</span></span>
- <span data-ttu-id="8ad82-133">為您的應用程式建立獨立且極為安全的環境</span><span class="sxs-lookup"><span data-stu-id="8ad82-133">Create an isolated and highly secure environment for your applications</span></span>
- <span data-ttu-id="8ad82-134">使用其中一種[連線選項](/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti)將 VM 連線至內部部署網路</span><span class="sxs-lookup"><span data-stu-id="8ad82-134">Connect your VM to your on-premises network using one of several [connectivity options](/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti)</span></span>
- <span data-ttu-id="8ad82-135">使用 [ExpressRoute](https://azure.microsoft.com/services/expressroute/) 將您的虛擬機器整合到內部部署網路</span><span class="sxs-lookup"><span data-stu-id="8ad82-135">Integrate your virtual machine into your on-premises network using [ExpressRoute](https://azure.microsoft.com/services/expressroute/)</span></span>

<span data-ttu-id="8ad82-136">請參閱[虛擬網路文件](/azure/virtual-network/)以開始使用</span><span class="sxs-lookup"><span data-stu-id="8ad82-136">To get started, see the [Virtual Network documentation](/azure/virtual-network/)</span></span>

### <a name="active-directory"></a><span data-ttu-id="8ad82-137">Active Directory</span><span class="sxs-lookup"><span data-stu-id="8ad82-137">Active Directory</span></span>
<span data-ttu-id="8ad82-138">許多應用程式使用 Active Directory 進行驗證和身分識別管理。</span><span class="sxs-lookup"><span data-stu-id="8ad82-138">Many applications use Active Directory for authentication and identity management.</span></span>

- <span data-ttu-id="8ad82-139">Azure AD Connect 可讓您整合內部部署目錄與 Azure Active Directory。</span><span class="sxs-lookup"><span data-stu-id="8ad82-139">Azure AD Connect enables you to integrate your on-premises directories with Azure Active Directory.</span></span> <span data-ttu-id="8ad82-140">若要開始，請參閱[整合您的內部部署目錄與 Azure Active Directory](/azure/active-directory/connect/active-directory-aadconnect)。</span><span class="sxs-lookup"><span data-stu-id="8ad82-140">To get started, see [Integrate your on-premises directories with Azure Active Directory](/azure/active-directory/connect/active-directory-aadconnect).</span></span>
- <span data-ttu-id="8ad82-141">或者，[ExpressRoute](https://azure.microsoft.com/services/expressroute/) 可讓應用程式存取您的內部部署 Active Directory。</span><span class="sxs-lookup"><span data-stu-id="8ad82-141">Alternatively, [ExpressRoute](https://azure.microsoft.com/services/expressroute/) enables your application to access your on-premises Active Directory.</span></span>

### <a name="sql-databases"></a><span data-ttu-id="8ad82-142">SQL Database</span><span class="sxs-lookup"><span data-stu-id="8ad82-142">SQL Databases</span></span>

<span data-ttu-id="8ad82-143">如果您的應用程式正在使用內部部署資料庫，則預設應用程式將無法與其通話。</span><span class="sxs-lookup"><span data-stu-id="8ad82-143">If your application is using an on-premises database, your app will not be able to talk to it by default.</span></span> <span data-ttu-id="8ad82-144">您可以：</span><span class="sxs-lookup"><span data-stu-id="8ad82-144">You can either:</span></span>

- <span data-ttu-id="8ad82-145">設定混合式網路，讓應用程式存取您在內部部署執行的資料庫。</span><span class="sxs-lookup"><span data-stu-id="8ad82-145">Configure a hybrid network that enables your application to access your database running on-premises.</span></span>
- <span data-ttu-id="8ad82-146">將資料庫移轉至 Azure。</span><span class="sxs-lookup"><span data-stu-id="8ad82-146">Migrate your database to the Azure.</span></span> <span data-ttu-id="8ad82-147">如需詳細資訊，請參閱[將您的 SQL Server 資料庫移轉至 Azure](sql.md)。</span><span class="sxs-lookup"><span data-stu-id="8ad82-147">For more information, see [Migrate your SQL Server database to Azure](sql.md).</span></span>

### <a name="high-availability-and-scalability"></a><span data-ttu-id="8ad82-148">高可用性和延展性</span><span class="sxs-lookup"><span data-stu-id="8ad82-148">High Availability and Scalability</span></span>

#### <a name="virtual-machine-scale-sets"></a><span data-ttu-id="8ad82-149">虛擬機器擴展集</span><span class="sxs-lookup"><span data-stu-id="8ad82-149">Virtual Machine Scale Sets</span></span>
<span data-ttu-id="8ad82-150">若您想要確定應用程式為高可用性且可以調整，可以將 VM 映像移轉到 Azure 虛擬機器擴展集來改善應用程式的可用性和延展性。</span><span class="sxs-lookup"><span data-stu-id="8ad82-150">You want to make sure that your application is highly available and can scale, migrate your VM image to an Azure Virtual Machine Scale Set to improve the availability and scalability of your application.</span></span> <span data-ttu-id="8ad82-151">VM 擴展集提供使用已設定之現有 VM 的功能，或設定組建管線以使用您的應用程式建立映射。</span><span class="sxs-lookup"><span data-stu-id="8ad82-151">VM Scale Sets provide the ability to use an existing VM you've already configured or set up a build pipeline to build an image with your application.</span></span>

<span data-ttu-id="8ad82-152">若要開始，請參閱[在虛擬機器擴展集上部署您的應用程式](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)。</span><span class="sxs-lookup"><span data-stu-id="8ad82-152">To get started, see [Deploy your application on virtual machine scale sets](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app).</span></span>

#### <a name="centralized-logging"></a><span data-ttu-id="8ad82-153">集中式記錄</span><span class="sxs-lookup"><span data-stu-id="8ad82-153">Centralized Logging</span></span>
<span data-ttu-id="8ad82-154">在多個執行個體中執行應用程式時，請考慮將您的記錄儲存在集中位置，如 [Azure 儲存體](/azure/storage/)。</span><span class="sxs-lookup"><span data-stu-id="8ad82-154">When running your application across multiple instances, consider storing your logs in a centralized location such as [Azure Storage](/azure/storage/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="8ad82-155">接下來的步驟</span><span class="sxs-lookup"><span data-stu-id="8ad82-155">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8ad82-156">將 SQL Server 資料庫移轉至 Azure</span><span class="sxs-lookup"><span data-stu-id="8ad82-156">Migrate a SQL Server database to Azure</span></span>](sql.md)

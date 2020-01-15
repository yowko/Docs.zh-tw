---
title: 在網際網路資訊服務中裝載
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
ms.openlocfilehash: 108048f6bdd2c02a67e331bd7b07b724d0e86527
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2020
ms.locfileid: "75963793"
---
# <a name="host-in-internet-information-services"></a><span data-ttu-id="0874a-102">Internet Information Services 中的主機</span><span class="sxs-lookup"><span data-stu-id="0874a-102">Host in Internet Information Services</span></span>

<span data-ttu-id="0874a-103">裝載 Windows Communication Foundation （WCF）服務的一個選項是在 Internet Information Services （IIS）應用程式中。</span><span class="sxs-lookup"><span data-stu-id="0874a-103">One option for hosting Windows Communication Foundation (WCF) services is inside of an Internet Information Services (IIS) application.</span></span> <span data-ttu-id="0874a-104">此裝載模型類似于 ASP.NET 和 ASP.NET Web 服務（.ASMX） Web 服務所使用的模型。</span><span class="sxs-lookup"><span data-stu-id="0874a-104">This hosting model is similar to the model used by ASP.NET and ASP.NET Web services (ASMX) Web Services.</span></span>

## <a name="versions-of-iis"></a><span data-ttu-id="0874a-105">IIS 的版本</span><span class="sxs-lookup"><span data-stu-id="0874a-105">Versions of IIS</span></span>

<span data-ttu-id="0874a-106">WCF 可以裝載于下列作業系統上的下列 IIS 版本：</span><span class="sxs-lookup"><span data-stu-id="0874a-106">WCF can be hosted on the following versions of IIS on the following operating systems:</span></span>

- <span data-ttu-id="0874a-107">[!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] 上的 IIS 5.1。</span><span class="sxs-lookup"><span data-stu-id="0874a-107">IIS 5.1 on [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)].</span></span> <span data-ttu-id="0874a-108">此環境適用于稍後部署在伺服器作業系統（例如 Windows Server 2003）上的 IIS 裝載應用程式的設計和開發。</span><span class="sxs-lookup"><span data-stu-id="0874a-108">This environment is useful for the design and development of IIS-hosted applications that are later deployed on a server operating system such as Windows Server 2003.</span></span>

- <span data-ttu-id="0874a-109">Windows Server 2003 上的 IIS 6.0。</span><span class="sxs-lookup"><span data-stu-id="0874a-109">IIS 6.0 on Windows Server 2003.</span></span> <span data-ttu-id="0874a-110">IIS 6.0 提供先進的進程模型，可提供改良的擴充性、可靠性和應用程式隔離。</span><span class="sxs-lookup"><span data-stu-id="0874a-110">IIS 6.0 provides an advanced process model that offers improved scalability, reliability, and application isolation.</span></span> <span data-ttu-id="0874a-111">此環境適用于以獨佔方式使用 HTTP 通訊的 WCF 服務生產部署。</span><span class="sxs-lookup"><span data-stu-id="0874a-111">This environment is suitable for production deployment of WCF services that use HTTP communication exclusively.</span></span>

- <span data-ttu-id="0874a-112">Windows Vista 和 Windows Server 2008 上的 IIS 7.0。</span><span class="sxs-lookup"><span data-stu-id="0874a-112">IIS 7.0 on Windows Vista and Windows Server 2008.</span></span> <span data-ttu-id="0874a-113">IIS 7.0 提供與 IIS 6.0 相同的先進進程模型，但使用 Windows 進程啟用服務（WAS）允許透過 HTTP 以外的通訊協定進行啟用和網路通訊。</span><span class="sxs-lookup"><span data-stu-id="0874a-113">IIS 7.0 provides the same advanced process model as IIS 6.0, but uses the Windows Process Activation Service (WAS) to allow activation and network communication over protocols other than HTTP.</span></span> <span data-ttu-id="0874a-114">此環境適用于透過 WCF 支援的任何網路通訊協定進行通訊的 WCF 服務開發（包括 HTTP、net.tcp、net.pipe 和 net.tcp）。</span><span class="sxs-lookup"><span data-stu-id="0874a-114">This environment is suitable for the development of WCF services that communicate over any network protocol supported by WCF (including HTTP, net.tcp, net.pipe, and net.msmq).</span></span> <span data-ttu-id="0874a-115">如需 WAS 的詳細資訊，請參閱[在 Windows 進程啟用服務中裝載](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)。</span><span class="sxs-lookup"><span data-stu-id="0874a-115">For more information about WAS, see [Hosting in Windows Process Activation Service](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).</span></span>

- <span data-ttu-id="0874a-116">[Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff384253(v=azure.10))適用于 IIS 7.0 和 Windows 進程啟用服務（WAS），以提供豐富的應用程式裝載環境來 NET4 WCF 和 WF 服務。</span><span class="sxs-lookup"><span data-stu-id="0874a-116">[Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff384253(v=azure.10)) works with IIS 7.0 and Windows Process Activation Service (WAS) to provide a rich application hosting environment for NET4 WCF and WF services.</span></span> <span data-ttu-id="0874a-117">這些優點包括處理序生命週期管理、處理序回收、共用裝載、快速失敗保護、處理序損壞、隨選啟動和健康監視。</span><span class="sxs-lookup"><span data-stu-id="0874a-117">These benefits include process life-cycle management, process recycling, shared hosting, rapid failure protection, process orphaning, on-demand activation, and health monitoring.</span></span> <span data-ttu-id="0874a-118">如需詳細資訊，請參閱[Appfabric 裝載功能](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))和[appfabric 裝載概念](https://docs.microsoft.com/previous-versions/appfabric/ee677371(v=azure.10))。</span><span class="sxs-lookup"><span data-stu-id="0874a-118">For detailed information, see [AppFabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10)) and [AppFabric Hosting Concepts](https://docs.microsoft.com/previous-versions/appfabric/ee677371(v=azure.10)).</span></span>

## <a name="benefits-of-iis-hosting"></a><span data-ttu-id="0874a-119">IIS 裝載的優點</span><span class="sxs-lookup"><span data-stu-id="0874a-119">Benefits of IIS hosting</span></span>

<span data-ttu-id="0874a-120">在 IIS 中裝載 WCF 服務有數個優點：</span><span class="sxs-lookup"><span data-stu-id="0874a-120">Hosting WCF services in IIS has several benefits:</span></span>

- <span data-ttu-id="0874a-121">裝載于 IIS 中的 WCF 服務會像任何其他類型的 IIS 應用程式一樣進行部署和管理，包括 ASP.NET 應用程式和 .ASMX。</span><span class="sxs-lookup"><span data-stu-id="0874a-121">WCF services hosted in IIS are deployed and managed like any other type of IIS application, including ASP.NET applications and ASMX.</span></span>

- <span data-ttu-id="0874a-122">IIS 提供處理程序啟動、健康情況管理以及回收功能，以提升裝載應用程式的可靠性。</span><span class="sxs-lookup"><span data-stu-id="0874a-122">IIS provides process activation, health management, and recycling capabilities to increase the reliability of hosted applications.</span></span>

- <span data-ttu-id="0874a-123">如同 ASP.NET，裝載在 ASP.NET 中的 WCF 服務可以利用 ASP.NET 共用裝載模型，其中多個應用程式位於共同的工作者進程中，以改善伺服器密度和擴充性。</span><span class="sxs-lookup"><span data-stu-id="0874a-123">Like ASP.NET, WCF services hosted in ASP.NET can take advantage of the ASP.NET shared hosting model where multiple applications reside in a common worker process for improved server density and scalability.</span></span>

- <span data-ttu-id="0874a-124">裝載于 IIS 的 WCF 服務會使用與 ASP.NET 2.0 相同的動態編譯模型，這可簡化託管服務的開發和部署。</span><span class="sxs-lookup"><span data-stu-id="0874a-124">WCF services hosted in IIS use the same dynamic compilation model as ASP.NET 2.0, which simplifies development and deployment of hosted services.</span></span>

<span data-ttu-id="0874a-125">在決定要在 IIS 中裝載 WCF 服務時，請務必記住 IIS 5.1 和 IIS 6.0 僅限於 HTTP 通訊。</span><span class="sxs-lookup"><span data-stu-id="0874a-125">When deciding to host WCF services in IIS, it is important to remember that IIS 5.1 and IIS 6.0 are limited to HTTP communication only.</span></span> <span data-ttu-id="0874a-126">如需選擇裝載環境的詳細資訊，請參閱[裝載服務](../../../../docs/framework/wcf/hosting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="0874a-126">For more information about choosing a hosting environment, see [Hosting Services](../../../../docs/framework/wcf/hosting-services.md).</span></span>

## <a name="deploy-an-iis-hosted-wcf-service"></a><span data-ttu-id="0874a-127">部署裝載于 IIS 的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="0874a-127">Deploy an IIS-hosted WCF service</span></span>

<span data-ttu-id="0874a-128">開發和部署 IIS 裝載的 WCF 服務包含下列工作：</span><span class="sxs-lookup"><span data-stu-id="0874a-128">Developing and deploying an IIS-hosted WCF service consists of the following tasks:</span></span>

- <span data-ttu-id="0874a-129">請確定已正確安裝及註冊 IIS、ASP.NET、WCF 和 WCF HTTP 啟用元件。</span><span class="sxs-lookup"><span data-stu-id="0874a-129">Ensure that IIS, ASP.NET, WCF, and the WCF HTTP activation component are correctly installed and registered.</span></span>

- <span data-ttu-id="0874a-130">建立新的 IIS 應用程式，或重複使用現有的 ASP.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0874a-130">Create a new IIS application, or reuse an existing ASP.NET application.</span></span>

- <span data-ttu-id="0874a-131">建立 WCF 服務的 .svc 檔案。</span><span class="sxs-lookup"><span data-stu-id="0874a-131">Create a .svc file for the WCF service.</span></span>

- <span data-ttu-id="0874a-132">將服務實作部署到 IIS 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0874a-132">Deploy the service implementation to the IIS application.</span></span>

- <span data-ttu-id="0874a-133">設定 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="0874a-133">Configure the WCF service.</span></span>

<span data-ttu-id="0874a-134">如需每項工作的討論，請參閱[部署 Internet Information Services 託管的 WCF 服務](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)。</span><span class="sxs-lookup"><span data-stu-id="0874a-134">For a discussion of each of these tasks, see [Deploying an Internet Information Services-Hosted WCF Service](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).</span></span>

## <a name="wcf-services-and-aspnet"></a><span data-ttu-id="0874a-135">WCF 服務和 ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0874a-135">WCF services and ASP.NET</span></span>

<span data-ttu-id="0874a-136">WCF 服務可以與 ASP.NET 並存裝載，或在 ASP.NET 相容性模式中裝載，服務可以充分利用 ASP.NET Web 應用程式平臺所提供的功能。</span><span class="sxs-lookup"><span data-stu-id="0874a-136">WCF services can be hosted either side-by-side with ASP.NET or in ASP.NET Compatibility Mode in which services can take full advantage of features provided by the ASP.NET Web application platform.</span></span> <span data-ttu-id="0874a-137">如需這些功能的討論，請參閱[WCF 服務和 ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)。</span><span class="sxs-lookup"><span data-stu-id="0874a-137">For a discussion of these features, see [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0874a-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="0874a-138">See also</span></span>

- [<span data-ttu-id="0874a-139">使用 ServiceHostFactory 擴充裝載</span><span class="sxs-lookup"><span data-stu-id="0874a-139">Extending Hosting Using ServiceHostFactory</span></span>](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)
- [<span data-ttu-id="0874a-140">部署已裝載 Internet Information Services 的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="0874a-140">Deploying an Internet Information Services-Hosted WCF Service</span></span>](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)
- [<span data-ttu-id="0874a-141">WCF 服務與 ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0874a-141">WCF Services and ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [<span data-ttu-id="0874a-142">Internet Information Services 裝載最佳做法</span><span class="sxs-lookup"><span data-stu-id="0874a-142">Internet Information Services Hosting Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
- [<span data-ttu-id="0874a-143">設定 Internet Information Services 7.0 for Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="0874a-143">Configuring Internet Information Services 7.0 for Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/feature-details/configuring-iis-for-wcf.md)
- <span data-ttu-id="0874a-144">[Windows Server AppFabric 裝載功能](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="0874a-144">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>

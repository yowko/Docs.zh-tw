---
title: 使用者入門 Tutorial1
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF [WCF], getting started
- Windows Communication Foundation [WCF], getting started
- getting started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
caps.latest.revision: 47
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2dbf3ddb903600df6094c8486fda7183eac2abe7
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="getting-started-tutorial"></a><span data-ttu-id="fce34-102">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="fce34-102">Getting Started Tutorial</span></span>
<span data-ttu-id="fce34-103">本節所包含的主題主要是讓您快速獲得 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 程式設計經驗。</span><span class="sxs-lookup"><span data-stu-id="fce34-103">The topics contained in this section are intended to give you quick exposure to the [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] programming experience.</span></span> <span data-ttu-id="fce34-104">每個主題已設計成依本主題結尾的清單順序完成。</span><span class="sxs-lookup"><span data-stu-id="fce34-104">They are designed to be completed in the order of the list at the bottom of this topic.</span></span> <span data-ttu-id="fce34-105">完成這個入門課程之後，您將對建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務與用戶端應用程式所需的步驟有初步的了解。</span><span class="sxs-lookup"><span data-stu-id="fce34-105">Working through this tutorial gives you an introductory understanding of the steps required to create [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service and client applications.</span></span> <span data-ttu-id="fce34-106">服務會公開一個或多個端點，而其中每個端點都會公開一項或多項服務作業。</span><span class="sxs-lookup"><span data-stu-id="fce34-106">A service exposes one or more endpoints, each of which exposes one or more service operations.</span></span> <span data-ttu-id="fce34-107">*端點*服務的指定位置可以找到服務，位址的繫結，其中包含說明定義功能的合約與服務，用戶端必須之間的通訊資訊提供服務給其用戶端。</span><span class="sxs-lookup"><span data-stu-id="fce34-107">The *endpoint* of a service specifies an address where the service can be found, a binding that contains the information that describes how a client must communicate with the service, and a contract that defines the functionality provided by the service to its clients.</span></span>  
  
 <span data-ttu-id="fce34-108">在您逐步執行本教學課程中各主題的程序之後，您將會有執行中的服務和呼叫服務的用戶端。</span><span class="sxs-lookup"><span data-stu-id="fce34-108">After you work through the sequence of topics in this tutorial, you will have a running service, and a client that calls the service.</span></span> <span data-ttu-id="fce34-109">前面三個主題說明如何定義服務合約、如何實作服務合約以及如何裝載服務。</span><span class="sxs-lookup"><span data-stu-id="fce34-109">The first three topics describe how to define a service contract, how to implement the service contract, and how to host the service.</span></span> <span data-ttu-id="fce34-110">建立的這個服務是在主控台應用程式中自我裝載的服務。</span><span class="sxs-lookup"><span data-stu-id="fce34-110">The service that is created is self-hosted within a console application.</span></span> <span data-ttu-id="fce34-111">服務也可以在網際網路資訊服務 (IIS) 之下進行裝載。</span><span class="sxs-lookup"><span data-stu-id="fce34-111">Services can also be hosted under Internet Information Services (IIS).</span></span> <span data-ttu-id="fce34-112">如需如何執行這項操作的詳細資訊，請參閱[How to： 將 WCF 服務裝載於 IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)。</span><span class="sxs-lookup"><span data-stu-id="fce34-112">For more information about how to do this, see [How to: Host a WCF Service in IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span> <span data-ttu-id="fce34-113">服務是在程式碼中進行設定的，但是也可以在組態檔中設定。</span><span class="sxs-lookup"><span data-stu-id="fce34-113">The service is configured in code; however, services can also be configured within a configuration file.</span></span> <span data-ttu-id="fce34-114">如需有關使用組態檔，請參閱[設定服務使用組態檔](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)。</span><span class="sxs-lookup"><span data-stu-id="fce34-114">For more information about using a configuration file see [Configuring Services Using Configuration Files](../../../docs/framework/wcf/configuring-services-using-configuration-files.md).</span></span>  
  
 <span data-ttu-id="fce34-115">後面三個主題將說明如何建立用戶端 Proxy、設定用戶端應用程式，以及使用用戶端 Proxy 來呼叫服務所公開的服務作業。</span><span class="sxs-lookup"><span data-stu-id="fce34-115">The next three topics describe how to create a client proxy, configure the client application, and use the client proxy to call service operation exposed by the service.</span></span> <span data-ttu-id="fce34-116">服務會發行定義用戶端應用程式與服務進行通訊所需之資訊的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="fce34-116">Services publish metadata that define the information a client application needs to communicate with the service.</span></span> [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]<span data-ttu-id="fce34-117"> 會自動化存取這個中繼資料的程序，並用它來建構和設定服務的用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="fce34-117"> automates the process of accessing this metadata and uses it to construct and configure the client application for the service.</span></span> <span data-ttu-id="fce34-118">如果您不使用[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]，您可以使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來建構和設定服務的用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="fce34-118">If you are not using [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], you can use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to construct and configure the client application for the service.</span></span>  
  
 <span data-ttu-id="fce34-119">本節中的所有主題都假設您是使用 Visual Studio 2011 做為開發環境。</span><span class="sxs-lookup"><span data-stu-id="fce34-119">All of the topics in this section assume you are using Visual Studio 2011 as the development environment.</span></span> <span data-ttu-id="fce34-120">如果您使用其他開發環境，略過 Visual Studio 特定指示。</span><span class="sxs-lookup"><span data-stu-id="fce34-120">If you are using another development environment, ignore the Visual Studio specific instructions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fce34-121">如果您正在[!INCLUDE[wv](../../../includes/wv-md.md)]或更新版本的 Windows 作業系統，您必須移至 [開始] 功能表，然後以滑鼠右鍵按一下 Visual Studio 2011 並選取來啟動 Visual Studio**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="fce34-121">If you are running [!INCLUDE[wv](../../../includes/wv-md.md)] or later versions of the Windows operating system, you must start Visual Studio by going to the Start menu and right clicking Visual Studio 2011 and selecting **Run as Administrator**.</span></span> <span data-ttu-id="fce34-122">若要一律以您可以建立快速鍵，以滑鼠右鍵按一下該快速鍵，選取屬性，選取系統管理員身分啟動 Visual Studio 2011**相容性**索引標籤，然後檢查**以系統管理員身分執行此程式**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="fce34-122">To always launch Visual Studio 2011 as an administrator you can create a short cut, right click the short cut, select properties, select the **Compatibility** tab, and check the **Run this program as an administrator** checkbox.</span></span> <span data-ttu-id="fce34-123">當您使用此快速鍵啟動 Visual Studio 2011 時，以後就會固定以系統管理員身分執行。</span><span class="sxs-lookup"><span data-stu-id="fce34-123">When you start Visual Studio 2011 with this shortcut, it will always run as administrator.</span></span>  
  
 <span data-ttu-id="fce34-124">範例應用程式會將下載到您的硬碟和執行，請參閱中的主題[Windows Communication Foundation 範例](http://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)。</span><span class="sxs-lookup"><span data-stu-id="fce34-124">For sample applications that can be downloaded to your hard disk and run, see the topics in [Windows Communication Foundation Samples](http://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91).</span></span> <span data-ttu-id="fce34-125">如本主題中，特別是，請參閱[入門](../../../docs/framework/wcf/samples/getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="fce34-125">For this topic, see, in particular, the [Getting Started](../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
 <span data-ttu-id="fce34-126">如需建立服務和用戶端相關的深入資訊，請參閱[基本 WCF 程式設計](../../../docs/framework/wcf/basic-wcf-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="fce34-126">For more in-depth information about creating services and clients, see [Basic WCF Programming](../../../docs/framework/wcf/basic-wcf-programming.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fce34-127">本節內容</span><span class="sxs-lookup"><span data-stu-id="fce34-127">In This Section</span></span>  
 [<span data-ttu-id="fce34-128">如何：定義服務合約</span><span class="sxs-lookup"><span data-stu-id="fce34-128">How to: Define a Service Contract</span></span>](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 <span data-ttu-id="fce34-129">說明如何利用使用者定義的介面來建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 合約。</span><span class="sxs-lookup"><span data-stu-id="fce34-129">Describes how to create a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] contract using a user-defined interface.</span></span> <span data-ttu-id="fce34-130">合約會定義服務所公開的功能。</span><span class="sxs-lookup"><span data-stu-id="fce34-130">The contract defines the functionality exposed by the service.</span></span>  
  
 [<span data-ttu-id="fce34-131">如何：履行服務合約</span><span class="sxs-lookup"><span data-stu-id="fce34-131">How to: Implement a Service Contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 <span data-ttu-id="fce34-132">說明如何實作服務合約。</span><span class="sxs-lookup"><span data-stu-id="fce34-132">Describes how to implement a service contract.</span></span> <span data-ttu-id="fce34-133">一旦定義了合約，就必須透過服務類別加以實作。</span><span class="sxs-lookup"><span data-stu-id="fce34-133">Once a contract is define, it must be implemented with a service class.</span></span>  
  
 [<span data-ttu-id="fce34-134">如何：裝載及執行基本服務</span><span class="sxs-lookup"><span data-stu-id="fce34-134">How to: Host and Run a Basic Service</span></span>](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md)  
 <span data-ttu-id="fce34-135">說明如何在程式碼中設定服務的端點，以及如何在主控台應用程式中裝載服務。</span><span class="sxs-lookup"><span data-stu-id="fce34-135">Describes how to configure an endpoint for the service in code and how to host the service in a console application.</span></span> <span data-ttu-id="fce34-136">如果要成為作用中的服務，必須在執行階段環境中設定與裝載服務。</span><span class="sxs-lookup"><span data-stu-id="fce34-136">To become active, a service must be configured and hosted within a run-time environment.</span></span> <span data-ttu-id="fce34-137">此環境會建立服務並控制其內容與存留期。</span><span class="sxs-lookup"><span data-stu-id="fce34-137">This environment creates the service and controls its context and lifetime.</span></span>  
  
 [<span data-ttu-id="fce34-138">如何：建立用戶端</span><span class="sxs-lookup"><span data-stu-id="fce34-138">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 <span data-ttu-id="fce34-139">說明如何從 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務擷取用來建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端 Proxy 的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="fce34-139">Describes how to retrieve metadata used to create a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client proxy from a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="fce34-140">這個程序會使用 Visual Studio 2011 中的 [加入服務參考] 功能。</span><span class="sxs-lookup"><span data-stu-id="fce34-140">This process uses the Add Service Reference functionality within Visual Studio 2011.</span></span>  
  
 [<span data-ttu-id="fce34-141">如何：設定用戶端</span><span class="sxs-lookup"><span data-stu-id="fce34-141">How to: Configure a Client</span></span>](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)  
 <span data-ttu-id="fce34-142">說明如何設定 WCF 用戶端。設定用戶端時，需要指定用戶端用來存取服務的端點。</span><span class="sxs-lookup"><span data-stu-id="fce34-142">Describes how to configure a WCF client Configuring the client requires specifying the endpoint that the client uses to access the service.</span></span>  
  
 [<span data-ttu-id="fce34-143">如何：使用用戶端</span><span class="sxs-lookup"><span data-stu-id="fce34-143">How to: Use a Client</span></span>](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)  
 <span data-ttu-id="fce34-144">說明如何使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端 Proxy 來叫用服務作業。</span><span class="sxs-lookup"><span data-stu-id="fce34-144">Describes how to use the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client proxy to invoke service operations.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="fce34-145">參考資料</span><span class="sxs-lookup"><span data-stu-id="fce34-145">Reference</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
  
 <xref:System.ServiceModel.OperationContractAttribute>  
  
## <a name="related-sections"></a><span data-ttu-id="fce34-146">相關章節</span><span class="sxs-lookup"><span data-stu-id="fce34-146">Related Sections</span></span>  
 [<span data-ttu-id="fce34-147">Windows Communication Foundation 範例</span><span class="sxs-lookup"><span data-stu-id="fce34-147">Windows Communication Foundation Samples</span></span>](http://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)  
  
 [<span data-ttu-id="fce34-148">基本程式設計週期</span><span class="sxs-lookup"><span data-stu-id="fce34-148">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
## <a name="see-also"></a><span data-ttu-id="fce34-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fce34-149">See Also</span></span>  
 [<span data-ttu-id="fce34-150">概念性概觀</span><span class="sxs-lookup"><span data-stu-id="fce34-150">Conceptual Overview</span></span>](../../../docs/framework/wcf/conceptual-overview.md)  
 [<span data-ttu-id="fce34-151">文件指南</span><span class="sxs-lookup"><span data-stu-id="fce34-151">Guide to the Documentation</span></span>](../../../docs/framework/wcf/guide-to-the-documentation.md)  
 [<span data-ttu-id="fce34-152">什麼是 Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="fce34-152">What Is Windows Communication Foundation</span></span>](../../../docs/framework/wcf/whats-wcf.md)  
 [<span data-ttu-id="fce34-153">WCF 功能詳細資料</span><span class="sxs-lookup"><span data-stu-id="fce34-153">WCF Feature Details</span></span>](../../../docs/framework/wcf/feature-details/index.md)

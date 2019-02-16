---
title: 開始使用 Tutorial1
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], getting started
- Windows Communication Foundation [WCF], getting started
- getting started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: 2bd0b7e0d927e53f70515cfa124034a4cacc5ce7
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/16/2019
ms.locfileid: "56332243"
---
# <a name="getting-started-tutorial"></a><span data-ttu-id="4df28-102">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="4df28-102">Getting Started Tutorial</span></span>
<span data-ttu-id="4df28-103">在本節中所包含的主題旨在讓您快速獲得至 Windows Communication Foundation (WCF) 程式設計經驗。</span><span class="sxs-lookup"><span data-stu-id="4df28-103">The topics contained in this section are intended to give you quick exposure to the Windows Communication Foundation (WCF) programming experience.</span></span> <span data-ttu-id="4df28-104">每個主題已設計成依本主題結尾的清單順序完成。</span><span class="sxs-lookup"><span data-stu-id="4df28-104">They are designed to be completed in the order of the list at the bottom of this topic.</span></span> <span data-ttu-id="4df28-105">循序完成本教學課程可讓您建立 WCF 服務和用戶端應用程式所需的步驟大致了解。</span><span class="sxs-lookup"><span data-stu-id="4df28-105">Working through this tutorial gives you an introductory understanding of the steps required to create WCF service and client applications.</span></span> <span data-ttu-id="4df28-106">服務會公開一個或多個端點，而其中每個端點都會公開一項或多項服務作業。</span><span class="sxs-lookup"><span data-stu-id="4df28-106">A service exposes one or more endpoints, each of which exposes one or more service operations.</span></span> <span data-ttu-id="4df28-107">*端點*服務的指定位置可以找到服務，包含的資訊，說明服務與合約定義的功能，用戶端必須之間的通訊的繫結位址服務提供給其用戶端。</span><span class="sxs-lookup"><span data-stu-id="4df28-107">The *endpoint* of a service specifies an address where the service can be found, a binding that contains the information that describes how a client must communicate with the service, and a contract that defines the functionality provided by the service to its clients.</span></span>

 <span data-ttu-id="4df28-108">在您逐步執行本教學課程中各主題的程序之後，您將會有執行中的服務和呼叫服務的用戶端。</span><span class="sxs-lookup"><span data-stu-id="4df28-108">After you work through the sequence of topics in this tutorial, you will have a running service, and a client that calls the service.</span></span> <span data-ttu-id="4df28-109">前面三個主題說明如何定義服務合約、如何實作服務合約以及如何裝載服務。</span><span class="sxs-lookup"><span data-stu-id="4df28-109">The first three topics describe how to define a service contract, how to implement the service contract, and how to host the service.</span></span> <span data-ttu-id="4df28-110">建立的這個服務是在主控台應用程式中自我裝載的服務。</span><span class="sxs-lookup"><span data-stu-id="4df28-110">The service that is created is self-hosted within a console application.</span></span> <span data-ttu-id="4df28-111">服務也可以在網際網路資訊服務 (IIS) 之下進行裝載。</span><span class="sxs-lookup"><span data-stu-id="4df28-111">Services can also be hosted under Internet Information Services (IIS).</span></span> <span data-ttu-id="4df28-112">如需這個做法的詳細資訊，請參閱[如何：將 WCF 服務裝載於 IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)。</span><span class="sxs-lookup"><span data-stu-id="4df28-112">For more information about how to do this, see [How to: Host a WCF Service in IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span> <span data-ttu-id="4df28-113">服務是在程式碼中進行設定的，但是也可以在組態檔中設定。</span><span class="sxs-lookup"><span data-stu-id="4df28-113">The service is configured in code; however, services can also be configured within a configuration file.</span></span> <span data-ttu-id="4df28-114">如需使用組態檔的詳細資訊，請參閱[設定服務使用組態檔](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)。</span><span class="sxs-lookup"><span data-stu-id="4df28-114">For more information about using a configuration file see [Configuring Services Using Configuration Files](../../../docs/framework/wcf/configuring-services-using-configuration-files.md).</span></span>

 <span data-ttu-id="4df28-115">後面三個主題將說明如何建立用戶端 Proxy、設定用戶端應用程式，以及使用用戶端 Proxy 來呼叫服務所公開的服務作業。</span><span class="sxs-lookup"><span data-stu-id="4df28-115">The next three topics describe how to create a client proxy, configure the client application, and use the client proxy to call service operation exposed by the service.</span></span> <span data-ttu-id="4df28-116">服務會發行定義用戶端應用程式與服務進行通訊所需之資訊的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4df28-116">Services publish metadata that define the information a client application needs to communicate with the service.</span></span> <span data-ttu-id="4df28-117">Visual Studio 2012 會存取此中繼資料的程序自動化，並使用它來建構和設定服務的用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="4df28-117">Visual Studio 2012 automates the process of accessing this metadata and uses it to construct and configure the client application for the service.</span></span> <span data-ttu-id="4df28-118">如果您不使用 Visual Studio 2012，您可以使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來建構和設定服務的用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="4df28-118">If you are not using Visual Studio 2012, you can use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to construct and configure the client application for the service.</span></span>

<span data-ttu-id="4df28-119">在本節中的主題會假設您使用 Visual Studio 作為開發環境。</span><span class="sxs-lookup"><span data-stu-id="4df28-119">The topics in this section assume you are using Visual Studio as the development environment.</span></span> <span data-ttu-id="4df28-120">如果您使用另一個開發環境，請略過 Visual Studio 特定指示。</span><span class="sxs-lookup"><span data-stu-id="4df28-120">If you are using another development environment, ignore the Visual Studio-specific instructions.</span></span>

<span data-ttu-id="4df28-121">範例應用程式，可以下載到您的硬碟並執行，請參閱中的主題[Windows Communication Foundation (WCF) 範例](./samples/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4df28-121">For sample applications that can be downloaded to your hard disk and run, see the topics in [Windows Communication Foundation (WCF) samples](./samples/index.md).</span></span> <span data-ttu-id="4df28-122">本主題中，特別是，請參閱[開始使用](../../../docs/framework/wcf/samples/getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="4df28-122">For this topic, see, in particular, the [Getting Started](../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>

<span data-ttu-id="4df28-123">如需建立服務和用戶端的詳細深入資訊，請參閱 <<c0> [ 基本 WCF 程式設計](../../../docs/framework/wcf/basic-wcf-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="4df28-123">For more in-depth information about creating services and clients, see [Basic WCF Programming](../../../docs/framework/wcf/basic-wcf-programming.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="4df28-124">本節內容</span><span class="sxs-lookup"><span data-stu-id="4df28-124">In This Section</span></span>
 [<span data-ttu-id="4df28-125">如何：定義服務合約</span><span class="sxs-lookup"><span data-stu-id="4df28-125">How to: Define a Service Contract</span></span>](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)

 <span data-ttu-id="4df28-126">描述如何建立 WCF 合約使用使用者定義的介面。</span><span class="sxs-lookup"><span data-stu-id="4df28-126">Describes how to create a WCF contract using a user-defined interface.</span></span> <span data-ttu-id="4df28-127">合約會定義服務所公開的功能。</span><span class="sxs-lookup"><span data-stu-id="4df28-127">The contract defines the functionality exposed by the service.</span></span>

 [<span data-ttu-id="4df28-128">如何：實作服務合約</span><span class="sxs-lookup"><span data-stu-id="4df28-128">How to: Implement a Service Contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)

 <span data-ttu-id="4df28-129">說明如何實作服務合約。</span><span class="sxs-lookup"><span data-stu-id="4df28-129">Describes how to implement a service contract.</span></span> <span data-ttu-id="4df28-130">一旦定義了合約，就必須透過服務類別加以實作。</span><span class="sxs-lookup"><span data-stu-id="4df28-130">Once a contract is define, it must be implemented with a service class.</span></span>

 [<span data-ttu-id="4df28-131">如何：裝載和執行基本的服務</span><span class="sxs-lookup"><span data-stu-id="4df28-131">How to: Host and Run a Basic Service</span></span>](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md)

 <span data-ttu-id="4df28-132">說明如何在程式碼中設定服務的端點，以及如何在主控台應用程式中裝載服務。</span><span class="sxs-lookup"><span data-stu-id="4df28-132">Describes how to configure an endpoint for the service in code and how to host the service in a console application.</span></span> <span data-ttu-id="4df28-133">如果要成為作用中的服務，必須在執行階段環境中設定與裝載服務。</span><span class="sxs-lookup"><span data-stu-id="4df28-133">To become active, a service must be configured and hosted within a run-time environment.</span></span> <span data-ttu-id="4df28-134">此環境會建立服務並控制其內容與存留期。</span><span class="sxs-lookup"><span data-stu-id="4df28-134">This environment creates the service and controls its context and lifetime.</span></span>

 [<span data-ttu-id="4df28-135">如何：建立用戶端</span><span class="sxs-lookup"><span data-stu-id="4df28-135">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)

 <span data-ttu-id="4df28-136">描述如何擷取用來從 WCF 服務建立 WCF 用戶端 proxy 的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4df28-136">Describes how to retrieve metadata used to create a WCF client proxy from a WCF service.</span></span> <span data-ttu-id="4df28-137">此程序會使用 Visual Studio 中的新增服務參考 功能。</span><span class="sxs-lookup"><span data-stu-id="4df28-137">This process uses the Add Service Reference functionality within Visual Studio.</span></span>

 [<span data-ttu-id="4df28-138">如何：設定用戶端</span><span class="sxs-lookup"><span data-stu-id="4df28-138">How to: Configure a Client</span></span>](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)

 <span data-ttu-id="4df28-139">說明如何設定 WCF 用戶端。設定用戶端時，需要指定用戶端用來存取服務的端點。</span><span class="sxs-lookup"><span data-stu-id="4df28-139">Describes how to configure a WCF client Configuring the client requires specifying the endpoint that the client uses to access the service.</span></span>

 [<span data-ttu-id="4df28-140">如何：使用用戶端</span><span class="sxs-lookup"><span data-stu-id="4df28-140">How to: Use a Client</span></span>](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)

 <span data-ttu-id="4df28-141">描述如何使用 WCF 用戶端 proxy 叫用服務作業。</span><span class="sxs-lookup"><span data-stu-id="4df28-141">Describes how to use the WCF client proxy to invoke service operations.</span></span>

## <a name="reference"></a><span data-ttu-id="4df28-142">參考資料</span><span class="sxs-lookup"><span data-stu-id="4df28-142">Reference</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="related-sections"></a><span data-ttu-id="4df28-143">相關章節</span><span class="sxs-lookup"><span data-stu-id="4df28-143">Related Sections</span></span>

- [<span data-ttu-id="4df28-144">Windows Communication Foundation (WCF) 範例</span><span class="sxs-lookup"><span data-stu-id="4df28-144">Windows Communication Foundation (WCF) samples</span></span>](./samples/index.md)
- [<span data-ttu-id="4df28-145">基本程式設計週期</span><span class="sxs-lookup"><span data-stu-id="4df28-145">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)

## <a name="see-also"></a><span data-ttu-id="4df28-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4df28-146">See also</span></span>

- [<span data-ttu-id="4df28-147">概念性概觀</span><span class="sxs-lookup"><span data-stu-id="4df28-147">Conceptual Overview</span></span>](../../../docs/framework/wcf/conceptual-overview.md)
- [<span data-ttu-id="4df28-148">文件指南</span><span class="sxs-lookup"><span data-stu-id="4df28-148">Guide to the Documentation</span></span>](../../../docs/framework/wcf/guide-to-the-documentation.md)
- [<span data-ttu-id="4df28-149">什麼是 Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="4df28-149">What Is Windows Communication Foundation</span></span>](../../../docs/framework/wcf/whats-wcf.md)
- [<span data-ttu-id="4df28-150">WCF 功能詳細資料</span><span class="sxs-lookup"><span data-stu-id="4df28-150">WCF Feature Details</span></span>](../../../docs/framework/wcf/feature-details/index.md)

---
title: 設定服務
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: 7718edaefbad18afa11b3e3680fac39da585a610
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803276"
---
# <a name="configuring-services"></a><span data-ttu-id="3a63a-102">設定服務</span><span class="sxs-lookup"><span data-stu-id="3a63a-102">Configuring Services</span></span>
<span data-ttu-id="3a63a-103">在設計並實作您的服務合約之後，就可開始設定您的服務。</span><span class="sxs-lookup"><span data-stu-id="3a63a-103">Once you have designed and implemented your service contract, you are ready to configure your service.</span></span> <span data-ttu-id="3a63a-104">您可在此處定義及自訂向用戶端公開服務的方式，包括指定所在的位址、用於傳送及接收訊息的傳輸和訊息編碼，以及所需要的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="3a63a-104">This is where you define and customize how your service is exposed to clients, including specifying the address where it can be found, the transport and message encoding it uses to send and receive messages, and the type of security it requires.</span></span>  
  
 <span data-ttu-id="3a63a-105">此處所使用的組態包括所有的方法，如命令式程式碼或使用組態檔，您可以在其中定義及自訂服務的各方面，例如指定端點位址、使用的傳輸以及安全性配置。</span><span class="sxs-lookup"><span data-stu-id="3a63a-105">Configuration as used here includes all the ways, imperatively in code or by using a configuration file, in which you can define and customize the various aspects of a service, such as specifying its endpoint addresses, the transports used, and its security schemes.</span></span> <span data-ttu-id="3a63a-106">事實上，撰寫組態是主要的撰寫 WCF 應用程式一部分。</span><span class="sxs-lookup"><span data-stu-id="3a63a-106">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3a63a-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="3a63a-107">In This Section</span></span>  
 [<span data-ttu-id="3a63a-108">簡化設定</span><span class="sxs-lookup"><span data-stu-id="3a63a-108">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 <span data-ttu-id="3a63a-109">從開始[!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)]，WCF 隨附可簡化 WCF 組態需求的新預設組態模型。</span><span class="sxs-lookup"><span data-stu-id="3a63a-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="3a63a-110">如果您未提供任何特定服務的 WCF 組態，執行階段會使用預設端點、 繫結和行為自動設定您的服務。</span><span class="sxs-lookup"><span data-stu-id="3a63a-110">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with default endpoints, bindings, and behaviors.</span></span>  
  
 [<span data-ttu-id="3a63a-111">使用設定檔設定服務</span><span class="sxs-lookup"><span data-stu-id="3a63a-111">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 <span data-ttu-id="3a63a-112">Windows Communication Foundation (WCF) 服務是可設定使用[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]技術設定。</span><span class="sxs-lookup"><span data-stu-id="3a63a-112">A Windows Communication Foundation (WCF) service is configurable using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] configuration technology.</span></span> <span data-ttu-id="3a63a-113">最常見的是，XML 項目新增至裝載 WCF 服務的 Internet Information Services (IIS) 網站的 Web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="3a63a-113">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="3a63a-114">這些項目允許您變更詳細資料，例如各電腦的端點位址 (用於與服務通訊的實際位址)。</span><span class="sxs-lookup"><span data-stu-id="3a63a-114">The elements allow you to change details, such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span>  
  
 [<span data-ttu-id="3a63a-115">繫結</span><span class="sxs-lookup"><span data-stu-id="3a63a-115">Bindings</span></span>](../../../docs/framework/wcf/bindings.md)  
 <span data-ttu-id="3a63a-116">此外，WCF 會繫結可讓您快速選取用戶端和服務如何通訊，例如傳輸、 安全性與訊息編碼使用的最基本功能的形式，包括數種系統提供的常用組態。</span><span class="sxs-lookup"><span data-stu-id="3a63a-116">In addition, WCF includes several system-provided common configurations in the form of bindings that allow you to quickly select the most basic features for how a client and service communicate, such as the transports, security, and message encodings used.</span></span>  
  
 [<span data-ttu-id="3a63a-117">端點</span><span class="sxs-lookup"><span data-stu-id="3a63a-117">Endpoints</span></span>](../../../docs/framework/wcf/endpoints.md)  
 <span data-ttu-id="3a63a-118">所有與 WCF 服務的通訊會透過*端點*的服務。</span><span class="sxs-lookup"><span data-stu-id="3a63a-118">All communication with a WCF service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="3a63a-119">端點包含合約、在繫結中指定的組態資訊，以及指出何處可找到服務或何處可取得有關服務之資訊的位址。</span><span class="sxs-lookup"><span data-stu-id="3a63a-119">Endpoints contain the contract, the configuration information that is specified in the bindings, and the addresses that indicate where to find the service or where to obtain information about the service.</span></span>  
  
 [<span data-ttu-id="3a63a-120">保護服務安全</span><span class="sxs-lookup"><span data-stu-id="3a63a-120">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 <span data-ttu-id="3a63a-121">使用 WCF 和現有的安全性機制，您可以實作機密性、 完整性、 驗證和授權，在任何服務。</span><span class="sxs-lookup"><span data-stu-id="3a63a-121">Using WCF and existing security mechanisms, you can implement confidentiality, integrity, authentication, and authorization into any service.</span></span> <span data-ttu-id="3a63a-122">您也可以稽核安全性成功和失敗。</span><span class="sxs-lookup"><span data-stu-id="3a63a-122">You can also audit for security successes and failures.</span></span>  
  
 [<span data-ttu-id="3a63a-123">建立 WS-I Basic Profile 1.1 交互操作服務</span><span class="sxs-lookup"><span data-stu-id="3a63a-123">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>](../../../docs/framework/wcf/creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 <span data-ttu-id="3a63a-124">在 WS-I Basic Profile 1.1 規格中略述了部署與其他平台或作業系統上的服務和用戶端互通之服務的需求。</span><span class="sxs-lookup"><span data-stu-id="3a63a-124">The requirements for deploying a service that is interoperable with services and clients on any other platform or operating system are outlined in the WS-I Basic Profile 1.1 specification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3a63a-125">參考資料</span><span class="sxs-lookup"><span data-stu-id="3a63a-125">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a><span data-ttu-id="3a63a-126">相關章節</span><span class="sxs-lookup"><span data-stu-id="3a63a-126">Related Sections</span></span>  
 [<span data-ttu-id="3a63a-127">基本程式設計週期</span><span class="sxs-lookup"><span data-stu-id="3a63a-127">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
 [<span data-ttu-id="3a63a-128">設計與實作服務</span><span class="sxs-lookup"><span data-stu-id="3a63a-128">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
 [<span data-ttu-id="3a63a-129">裝載服務</span><span class="sxs-lookup"><span data-stu-id="3a63a-129">Hosting Services</span></span>](../../../docs/framework/wcf/hosting-services.md)  
  
 [<span data-ttu-id="3a63a-130">建置用戶端</span><span class="sxs-lookup"><span data-stu-id="3a63a-130">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)  
  
 [<span data-ttu-id="3a63a-131">擴充性簡介</span><span class="sxs-lookup"><span data-stu-id="3a63a-131">Introduction to Extensibility</span></span>](../../../docs/framework/wcf/introduction-to-extensibility.md)  
  
 [<span data-ttu-id="3a63a-132">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="3a63a-132">Administration and Diagnostics</span></span>](../../../docs/framework/wcf/diagnostics/index.md)  
  
## <a name="see-also"></a><span data-ttu-id="3a63a-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a63a-133">See Also</span></span>  
 [<span data-ttu-id="3a63a-134">基本 WCF 程式設計</span><span class="sxs-lookup"><span data-stu-id="3a63a-134">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="3a63a-135">概念性概觀</span><span class="sxs-lookup"><span data-stu-id="3a63a-135">Conceptual Overview</span></span>](../../../docs/framework/wcf/conceptual-overview.md)  
 [<span data-ttu-id="3a63a-136">WCF 功能詳細資料</span><span class="sxs-lookup"><span data-stu-id="3a63a-136">WCF Feature Details</span></span>](../../../docs/framework/wcf/feature-details/index.md)

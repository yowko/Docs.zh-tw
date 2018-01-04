---
title: "設定服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 857ec77e54d6a55bde1a94fd9fd5758ef7a24309
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-services"></a><span data-ttu-id="73500-102">設定服務</span><span class="sxs-lookup"><span data-stu-id="73500-102">Configuring Services</span></span>
<span data-ttu-id="73500-103">在設計並實作您的服務合約之後，就可開始設定您的服務。</span><span class="sxs-lookup"><span data-stu-id="73500-103">Once you have designed and implemented your service contract, you are ready to configure your service.</span></span> <span data-ttu-id="73500-104">您可在此處定義及自訂向用戶端公開服務的方式，包括指定所在的位址、用於傳送及接收訊息的傳輸和訊息編碼，以及所需要的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="73500-104">This is where you define and customize how your service is exposed to clients, including specifying the address where it can be found, the transport and message encoding it uses to send and receive messages, and the type of security it requires.</span></span>  
  
 <span data-ttu-id="73500-105">此處所使用的組態包括所有的方法，如命令式程式碼或使用組態檔，您可以在其中定義及自訂服務的各方面，例如指定端點位址、使用的傳輸以及安全性配置。</span><span class="sxs-lookup"><span data-stu-id="73500-105">Configuration as used here includes all the ways, imperatively in code or by using a configuration file, in which you can define and customize the various aspects of a service, such as specifying its endpoint addresses, the transports used, and its security schemes.</span></span> <span data-ttu-id="73500-106">事實上，撰寫組態是程式設計 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 應用程式的主要部分。</span><span class="sxs-lookup"><span data-stu-id="73500-106">In practice, writing configuration is a major part of programming [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="73500-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="73500-107">In This Section</span></span>  
 [<span data-ttu-id="73500-108">簡化設定</span><span class="sxs-lookup"><span data-stu-id="73500-108">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 <span data-ttu-id="73500-109">從 [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)]開始， [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 隨附可簡化 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 組態需求的新預設組態模型。</span><span class="sxs-lookup"><span data-stu-id="73500-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] comes with a new default configuration model that simplifies [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration requirements.</span></span> <span data-ttu-id="73500-110">如果您沒有對特定服務提供任何 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 組態，執行階段會以預設端點、繫結和行為自動設定服務。</span><span class="sxs-lookup"><span data-stu-id="73500-110">If you do not provide any [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration for a particular service, the runtime automatically configures your service with default endpoints, bindings, and behaviors.</span></span>  
  
 [<span data-ttu-id="73500-111">使用設定檔設定服務</span><span class="sxs-lookup"><span data-stu-id="73500-111">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 <span data-ttu-id="73500-112">[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務可使用 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 組態技術來設定。</span><span class="sxs-lookup"><span data-stu-id="73500-112">A [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service is configurable using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] configuration technology.</span></span> <span data-ttu-id="73500-113">最常見的是，會將 XML 項目新增至裝載 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務的網際網路資訊服務 (IIS) 網站的 Web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="73500-113">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="73500-114">這些項目允許您變更詳細資料，例如各電腦的端點位址 (用於與服務通訊的實際位址)。</span><span class="sxs-lookup"><span data-stu-id="73500-114">The elements allow you to change details, such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span>  
  
 [<span data-ttu-id="73500-115">繫結</span><span class="sxs-lookup"><span data-stu-id="73500-115">Bindings</span></span>](../../../docs/framework/wcf/bindings.md)  
 <span data-ttu-id="73500-116">此外，[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 還包括數種系統提供的常用組態，並以繫結的形式表示，允許您快速選取用戶端和服務如何通訊的最基本功能，例如所使用的傳輸、安全性和訊息編碼。</span><span class="sxs-lookup"><span data-stu-id="73500-116">In addition, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] includes several system-provided common configurations in the form of bindings that allow you to quickly select the most basic features for how a client and service communicate, such as the transports, security, and message encodings used.</span></span>  
  
 [<span data-ttu-id="73500-117">端點</span><span class="sxs-lookup"><span data-stu-id="73500-117">Endpoints</span></span>](../../../docs/framework/wcf/endpoints.md)  
 <span data-ttu-id="73500-118">所有與通訊[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]服務會透過*端點*的服務。</span><span class="sxs-lookup"><span data-stu-id="73500-118">All communication with a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="73500-119">端點包含合約、在繫結中指定的組態資訊，以及指出何處可找到服務或何處可取得有關服務之資訊的位址。</span><span class="sxs-lookup"><span data-stu-id="73500-119">Endpoints contain the contract, the configuration information that is specified in the bindings, and the addresses that indicate where to find the service or where to obtain information about the service.</span></span>  
  
 [<span data-ttu-id="73500-120">保護服務安全</span><span class="sxs-lookup"><span data-stu-id="73500-120">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 <span data-ttu-id="73500-121">使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 和現有的安全性機制，您可以在任何服務中實作機密性、完整性、驗證和授權。</span><span class="sxs-lookup"><span data-stu-id="73500-121">Using [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] and existing security mechanisms, you can implement confidentiality, integrity, authentication, and authorization into any service.</span></span> <span data-ttu-id="73500-122">您也可以稽核安全性成功和失敗。</span><span class="sxs-lookup"><span data-stu-id="73500-122">You can also audit for security successes and failures.</span></span>  
  
 [<span data-ttu-id="73500-123">建立 WS-I Basic Profile 1.1 交互操作服務</span><span class="sxs-lookup"><span data-stu-id="73500-123">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>](../../../docs/framework/wcf/creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 <span data-ttu-id="73500-124">在 WS-I Basic Profile 1.1 規格中略述了部署與其他平台或作業系統上的服務和用戶端互通之服務的需求。</span><span class="sxs-lookup"><span data-stu-id="73500-124">The requirements for deploying a service that is interoperable with services and clients on any other platform or operating system are outlined in the WS-I Basic Profile 1.1 specification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="73500-125">參考資料</span><span class="sxs-lookup"><span data-stu-id="73500-125">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a><span data-ttu-id="73500-126">相關章節</span><span class="sxs-lookup"><span data-stu-id="73500-126">Related Sections</span></span>  
 [<span data-ttu-id="73500-127">基本程式設計週期</span><span class="sxs-lookup"><span data-stu-id="73500-127">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
 [<span data-ttu-id="73500-128">設計與實作服務</span><span class="sxs-lookup"><span data-stu-id="73500-128">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
 [<span data-ttu-id="73500-129">裝載服務</span><span class="sxs-lookup"><span data-stu-id="73500-129">Hosting Services</span></span>](../../../docs/framework/wcf/hosting-services.md)  
  
 [<span data-ttu-id="73500-130">建置用戶端</span><span class="sxs-lookup"><span data-stu-id="73500-130">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)  
  
 [<span data-ttu-id="73500-131">擴充性簡介</span><span class="sxs-lookup"><span data-stu-id="73500-131">Introduction to Extensibility</span></span>](../../../docs/framework/wcf/introduction-to-extensibility.md)  
  
 [<span data-ttu-id="73500-132">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="73500-132">Administration and Diagnostics</span></span>](../../../docs/framework/wcf/diagnostics/index.md)  
  
## <a name="see-also"></a><span data-ttu-id="73500-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="73500-133">See Also</span></span>  
 [<span data-ttu-id="73500-134">基本 WCF 程式設計</span><span class="sxs-lookup"><span data-stu-id="73500-134">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="73500-135">概念性概觀</span><span class="sxs-lookup"><span data-stu-id="73500-135">Conceptual Overview</span></span>](../../../docs/framework/wcf/conceptual-overview.md)  
 [<span data-ttu-id="73500-136">WCF 功能詳細資料</span><span class="sxs-lookup"><span data-stu-id="73500-136">WCF Feature Details</span></span>](../../../docs/framework/wcf/feature-details/index.md)

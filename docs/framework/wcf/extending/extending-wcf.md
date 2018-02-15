---
title: "延伸 WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2c84f25dfd5d3066f9c5d0b62bc0b28bc98c283d
ms.sourcegitcommit: e2bf8e6bc365bd9a0e86fe81eeae7d14f85f48c1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="extending-wcf"></a><span data-ttu-id="e484f-102">延伸 WCF</span><span class="sxs-lookup"><span data-stu-id="e484f-102">Extending WCF</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] <span data-ttu-id="e484f-103">可讓您修改和擴充執行的階段元件，以精確地控制及延伸服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="e484f-103">allows you to modify and extend run time components to precisely control and extend service-based applications.</span></span> <span data-ttu-id="e484f-104">本節中的主題將深入說明延伸性結構。</span><span class="sxs-lookup"><span data-stu-id="e484f-104">The topics in this section go in depth about the extensibility architecture.</span></span> <span data-ttu-id="e484f-105">如需基本程式設計的詳細資訊，請參閱[基本 WCF 程式設計](../../../../docs/framework/wcf/basic-wcf-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="e484f-105">For more information about basic programming, see [Basic WCF Programming](../../../../docs/framework/wcf/basic-wcf-programming.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e484f-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="e484f-106">In This Section</span></span>  
 [<span data-ttu-id="e484f-107">擴充 ServiceHost 與服務模型層</span><span class="sxs-lookup"><span data-stu-id="e484f-107">Extending ServiceHost and the Service Model Layer</span></span>](../../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md)  
 <span data-ttu-id="e484f-108">服務模型層負責從基礎通道提取傳入訊息，將它們以應用程式碼轉譯成方法叫用，然後將結果傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="e484f-108">The service model layer is responsible for pulling incoming messages out of the underlying channels, translating them into method invocations in application code, and sending the results back to the caller.</span></span>  <span data-ttu-id="e484f-109">服務模型延伸會修改或實作涉及發送器功能、自訂行為、訊息與參數攔截與其他延伸性功能的執行或通訊行為與功能。</span><span class="sxs-lookup"><span data-stu-id="e484f-109">Service model extensions modify or implement execution or communication behavior and features involving dispatcher functionality, custom behaviors, message and parameter interception, and other extensibility functionality.</span></span>  
  
 [<span data-ttu-id="e484f-110">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="e484f-110">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)  
 <span data-ttu-id="e484f-111">繫結是描述連接至端點所需之通訊詳細資料的物件。</span><span class="sxs-lookup"><span data-stu-id="e484f-111">Bindings are objects that describe the communication details required to connect to an endpoint.</span></span> <span data-ttu-id="e484f-112">繫結延伸或自訂繫結會實作支援應用程式功能所需的自訂通訊功能。</span><span class="sxs-lookup"><span data-stu-id="e484f-112">Binding extensions or custom bindings implement custom communication functionality required to support application features.</span></span>  
  
 [<span data-ttu-id="e484f-113">擴充通道層</span><span class="sxs-lookup"><span data-stu-id="e484f-113">Extending the Channel Layer</span></span>](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)  
 <span data-ttu-id="e484f-114">通道層位於服務模型層之下，負責用戶端和服務之間的訊息交換。</span><span class="sxs-lookup"><span data-stu-id="e484f-114">The channel layer sits beneath the service model layer and is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="e484f-115">通道延伸可以實作新的通訊協定功能，例如安全性。</span><span class="sxs-lookup"><span data-stu-id="e484f-115">Channel extensions can implement new protocol functionality, such as security.</span></span> <span data-ttu-id="e484f-116">通道延伸也會傳輸功能，例如實作新的網路傳輸以傳送 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="e484f-116">Channel extensions also transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
 [<span data-ttu-id="e484f-117">擴充安全性</span><span class="sxs-lookup"><span data-stu-id="e484f-117">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
 <span data-ttu-id="e484f-118">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的安全性是由傳輸安全性 (完整性、機密性和驗證)、存取控制 (授權) 和稽核所組成。</span><span class="sxs-lookup"><span data-stu-id="e484f-118">Security in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] consists of transfer security (integrity, confidentiality, and authentication), access control (authorization) and auditing.</span></span> <span data-ttu-id="e484f-119">`IdentityModel` 命名空間中的類別是由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用於存取控制。</span><span class="sxs-lookup"><span data-stu-id="e484f-119">The classes found in the `IdentityModel` namespace are used by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] for access control.</span></span> <span data-ttu-id="e484f-120">瞭解安全性結構可讓您建立自訂宣告類型，以配合自訂存取控制系統。</span><span class="sxs-lookup"><span data-stu-id="e484f-120">Understanding the security architecture allows you to create custom claim types to accommodate custom access control systems.</span></span>  
  
 [<span data-ttu-id="e484f-121">擴充中繼資料系統</span><span class="sxs-lookup"><span data-stu-id="e484f-121">Extending the Metadata System</span></span>](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)  
 <span data-ttu-id="e484f-122">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中繼資料系統是一個由類別和介面組成的群組，代表實作服務應用程式所需的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e484f-122">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="e484f-123">修改或擴充類別，或是實作和設定介面，即可匯出和匯入自訂中繼資料 (例如 Web 服務描述語言 (WSDL) 擴充功能或自訂 WS-PolicyAttachments 判斷提示)。</span><span class="sxs-lookup"><span data-stu-id="e484f-123">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
 [<span data-ttu-id="e484f-124">擴充編碼器與序列化程式</span><span class="sxs-lookup"><span data-stu-id="e484f-124">Extending Encoders and Serializers</span></span>](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
 <span data-ttu-id="e484f-125">編碼器和序列化程式會將資料從一種形式轉譯為另一種形式。</span><span class="sxs-lookup"><span data-stu-id="e484f-125">Encoders and serializers translate data from one form to another.</span></span> <span data-ttu-id="e484f-126">本節中的主題將說明如何延伸所提供的類別，以符合特殊需求。</span><span class="sxs-lookup"><span data-stu-id="e484f-126">The topics in this section discuss how to extend the supplied classes to meet special requirements.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e484f-127">參考資料</span><span class="sxs-lookup"><span data-stu-id="e484f-127">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a><span data-ttu-id="e484f-128">相關章節</span><span class="sxs-lookup"><span data-stu-id="e484f-128">Related Sections</span></span>  
 [<span data-ttu-id="e484f-129">基本 WCF 程式設計</span><span class="sxs-lookup"><span data-stu-id="e484f-129">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [<span data-ttu-id="e484f-130">WCF 功能詳細資料</span><span class="sxs-lookup"><span data-stu-id="e484f-130">WCF Feature Details</span></span>](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [<span data-ttu-id="e484f-131">方針及最佳做法</span><span class="sxs-lookup"><span data-stu-id="e484f-131">Guidelines and Best Practices</span></span>](../../../../docs/framework/wcf/guidelines-and-best-practices.md)

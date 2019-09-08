---
title: 延伸 WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
ms.openlocfilehash: 037182a3cb105f544e15a05f955c142ba57f62f3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795534"
---
# <a name="extending-wcf"></a><span data-ttu-id="0bccf-102">延伸 WCF</span><span class="sxs-lookup"><span data-stu-id="0bccf-102">Extending WCF</span></span>
<span data-ttu-id="0bccf-103">Windows Communication Foundation （WCF）可讓您修改和擴充執行時間元件，以精確地控制和擴充以服務為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0bccf-103">Windows Communication Foundation (WCF) allows you to modify and extend run time components to precisely control and extend service-based applications.</span></span> <span data-ttu-id="0bccf-104">本節中的主題將深入說明延伸性結構。</span><span class="sxs-lookup"><span data-stu-id="0bccf-104">The topics in this section go in depth about the extensibility architecture.</span></span> <span data-ttu-id="0bccf-105">如需基本程式設計的詳細資訊，請參閱[基本 WCF 程式設計](../basic-wcf-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="0bccf-105">For more information about basic programming, see [Basic WCF Programming](../basic-wcf-programming.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0bccf-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="0bccf-106">In This Section</span></span>  
 [<span data-ttu-id="0bccf-107">擴充 ServiceHost 與服務模型層</span><span class="sxs-lookup"><span data-stu-id="0bccf-107">Extending ServiceHost and the Service Model Layer</span></span>](extending-servicehost-and-the-service-model-layer.md)  
 <span data-ttu-id="0bccf-108">服務模型層負責從基礎通道提取傳入訊息，將它們以應用程式碼轉譯成方法叫用，然後將結果傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="0bccf-108">The service model layer is responsible for pulling incoming messages out of the underlying channels, translating them into method invocations in application code, and sending the results back to the caller.</span></span>  <span data-ttu-id="0bccf-109">服務模型延伸會修改或實作涉及發送器功能、自訂行為、訊息與參數攔截與其他延伸性功能的執行或通訊行為與功能。</span><span class="sxs-lookup"><span data-stu-id="0bccf-109">Service model extensions modify or implement execution or communication behavior and features involving dispatcher functionality, custom behaviors, message and parameter interception, and other extensibility functionality.</span></span>  
  
 [<span data-ttu-id="0bccf-110">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="0bccf-110">Extending Bindings</span></span>](extending-bindings.md)  
 <span data-ttu-id="0bccf-111">繫結是描述連接至端點所需之通訊詳細資料的物件。</span><span class="sxs-lookup"><span data-stu-id="0bccf-111">Bindings are objects that describe the communication details required to connect to an endpoint.</span></span> <span data-ttu-id="0bccf-112">繫結延伸或自訂繫結會實作支援應用程式功能所需的自訂通訊功能。</span><span class="sxs-lookup"><span data-stu-id="0bccf-112">Binding extensions or custom bindings implement custom communication functionality required to support application features.</span></span>  
  
 [<span data-ttu-id="0bccf-113">擴充通道層</span><span class="sxs-lookup"><span data-stu-id="0bccf-113">Extending the Channel Layer</span></span>](extending-the-channel-layer.md)  
 <span data-ttu-id="0bccf-114">通道層位於服務模型層之下，負責用戶端和服務之間的訊息交換。</span><span class="sxs-lookup"><span data-stu-id="0bccf-114">The channel layer sits beneath the service model layer and is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="0bccf-115">通道延伸可以實作新的通訊協定功能，例如安全性。</span><span class="sxs-lookup"><span data-stu-id="0bccf-115">Channel extensions can implement new protocol functionality, such as security.</span></span> <span data-ttu-id="0bccf-116">通道延伸也會傳輸功能，例如實作新的網路傳輸以傳送 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="0bccf-116">Channel extensions also transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
 [<span data-ttu-id="0bccf-117">擴充安全性</span><span class="sxs-lookup"><span data-stu-id="0bccf-117">Extending Security</span></span>](extending-security.md)  
 <span data-ttu-id="0bccf-118">WCF 中的安全性是由傳輸安全性（完整性、機密性和驗證）、存取控制（授權）和審核所組成。</span><span class="sxs-lookup"><span data-stu-id="0bccf-118">Security in WCF consists of transfer security (integrity, confidentiality, and authentication), access control (authorization) and auditing.</span></span> <span data-ttu-id="0bccf-119">在`IdentityModel`命名空間中找到的類別是由 WCF 用於存取控制。</span><span class="sxs-lookup"><span data-stu-id="0bccf-119">The classes found in the `IdentityModel` namespace are used by WCF for access control.</span></span> <span data-ttu-id="0bccf-120">瞭解安全性結構可讓您建立自訂宣告類型，以配合自訂存取控制系統。</span><span class="sxs-lookup"><span data-stu-id="0bccf-120">Understanding the security architecture allows you to create custom claim types to accommodate custom access control systems.</span></span>  
  
 [<span data-ttu-id="0bccf-121">擴充中繼資料系統</span><span class="sxs-lookup"><span data-stu-id="0bccf-121">Extending the Metadata System</span></span>](extending-the-metadata-system.md)  
 <span data-ttu-id="0bccf-122">WCF 中繼資料系統是一組類別和介面，代表執行以服務為基礎的應用程式所需的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="0bccf-122">The WCF metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="0bccf-123">修改或擴充類別，或是實作和設定介面，即可匯出和匯入自訂中繼資料 (例如 Web 服務描述語言 (WSDL) 擴充功能或自訂 WS-PolicyAttachments 判斷提示)。</span><span class="sxs-lookup"><span data-stu-id="0bccf-123">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
 [<span data-ttu-id="0bccf-124">擴充編碼器與序列化程式</span><span class="sxs-lookup"><span data-stu-id="0bccf-124">Extending Encoders and Serializers</span></span>](extending-encoders-and-serializers.md)  
 <span data-ttu-id="0bccf-125">編碼器和序列化程式會將資料從一種形式轉譯為另一種形式。</span><span class="sxs-lookup"><span data-stu-id="0bccf-125">Encoders and serializers translate data from one form to another.</span></span> <span data-ttu-id="0bccf-126">本節中的主題將說明如何延伸所提供的類別，以符合特殊需求。</span><span class="sxs-lookup"><span data-stu-id="0bccf-126">The topics in this section discuss how to extend the supplied classes to meet special requirements.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0bccf-127">參考資料</span><span class="sxs-lookup"><span data-stu-id="0bccf-127">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a><span data-ttu-id="0bccf-128">相關章節</span><span class="sxs-lookup"><span data-stu-id="0bccf-128">Related Sections</span></span>  
 [<span data-ttu-id="0bccf-129">基本 WCF 程式設計</span><span class="sxs-lookup"><span data-stu-id="0bccf-129">Basic WCF Programming</span></span>](../basic-wcf-programming.md)  
  
 [<span data-ttu-id="0bccf-130">WCF 功能詳細資料</span><span class="sxs-lookup"><span data-stu-id="0bccf-130">WCF Feature Details</span></span>](../feature-details/index.md)  
  
 [<span data-ttu-id="0bccf-131">方針及最佳做法</span><span class="sxs-lookup"><span data-stu-id="0bccf-131">Guidelines and Best Practices</span></span>](../guidelines-and-best-practices.md)

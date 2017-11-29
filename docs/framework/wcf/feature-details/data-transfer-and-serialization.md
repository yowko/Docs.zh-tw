---
title: "資料傳輸與序列化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 41357c9a039414ac692bac69337b2963d5c6b341
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="data-transfer-and-serialization"></a><span data-ttu-id="df888-102">資料傳輸與序列化</span><span class="sxs-lookup"><span data-stu-id="df888-102">Data Transfer and Serialization</span></span>
<span data-ttu-id="df888-103">在連線系統中，服務與用戶端會仰賴資料交換來完成任何工作。</span><span class="sxs-lookup"><span data-stu-id="df888-103">In a connected system, services and clients depend on the exchange of data to accomplish any task.</span></span> <span data-ttu-id="df888-104">身為服務或用戶端的開發人員的您，必須同時了解 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 如何處理資料與資料序列化，以建立有效率且容易維護的應用程式。</span><span class="sxs-lookup"><span data-stu-id="df888-104">As a developer of a service or client, you must also understand how [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] handles data and data serialization in order to create applications that are efficient and easy to maintain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="df888-105">本章節內容</span><span class="sxs-lookup"><span data-stu-id="df888-105">In This Section</span></span>  
 [<span data-ttu-id="df888-106">Specifying Data Transfer in Service Contracts</span><span class="sxs-lookup"><span data-stu-id="df888-106">Specifying Data Transfer in Service Contracts</span></span>](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 <span data-ttu-id="df888-107">說明在服務中進行資料傳輸的基本概念。</span><span class="sxs-lookup"><span data-stu-id="df888-107">Describes the basic concepts of data transfer in services.</span></span>  
  
 [<span data-ttu-id="df888-108">使用資料合約</span><span class="sxs-lookup"><span data-stu-id="df888-108">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 <span data-ttu-id="df888-109">說明何謂資料合約以及如何建立與使用它們。</span><span class="sxs-lookup"><span data-stu-id="df888-109">Describes what data contracts are and how to create and use them.</span></span>  
  
 [<span data-ttu-id="df888-110">資料合約序列化程式</span><span class="sxs-lookup"><span data-stu-id="df888-110">Data Contract Serializer</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
 <span data-ttu-id="df888-111">說明如何透過 <xref:System.Runtime.Serialization.DataContractSerializer> 類別，或 <xref:System.Runtime.Serialization.XmlObjectSerializer> 類別的任何延伸來完成資料的序列化作業。</span><span class="sxs-lookup"><span data-stu-id="df888-111">Describes how to accomplish serialization of data with the <xref:System.Runtime.Serialization.DataContractSerializer> class or any extension of the <xref:System.Runtime.Serialization.XmlObjectSerializer> class.</span></span>  
  
 [<span data-ttu-id="df888-112">使用 XmlSerializer 類別</span><span class="sxs-lookup"><span data-stu-id="df888-112">Using the XmlSerializer Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 <span data-ttu-id="df888-113">說明如何與為何使用 <xref:System.Xml.Serialization.XmlSerializer> 類別 (<xref:System.Runtime.Serialization.DataContractSerializer> 類別的替代項目)。</span><span class="sxs-lookup"><span data-stu-id="df888-113">Describes how and why to use the <xref:System.Xml.Serialization.XmlSerializer> class, an alternative to the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 [<span data-ttu-id="df888-114">使用訊息合約</span><span class="sxs-lookup"><span data-stu-id="df888-114">Using Message Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)  
 <span data-ttu-id="df888-115">說明訊息合約如何允許對 SOAP 訊息進行精密控制。</span><span class="sxs-lookup"><span data-stu-id="df888-115">Describes how message contracts allow fine control over SOAP messages.</span></span>  
  
 [<span data-ttu-id="df888-116">使用 Message 類別</span><span class="sxs-lookup"><span data-stu-id="df888-116">Using the Message Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)  
 <span data-ttu-id="df888-117">說明如何使用 Message 類別功能。</span><span class="sxs-lookup"><span data-stu-id="df888-117">Describes how to use Message class features.</span></span>  
  
 [<span data-ttu-id="df888-118">篩選</span><span class="sxs-lookup"><span data-stu-id="df888-118">Filtering</span></span>](../../../../docs/framework/wcf/feature-details/filtering.md)  
 <span data-ttu-id="df888-119">說明可依據不同準則對訊息進行前置處理的篩選功能。</span><span class="sxs-lookup"><span data-stu-id="df888-119">Describes filtering, which enables pre-processing of a message based on various criteria.</span></span>  
  
 [<span data-ttu-id="df888-120">大型的資料與資料流</span><span class="sxs-lookup"><span data-stu-id="df888-120">Large Data and Streaming</span></span>](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 <span data-ttu-id="df888-121">說明如何傳送大型資料區塊，例如二進位檔。</span><span class="sxs-lookup"><span data-stu-id="df888-121">Describes how to send a large block of data, such as a binary file.</span></span>  
  
 [<span data-ttu-id="df888-122">資料的安全性考量</span><span class="sxs-lookup"><span data-stu-id="df888-122">Security Considerations for Data</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 <span data-ttu-id="df888-123">說明在設計資料傳輸與序列化的程式時，要注意的項目。</span><span class="sxs-lookup"><span data-stu-id="df888-123">Describes items to be aware of when programming data transfer and serialization.</span></span>  
  
 [<span data-ttu-id="df888-124">資料傳輸架構概觀</span><span class="sxs-lookup"><span data-stu-id="df888-124">Data Transfer Architectural Overview</span></span>](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 <span data-ttu-id="df888-125">說明 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的整體資料傳輸設計觀點。</span><span class="sxs-lookup"><span data-stu-id="df888-125">Describes a view of the overall design of data transfer in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="reference"></a><span data-ttu-id="df888-126">參考資料</span><span class="sxs-lookup"><span data-stu-id="df888-126">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a><span data-ttu-id="df888-127">相關章節</span><span class="sxs-lookup"><span data-stu-id="df888-127">Related Sections</span></span>  
 [<span data-ttu-id="df888-128">擴充編碼器與序列化程式</span><span class="sxs-lookup"><span data-stu-id="df888-128">Extending Encoders and Serializers</span></span>](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a><span data-ttu-id="df888-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df888-129">See Also</span></span>  
 [<span data-ttu-id="df888-130">最佳做法：資料合約版本設定</span><span class="sxs-lookup"><span data-stu-id="df888-130">Best Practices: Data Contract Versioning</span></span>](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)  
 [<span data-ttu-id="df888-131">服務版本設定</span><span class="sxs-lookup"><span data-stu-id="df888-131">Service Versioning</span></span>](../../../../docs/framework/wcf/service-versioning.md)

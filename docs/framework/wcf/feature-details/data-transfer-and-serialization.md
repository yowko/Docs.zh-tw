---
title: 資料傳輸與序列化
ms.date: 03/30/2017
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
ms.openlocfilehash: 490c89f5cfbecd4b2cc0c0e639aa97849132a809
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261978"
---
# <a name="data-transfer-and-serialization"></a><span data-ttu-id="b97b5-102">資料傳輸與序列化</span><span class="sxs-lookup"><span data-stu-id="b97b5-102">Data Transfer and Serialization</span></span>

<span data-ttu-id="b97b5-103">在連線系統中，服務與用戶端會仰賴資料交換來完成任何工作。</span><span class="sxs-lookup"><span data-stu-id="b97b5-103">In a connected system, services and clients depend on the exchange of data to accomplish any task.</span></span> <span data-ttu-id="b97b5-104">作為服務或用戶端的開發人員，您也必須瞭解 Windows Communication Foundation (WCF) 如何處理資料和資料序列化，以便建立有效率且容易維護的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b97b5-104">As a developer of a service or client, you must also understand how Windows Communication Foundation (WCF) handles data and data serialization in order to create applications that are efficient and easy to maintain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b97b5-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="b97b5-105">In This Section</span></span>  

 [<span data-ttu-id="b97b5-106">指定服務合約中的資料傳輸</span><span class="sxs-lookup"><span data-stu-id="b97b5-106">Specifying Data Transfer in Service Contracts</span></span>](specifying-data-transfer-in-service-contracts.md)  
 <span data-ttu-id="b97b5-107">說明在服務中進行資料傳輸的基本概念。</span><span class="sxs-lookup"><span data-stu-id="b97b5-107">Describes the basic concepts of data transfer in services.</span></span>  
  
 [<span data-ttu-id="b97b5-108">使用資料合約</span><span class="sxs-lookup"><span data-stu-id="b97b5-108">Using Data Contracts</span></span>](using-data-contracts.md)  
 <span data-ttu-id="b97b5-109">說明何謂資料合約以及如何建立與使用它們。</span><span class="sxs-lookup"><span data-stu-id="b97b5-109">Describes what data contracts are and how to create and use them.</span></span>  
  
 [<span data-ttu-id="b97b5-110">資料合約序列化程式</span><span class="sxs-lookup"><span data-stu-id="b97b5-110">Data Contract Serializer</span></span>](data-contract-serializer.md)  
 <span data-ttu-id="b97b5-111">說明如何透過 <xref:System.Runtime.Serialization.DataContractSerializer> 類別，或 <xref:System.Runtime.Serialization.XmlObjectSerializer> 類別的任何延伸來完成資料的序列化作業。</span><span class="sxs-lookup"><span data-stu-id="b97b5-111">Describes how to accomplish serialization of data with the <xref:System.Runtime.Serialization.DataContractSerializer> class or any extension of the <xref:System.Runtime.Serialization.XmlObjectSerializer> class.</span></span>  
  
 [<span data-ttu-id="b97b5-112">使用 XmlSerializer 類別</span><span class="sxs-lookup"><span data-stu-id="b97b5-112">Using the XmlSerializer Class</span></span>](using-the-xmlserializer-class.md)  
 <span data-ttu-id="b97b5-113">說明如何與為何使用 <xref:System.Xml.Serialization.XmlSerializer> 類別 (<xref:System.Runtime.Serialization.DataContractSerializer> 類別的替代項目)。</span><span class="sxs-lookup"><span data-stu-id="b97b5-113">Describes how and why to use the <xref:System.Xml.Serialization.XmlSerializer> class, an alternative to the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 [<span data-ttu-id="b97b5-114">使用訊息合約</span><span class="sxs-lookup"><span data-stu-id="b97b5-114">Using Message Contracts</span></span>](using-message-contracts.md)  
 <span data-ttu-id="b97b5-115">說明訊息合約如何允許對 SOAP 訊息進行精密控制。</span><span class="sxs-lookup"><span data-stu-id="b97b5-115">Describes how message contracts allow fine control over SOAP messages.</span></span>  
  
 [<span data-ttu-id="b97b5-116">使用 Message 類別</span><span class="sxs-lookup"><span data-stu-id="b97b5-116">Using the Message Class</span></span>](using-the-message-class.md)  
 <span data-ttu-id="b97b5-117">說明如何使用 Message 類別功能。</span><span class="sxs-lookup"><span data-stu-id="b97b5-117">Describes how to use Message class features.</span></span>  
  
 [<span data-ttu-id="b97b5-118">篩選</span><span class="sxs-lookup"><span data-stu-id="b97b5-118">Filtering</span></span>](filtering.md)  
 <span data-ttu-id="b97b5-119">說明可依據不同準則對訊息進行前置處理的篩選功能。</span><span class="sxs-lookup"><span data-stu-id="b97b5-119">Describes filtering, which enables pre-processing of a message based on various criteria.</span></span>  
  
 [<span data-ttu-id="b97b5-120">大型資料與資料流</span><span class="sxs-lookup"><span data-stu-id="b97b5-120">Large Data and Streaming</span></span>](large-data-and-streaming.md)  
 <span data-ttu-id="b97b5-121">說明如何傳送大型資料區塊，例如二進位檔。</span><span class="sxs-lookup"><span data-stu-id="b97b5-121">Describes how to send a large block of data, such as a binary file.</span></span>  
  
 [<span data-ttu-id="b97b5-122">資料的安全性考量</span><span class="sxs-lookup"><span data-stu-id="b97b5-122">Security Considerations for Data</span></span>](security-considerations-for-data.md)  
 <span data-ttu-id="b97b5-123">說明在設計資料傳輸與序列化的程式時，要注意的項目。</span><span class="sxs-lookup"><span data-stu-id="b97b5-123">Describes items to be aware of when programming data transfer and serialization.</span></span>  
  
 [<span data-ttu-id="b97b5-124">資料傳輸架構概觀</span><span class="sxs-lookup"><span data-stu-id="b97b5-124">Data Transfer Architectural Overview</span></span>](data-transfer-architectural-overview.md)  
 <span data-ttu-id="b97b5-125">描述 WCF 中資料傳輸的整體設計的觀點。</span><span class="sxs-lookup"><span data-stu-id="b97b5-125">Describes a view of the overall design of data transfer in WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b97b5-126">參考</span><span class="sxs-lookup"><span data-stu-id="b97b5-126">Reference</span></span>  

 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a><span data-ttu-id="b97b5-127">相關章節</span><span class="sxs-lookup"><span data-stu-id="b97b5-127">Related Sections</span></span>  

 [<span data-ttu-id="b97b5-128">擴充編碼器與序列化程式</span><span class="sxs-lookup"><span data-stu-id="b97b5-128">Extending Encoders and Serializers</span></span>](../extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a><span data-ttu-id="b97b5-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b97b5-129">See also</span></span>

- [<span data-ttu-id="b97b5-130">最佳做法：資料合約版本控制</span><span class="sxs-lookup"><span data-stu-id="b97b5-130">Best Practices: Data Contract Versioning</span></span>](../best-practices-data-contract-versioning.md)
- [<span data-ttu-id="b97b5-131">服務版本控制</span><span class="sxs-lookup"><span data-stu-id="b97b5-131">Service Versioning</span></span>](../service-versioning.md)

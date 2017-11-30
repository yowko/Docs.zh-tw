---
title: "Reliable Messaging Protocol 1.0 版"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d204600682ec8acbc229240c4e1bc859d8ea4d21
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="reliable-messaging-protocol-version-10"></a><span data-ttu-id="ae2bf-102">Reliable Messaging Protocol 1.0 版</span><span class="sxs-lookup"><span data-stu-id="ae2bf-102">Reliable Messaging Protocol version 1.0</span></span>
<span data-ttu-id="ae2bf-103">本主題涵蓋了 WS-Reliable Messaging February 2005 (1.0 版) 通訊協定的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 實作詳細資料，這個通訊協定是使用 HTTP 傳輸來進行交互操作時所需的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-103">This topic covers [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] implementation details for the WS-Reliable Messaging February 2005 (version 1.0) protocol necessary for interoperation using the HTTP transport.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-104"> 遵循本主題所述 WS-Reliable Messaging 規格的條件約束及說明。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-104"> follows the WS-Reliable Messaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="ae2bf-105">請注意，[!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] 中開始實作 WS-ReliableMessaging 1.0 版通訊協定。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-105">Note that the WS-ReliableMessaging version 1.0 protocol is implemented starting with the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].</span></span>  
  
 <span data-ttu-id="ae2bf-106">WS-Reliable Messaging February 2005 通訊協定可透過 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 在 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> 中實作。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-106">The WS-Reliable Messaging February 2005 protocol is implemented in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>  
  
 <span data-ttu-id="ae2bf-107">為了方便起見，本主題將使用下列角色：</span><span class="sxs-lookup"><span data-stu-id="ae2bf-107">For convenience, the topic uses the following roles:</span></span>  
  
-   <span data-ttu-id="ae2bf-108">啟動器：啟動 WS-Reliable 訊息序列建立作業的用戶端</span><span class="sxs-lookup"><span data-stu-id="ae2bf-108">Initiator: the client that initiates WS-Reliable Message sequence creation</span></span>  
  
-   <span data-ttu-id="ae2bf-109">回應程式：接收啟動器要求的服務</span><span class="sxs-lookup"><span data-stu-id="ae2bf-109">Responder: the service that receives the initiator's requests</span></span>  
  
 <span data-ttu-id="ae2bf-110">本文件會使用下表的前置詞和命名空間。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-110">This document uses the prefixes and namespaces in the following table.</span></span>  
  
|<span data-ttu-id="ae2bf-111">前置詞</span><span class="sxs-lookup"><span data-stu-id="ae2bf-111">Prefix</span></span>|<span data-ttu-id="ae2bf-112">命名空間</span><span class="sxs-lookup"><span data-stu-id="ae2bf-112">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="ae2bf-113">wsrm</span><span class="sxs-lookup"><span data-stu-id="ae2bf-113">wsrm</span></span>|<span data-ttu-id="ae2bf-114">http://schemas.xmlsoap.org/ws/2005/02/rm</span><span class="sxs-lookup"><span data-stu-id="ae2bf-114">http://schemas.xmlsoap.org/ws/2005/02/rm</span></span>|  
|<span data-ttu-id="ae2bf-115">netrm</span><span class="sxs-lookup"><span data-stu-id="ae2bf-115">netrm</span></span>|<span data-ttu-id="ae2bf-116">http://schemas.microsoft.com/ws/2006/05/rm</span><span class="sxs-lookup"><span data-stu-id="ae2bf-116">http://schemas.microsoft.com/ws/2006/05/rm</span></span>|  
|<span data-ttu-id="ae2bf-117">s</span><span class="sxs-lookup"><span data-stu-id="ae2bf-117">s</span></span>|<span data-ttu-id="ae2bf-118">http://www.w3.org/2003/05/soap-envelope</span><span class="sxs-lookup"><span data-stu-id="ae2bf-118">http://www.w3.org/2003/05/soap-envelope</span></span>|  
|<span data-ttu-id="ae2bf-119">wsa</span><span class="sxs-lookup"><span data-stu-id="ae2bf-119">wsa</span></span>|<span data-ttu-id="ae2bf-120">http://schemas.xmlsoap.org/ws/2005/08/addressing</span><span class="sxs-lookup"><span data-stu-id="ae2bf-120">http://schemas.xmlsoap.org/ws/2005/08/addressing</span></span>|  
|<span data-ttu-id="ae2bf-121">wsse</span><span class="sxs-lookup"><span data-stu-id="ae2bf-121">wsse</span></span>|<span data-ttu-id="ae2bf-122">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd</span><span class="sxs-lookup"><span data-stu-id="ae2bf-122">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd</span></span>|  
  
## <a name="messaging"></a><span data-ttu-id="ae2bf-123">傳訊</span><span class="sxs-lookup"><span data-stu-id="ae2bf-123">Messaging</span></span>  
  
### <a name="sequence-establishment-messages"></a><span data-ttu-id="ae2bf-124">序列建立訊息</span><span class="sxs-lookup"><span data-stu-id="ae2bf-124">Sequence Establishment Messages</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-125"> 會實作 `CreateSequence` 和 `CreateSequenceResponse` 訊息以建立可靠訊息序列。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-125"> implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable message sequence.</span></span> <span data-ttu-id="ae2bf-126">以下是適用的條件約束：</span><span class="sxs-lookup"><span data-stu-id="ae2bf-126">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="ae2bf-127">B1101：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器不會在 `CreateSequence` 訊息中產生選用的 Expires 項目，或當 `CreateSequence` 訊息包含 `Offer` 項目時，在 `Expires` 項目中產生選用的 `Offer` 項目。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-127">B1101: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator does not generate the optional Expires element in the `CreateSequence` message or, in the cases when the `CreateSequence` message contains an `Offer` element, the optional `Expires` element in the `Offer` element.</span></span>  
  
-   <span data-ttu-id="ae2bf-128">B1102：在存取 `CreateSequence` 訊息時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]`Responder` 會同時傳送與接收 `Expires` 項目 (如果兩者都存在的話)，但是不會使用它們的值。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-128">B1102: When accessing the `CreateSequence` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]`Responder` sends and receives both `Expires` elements if they exist, but does not use their values.</span></span>  
  
 <span data-ttu-id="ae2bf-129">WS-Reliable 訊息會使用 `Offer` 機制來建立兩個反向關聯序列以形成工作階段。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-129">WS-Reliable Messaging introduces the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>  
  
-   <span data-ttu-id="ae2bf-130">R1103：如果 `CreateSequence` 包含 `Offer` 項目，則可信賴傳訊回應程式必須接收序列並以包含 `CreateSequenceResponse` 項目的 `wsrm:Accept` 來回應，以形成兩個相互關聯的反向序列，或是拒絕 `CreateSequence` 要求。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-130">R1103: If `CreateSequence` contains an `Offer` element, the Reliable Messaging Responder must either accept the sequence and respond with `CreateSequenceResponse` that contains a `wsrm:Accept` element, forming two correlated converse sequences or reject the `CreateSequence` request.</span></span>  
  
-   <span data-ttu-id="ae2bf-131">R1104：流經反向序列的 `SequenceAcknowledgement` 和應用程式訊息必須傳送到 `ReplyTo` 的 `CreateSequence` 端點參考。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-131">R1104: `SequenceAcknowledgement` and application messages flowing on converse sequence must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="ae2bf-132">R1105：`AcksTo` 中的 `ReplyTo` 和 `CreateSequence` 端點參考必須具有位址值以符合八位元規格。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-132">R1105: `AcksTo` and `ReplyTo` endpoint references in the `CreateSequence` must have address values that match the octet-wise.</span></span>  
  
     <span data-ttu-id="ae2bf-133">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會在建立序列之前，先驗證 `AcksTo`、`ReplyTo` EPR 的 URI 部分是否相同。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-133">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder verifies that the URI portion of the `AcksTo` and `ReplyTo` EPRs are identical before creating a sequence.</span></span>  
  
-   <span data-ttu-id="ae2bf-134">R1106：`AcksTo` 訊息中的 `ReplyTo` 和 `CreateSequence` 端點參照應該具有相同的參照參數集合。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-134">R1106: `AcksTo` and `ReplyTo` Endpoint References in the `CreateSequence` should have the same set of reference parameters.</span></span>  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-135"> 不會強制執行，但會假定 `AcksTo` 上的 `ReplyTo` 和 `CreateSequence` 之 [reference parameters] 都是一樣，並且使用來自 `ReplyTo` 端點參照的 [reference parameters]，以認可並與序列訊息對話。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-135"> does not enforce but assumes that [reference parameters] of `AcksTo` and `ReplyTo` on `CreateSequence` are identical and uses [reference parameters] from `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>  
  
-   <span data-ttu-id="ae2bf-136">R1107：當兩個反向序列都是透過 `Offer` 機制建立時，流經反向序列的 `SequenceAcknowledgement` 和應用程式訊息必須傳送至 `ReplyTo` 的 `CreateSequence` 端點參考。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-136">R1107: When two converse sequences are established using the `Offer` mechanism, `SequenceAcknowledgement` and application messages flowing on converse sequences must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="ae2bf-137">R1108：當兩個反向序列都透過 Offer 機制建立時，`[address]` 端點參考子項目 (屬於 `wsrm:AcksTo` 的 `wsrm:Accept` 項目) 的 `CreateSequenceResponse` 屬性必須符合 `CreateSequence` 的目的地 URI 的位元組規格。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-137">R1108: When two converse sequences are established using the Offer mechanism, the `[address]` property of the `wsrm:AcksTo` Endpoint Reference child element of the `wsrm:Accept` element of the `CreateSequenceResponse` must match byte-wise the destination URI of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="ae2bf-138">R1109：當兩個反向序列都是透過 `Offer` 機制建立時，從啟動器傳送的訊息以及透過回應程式對訊息的認可，必須傳送至相同的端點參考。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-138">R1109: When two converse sequences are established using the `Offer` mechanism, messages sent by initiator and acknowledgements to messages by responder must be sent to the same Endpoint Reference.</span></span>  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-139"> 使用 WS-Reliable 訊息在啟動器與回應程式之間建立可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-139"> uses WS-Reliable Messaging to establish reliable sessions between the Initiator and Responder.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-140"> 的 WS-Reliable 訊息實作會針對單向、要求-回覆與全雙工訊息模式提供可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-140">'s WS-Reliable Messaging implementation provides reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="ae2bf-141">Ws-reliable 訊息`Offer`上的機制`CreateSequence` / `CreateSequenceResponse`可讓您建立兩個相互關聯的反向序列，並提供工作階段通訊協定，可適用於所有訊息端點。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-141">The WS-Reliable Messaging `Offer` mechanism on `CreateSequence`/`CreateSequenceResponse` lets you establish two correlated converse sequences, and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="ae2bf-142">由於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會針對此類工作階段提供安全性保證，包含工作階段完整性的端對端保護，因此可以實際地確保訊息會抵達預定的相同目的地。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-142">Because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure messages intended to the same party are arriving at the same destination.</span></span> <span data-ttu-id="ae2bf-143">這麼做也可以針對應用程式訊息進行 Piggy-Backing 的序列認可作業。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-143">This also allows piggy-backing of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="ae2bf-144">因此，R1104、R1105，和 R1108 的約束條件適用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-144">Therefore, constraints R1104, R1105, and R1108 apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="ae2bf-145">`CreateSequence` 訊息的範例。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-145">An example of a `CreateSequence` message.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action s:mustUnderstand="1">  
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequence  
    </a:Action>  
    <a:ReplyTo>  
      <a:Address>          
         http://Business456.com/clientA        
      </a:Address>  
    </a:ReplyTo>  
    <a:MessageID>  
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
    </a:MessageID>  
    <a:To s:mustUnderstand="1">  
      http://Business456.com/clientA  
    </a:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CreateSequence>  
      <wsrm:AcksTo>  
       <wsa:Address>  
         http://Business456.com/clientA  
       </wsa:Address>  
     </wsrm:AcksTo>  
     <wsrm:Offer>  
      <wsrm:Identifier>  
        urn:uuid:0afb8d36-bf26-4776-b8cf-8c91fddb5496  
      </wsrm:Identifier>  
     </wsrm:Offer>  
   </wsrm:CreateSequence>  
  </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="ae2bf-146">`CreateSequenceResponse` 訊息的範例。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-146">An example of a `CreateSequenceResponse` message.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action s:mustUnderstand="1">  
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequenceResponse  
    </a:Action>  
    <a:RelatesTo>  
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
    </a:RelatesTo>  
    <a:To s:mustUnderstand="1">  
      http://Business456.com/clientA  
    </a:To>  
  </s:Header>  
  <s:Body>  
   <wsrm:CreateSequenceResponse>  
    <Identifier>  
     urn:uuid:eea0a36c-b38a-43e8-8c76-2fabe2d76386  
    </Identifier>  
    <Accept>  
    <AcksTo>  
      <a:Address>  
        http://BusinessABC.com/serviceA  
      </a:Address>  
    </AcksTo>  
    </Accept>  
   </wsrm:CreateSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="sequence"></a><span data-ttu-id="ae2bf-147">序列</span><span class="sxs-lookup"><span data-stu-id="ae2bf-147">Sequence</span></span>  
 <span data-ttu-id="ae2bf-148">下列清單列出適用於序列的條件約束：</span><span class="sxs-lookup"><span data-stu-id="ae2bf-148">The following is a list of constraints that apply to sequences:</span></span>  
  
-   <span data-ttu-id="ae2bf-149">B1201:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]會產生並存取序號大於`xs:long`的最大包含值，9223372036854775807。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-149">B1201:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>  
  
-   <span data-ttu-id="ae2bf-150">B1202:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]一律會產生空白主體最後一個訊息，與 http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage 的動作 URI。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-150">B1202:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] always generates an empty-bodied last message with the action URI of http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span></span>  
  
-   <span data-ttu-id="ae2bf-151">B1203：只要動作 URI 不是 http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會透過序列標頭 (其中包含 `LastMessage` 項目) 來接收與傳遞訊息。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-151">B1203: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] receives and delivers a message with a Sequence header that contains a `LastMessage` element as long as the action URI is not http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span></span>  
  
 <span data-ttu-id="ae2bf-152">序列標頭的範例。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-152">An example of a Sequence Header.</span></span>  
  
```xml  
<wsrm:Sequence>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
  <wsrm:MessageNumber>  
    10  
  </wsrm:MessageNumber>  
  <wsrm:LastMessage/>  
 </wsrm:Sequence>  
```  
  
### <a name="ackrequested-header"></a><span data-ttu-id="ae2bf-153">AckRequested 標頭</span><span class="sxs-lookup"><span data-stu-id="ae2bf-153">AckRequested Header</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-154"> 會使用 `AckRequested` 標頭做為 Keep-Alive 機制。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-154"> uses `AckRequested` Header as a keep-alive mechanism.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-155"> 不會產生選用的 `MessageNumber` 元素。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-155"> does not generate the optional `MessageNumber` element.</span></span> <span data-ttu-id="ae2bf-156">在收到使用 `AckRequested` 標頭 (內含 `MessageNumber` 項目) 的訊息時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會忽略 `MessageNumber` 的項目值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-156">Upon receiving a message with an `AckRequested` header that contains the `MessageNumber` element, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignores the `MessageNumber` element’s value, as shown in the following example.</span></span>  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement-header"></a><span data-ttu-id="ae2bf-157">SequenceAcknowledgement 標頭</span><span class="sxs-lookup"><span data-stu-id="ae2bf-157">SequenceAcknowledgement Header</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-158"> 會針對 WS-Reliable 訊息所提供的序列認可使用 Piggy-Back 機制。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-158"> uses piggy-back mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="ae2bf-159">R1401：當兩個反向序列透過 `Offer` 機制建立時，`SequenceAcknowledgement` 標頭可以包含在任何傳送至目的收件者的應用程式訊息中。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-159">R1401: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span>  
  
-   <span data-ttu-id="ae2bf-160">B1402：當 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 在收到任何序列訊息之前必須先產生認可時 (例如，為了滿足 `AckRequested` 訊息)，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會產生包含範圍 0-0 的 `SequenceAcknowledgement` 標頭，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-160">B1402: When [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] must generate an acknowledgement prior to receiving any sequence messages (for example, to satisfy an `AckRequested` message), [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates a `SequenceAcknowledgement` header that contains the range 0-0, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="0" Lower="0"/>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="ae2bf-161">B1403：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不會產生包含 `SequenceAcknowledgement` 項目的 `Nack` 標頭，但是支援 `Nack` 項目。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-161">B1403: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate `SequenceAcknowledgement` headers that contain a `Nack` element but supports `Nack` elements.</span></span>  
  
### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="ae2bf-162">WS-ReliableMessaging 錯誤</span><span class="sxs-lookup"><span data-stu-id="ae2bf-162">WS-ReliableMessaging Faults</span></span>  
 <span data-ttu-id="ae2bf-163">下列清單列出適用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 之 WS-Reliable 訊息錯誤實作的條件約束：</span><span class="sxs-lookup"><span data-stu-id="ae2bf-163">The following is a list of constraints that apply to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation of WS-Reliable Messaging faults:</span></span>  
  
-   <span data-ttu-id="ae2bf-164">B1501：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不會產生 `MessageNumberRollover` 錯誤。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-164">B1501: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate `MessageNumberRollover` faults.</span></span>  
  
-   <span data-ttu-id="ae2bf-165">B1502:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]端點可能會產生`CreateSequenceRefused`規格中所述的錯誤。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-165">B1502:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint may generate `CreateSequenceRefused` faults as described in the specification.</span></span>  
  
-   <span data-ttu-id="ae2bf-166">B1503:When 服務端點到達其連線限制，且無法處理新的連接，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]會產生額外`CreateSequenceRefused`錯誤子代碼`netrm:ConnectionLimitReached`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-166">B1503:When the service endpoint reaches its connection limit and cannot process new connections, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates an additional `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>  
  
    ```xml  
    <s:Envelope>  
      <s:Header>  
        <wsa:Action>  
          http://schemas.xmlsoap.org/ws/2005/08/addressing/fault  
        </wsa:Action>  
      </s:Header>  
      <s:Body>  
        <s:Fault>  
          <s:Code>  
            <s:Value>  
              s:Receiver  
            </s:Value>  
            <s:Subcode>  
              <s:Value>  
                wsrm:CreateSequenceRefused  
              </s:Value>  
              <s:Subcode>  
                <s:Value>  
                  netrm:ConnectionLimitReached  
                </s:Value>  
              </s:Subcode>  
            </s:Subcode>  
          </s:Code>  
          <s:Reason>  
            <s:Text xml:lang="en">  
              [Reason]  
            </s:Text>  
          </s:Reason>  
        </s:Fault>  
      </s:Body>  
    </s:Envelope>  
    ```  
  
### <a name="ws-addressing-faults"></a><span data-ttu-id="ae2bf-167">WS-Addressing 錯誤</span><span class="sxs-lookup"><span data-stu-id="ae2bf-167">WS-Addressing Faults</span></span>  
 <span data-ttu-id="ae2bf-168">由於 WS-Reliable 訊息是使用 WS-Addressing，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-Reliable 訊息實作可能會產生並傳送 WS-Addressing 錯誤。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-168">Because WS-Reliable Messaging uses WS-Addressing, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-Reliable Messaging implementation may generate WS-Addressing faults.</span></span> <span data-ttu-id="ae2bf-169">本節涵蓋 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 在 WS-Reliable 訊息層明確產生的 WS-Addressing 錯誤：</span><span class="sxs-lookup"><span data-stu-id="ae2bf-169">This section covers the WS-Addressing faults that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] explicitly generates at the WS-Reliable Messaging layer:</span></span>  
  
-   <span data-ttu-id="ae2bf-170">B1601:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]當下列其中一項條件成立時，會產生錯誤訊息定址標頭需要：</span><span class="sxs-lookup"><span data-stu-id="ae2bf-170">B1601:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates the fault Message Addressing Header Required when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="ae2bf-171">訊息缺少 `Sequence` 標頭和 `Action` 標頭。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-171">A message is missing a `Sequence` header and an `Action` header.</span></span>  
  
    -   <span data-ttu-id="ae2bf-172">`CreateSequence` 訊息缺少 `MessageId` 標頭。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-172">A `CreateSequence` message is missing a `MessageId` header.</span></span>  
  
    -   <span data-ttu-id="ae2bf-173">`CreateSequence` 訊息缺少 `ReplyTo` 標頭。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-173">A `CreateSequence` message is missing a `ReplyTo` header.</span></span>  
  
-   <span data-ttu-id="ae2bf-174">B1602:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]會產生錯誤動作不支援時遺失訊息`Sequence`標頭，且`Action`不是可辨識的 Ws-reliable 訊息規格中的標頭。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-174">B1602:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates the fault Action Not Supported in reply to a message that is missing a `Sequence` header and has an `Action` header that is not a recognized in the WS-Reliable Messaging specification.</span></span>  
  
-   <span data-ttu-id="ae2bf-175">B1603:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]會產生錯誤端點無法使用，表示端點不會處理順序根據檢查`CreateSequence`訊息之定址標頭。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-175">B1603:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates the fault Endpoint Unavailable to indicate that the endpoint does not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>  
  
## <a name="protocol-composition"></a><span data-ttu-id="ae2bf-176">通訊協定組合</span><span class="sxs-lookup"><span data-stu-id="ae2bf-176">Protocol Composition</span></span>  
  
### <a name="composition-with-ws-addressing"></a><span data-ttu-id="ae2bf-177">與 WS-Addressing 組合</span><span class="sxs-lookup"><span data-stu-id="ae2bf-177">Composition with WS-Addressing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-178"> 支援兩種版本的 WS-Addressing：WS-Addressing 2004/08 [WS-ADDR] 和 W3C WS-Addressing 1.0 建議 [WS-ADDR-CORE] 和 [WS-ADDR-SOAP]。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-178"> supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>  
  
 <span data-ttu-id="ae2bf-179">儘管 WS-Reliable 訊息規格只提到 WS-Addressing 2004/08，它並未限制要使用的 WS-Addressing 版本。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-179">While the WS-Reliable Messaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="ae2bf-180">下列清單列出適用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的條件約束：</span><span class="sxs-lookup"><span data-stu-id="ae2bf-180">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="ae2bf-181">R2101： 兩個 Ws-addressing 2004/08 和 Ws-addressing 1.0 可與 WS 可靠傳訊。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-181">R2101:Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="ae2bf-182">R2102:A 單一版本的 Ws-addressing 必須在整個指定的 Ws-reliable 訊息序列或一組使用相互關聯的反向序列`wsrm:Offer`機制。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-182">R2102:A single version of WS-Addressing must be used throughout a given WS-Reliable Messaging sequence or a pair of converse sequences correlated by using the `wsrm:Offer` mechanism.</span></span>  
  
### <a name="composition-with-soap"></a><span data-ttu-id="ae2bf-183">與 SOAP 組合</span><span class="sxs-lookup"><span data-stu-id="ae2bf-183">Composition with SOAP</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-184"> 同時支援 SOAP 1.1 和 SOAP 1.2 搭配 WS-Reliable 訊息一起使用。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-184"> supports use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="ae2bf-185">與 WS-Security 和 WS-SecureConversation 組合</span><span class="sxs-lookup"><span data-stu-id="ae2bf-185">Composition with WS-Security and WS-SecureConversation</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-186"> 透過安全傳輸 (HTTPS)、與 WS-Security 組合，以及與 WS-Secure Conversation 組合，為 WS-Reliable 訊息序列提供保護。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-186"> provides protection for WS-Reliable Messaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="ae2bf-187">下列清單列出適用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的條件約束：</span><span class="sxs-lookup"><span data-stu-id="ae2bf-187">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="ae2bf-188">R2301： 若要保護的個別訊息，除了完整性 Ws-reliable 訊息序列的完整性與機密性[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]必須使用 Ws-secure Conversation。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-188">R2301:To protect the integrity of a WS-Reliable Messaging sequence in addition to the integrity and confidentiality of individual messages, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires that WS-Secure Conversation must be used.</span></span>  
  
-   <span data-ttu-id="ae2bf-189">R2302:AWS-必須建立安全對話工作階段中之前建立 Ws-reliable 訊息序列。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-189">R2302:AWS-Secure Conversation session must be established prior to establishing WS-Reliable Messaging sequence(s).</span></span>  
  
-   <span data-ttu-id="ae2bf-190">R2303：如果 WS-Reliable 訊息序列的存留期超過 WS-Secure Conversation 工作階段的存留期，則使用 WS-Secure Conversation 建立的 `SecurityContextToken` 必須透過對應的 WS-Secure Conversation 更新繫結來加以更新。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-190">R2303: If the WS-Reliable Messaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>  
  
-   <span data-ttu-id="ae2bf-191">B2304:WS-可信賴傳訊序列或一組相互關聯的反向順序永遠會繫結至單一的 Ws-secureconversation 工作階段。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-191">B2304:WS-Reliable Messaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>  
  
     <span data-ttu-id="ae2bf-192">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 來源會在 `wsse:SecurityTokenReference` 訊息的項目擴充性區段中產生 `CreateSequence` 項目。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-192">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] source generates the `wsse:SecurityTokenReference` element in the element extensibility section of the `CreateSequence` message.</span></span>  
  
-   <span data-ttu-id="ae2bf-193">將工作與 Ws-secure Conversation，R2305:When`CreateSequence`訊息必須包含`wsse:SecurityTokenReference`項目。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-193">R2305:When composed with WS-Secure Conversation, a `CreateSequence` message must contain the `wsse:SecurityTokenReference` element.</span></span>  
  
## <a name="ws-reliable-messaging-ws-policy-assertion"></a><span data-ttu-id="ae2bf-194">WS-Reliable 訊息 WS-Policy 判斷提示</span><span class="sxs-lookup"><span data-stu-id="ae2bf-194">WS-Reliable Messaging WS-Policy Assertion</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-195"> 使用 WS-Reliable 訊息 WS-Policy 判斷提示 `wsrm:RMAssertion` 來描述各項端點功能。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-195"> uses WS-Reliable Messaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="ae2bf-196">下列清單列出適用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的條件約束：</span><span class="sxs-lookup"><span data-stu-id="ae2bf-196">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="ae2bf-197">B3001：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會將 `wsrm:RMAssertion` WS-Policy 判斷提示附加至 `wsdl:binding` 元素。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-197">B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] attaches `wsrm:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-198"> 同時支援附加至 `wsdl:binding` 和 `wsdl:port` 元素。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-198"> supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>  
  
-   <span data-ttu-id="ae2bf-199">B3002：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 支援下列選用的 WS-Reliable 訊息判斷提示屬性，並在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]`ReliableMessagingBindingElement` 上針對它們提供控制：</span><span class="sxs-lookup"><span data-stu-id="ae2bf-199">B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports the following optional properties of WS-Reliable Messaging assertion and provides control over them on the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]`ReliableMessagingBindingElement`:</span></span>  
  
    -   `wsrm:InactivityTimeout`  
  
    -   `wsrm:AcknowledgementInterval`  
  
     <span data-ttu-id="ae2bf-200">下列為範例。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-200">The following is an example.</span></span>  
  
    ```xml  
    <wsrm:RMAssertion>  
      <wsrm:InactivityTimeout Milliseconds="600000" />  
      <wsrm:AcknowledgementInterval Milliseconds="200" />  
    </wsrm:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliable-messaging-extension"></a><span data-ttu-id="ae2bf-201">WS-Reliable 訊息延伸的流量控制</span><span class="sxs-lookup"><span data-stu-id="ae2bf-201">Flow Control WS-Reliable Messaging Extension</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-202"> 會透過 WS-Reliable 訊息擴充性，針對序列訊息流量提供其他更嚴格的選擇性控制。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-202"> uses WS-Reliable Messaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>  
  
 <span data-ttu-id="ae2bf-203">藉由設定已啟用流量控制`ReliableSessionBindingElement`的`FlowControlEnabled``bool`屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-203">Flow control is enabled by setting the `ReliableSessionBindingElement`’s `FlowControlEnabled``bool` property to `true`.</span></span> <span data-ttu-id="ae2bf-204">下列清單列出適用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的條件約束：</span><span class="sxs-lookup"><span data-stu-id="ae2bf-204">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="ae2bf-205">B4001：一旦啟用了可信賴傳訊流量控制，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 就會在 `netrm:BufferRemaining` 標頭的項目擴充性中產生 `SequenceAcknowledgement` 項目。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-205">B4001: When Reliable Messaging Flow Control is enabled, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="ae2bf-206">B4002：一旦啟用了可信賴傳訊流量控制，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不會要求 `netrm:BufferRemaining` 中一定得存在 `SequenceAcknowledgement` 項目，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-206">B4002: When Reliable Messaging Flow Control is enabled, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not require a `netrm:BufferRemaining` element to be present in `SequenceAcknowledgement` header, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        http://fabrikam123.com/abc  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>  
        8  
      </netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="ae2bf-207">B4003：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 使用 `netrm:BufferRemaining` 來指出可信賴傳訊目的地可以緩衝處理的新訊息數量。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-207">B4003: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses `netrm:BufferRemaining` to indicate how many new messages the Reliable Messaging Destination can buffer.</span></span>  
  
-   <span data-ttu-id="ae2bf-208">B4004:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]可靠的訊息處理服務會先調節的可信賴傳訊目的地應用程式都能快速地接收訊息時，傳輸的訊息數目。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-208">B4004:The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging Service throttles the number of messages transmitted when the Reliable Messaging destination application cannot receive messages quickly.</span></span> <span data-ttu-id="ae2bf-209">可信賴傳訊目的地會緩衝處理訊息，並讓項目值降為 0。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-209">The Reliable Messaging destination buffers messages and the element’s value drops to 0.</span></span>  
  
-   <span data-ttu-id="ae2bf-210">B4005：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會產生介於 0 到 4096 (含) 之間的 `netrm:BufferRemaining` 整數值，並讀取介於 0 和 `xs:int` 的 `maxInclusive` 值 214748364 (含) 之間的整數值。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-210">B4005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>  
  
## <a name="message-exchange-patterns"></a><span data-ttu-id="ae2bf-211">訊息交換模式</span><span class="sxs-lookup"><span data-stu-id="ae2bf-211">Message Exchange Patterns</span></span>  
 <span data-ttu-id="ae2bf-212">本節將說明當不同訊息交換模式使用 WS-Reliable 訊息時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的行為。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-212">This section describes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]'s behavior when WS-Reliable Messaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="ae2bf-213">在每個訊息交換模式中，會考慮下列兩種部署案例：</span><span class="sxs-lookup"><span data-stu-id="ae2bf-213">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>  
  
-   <span data-ttu-id="ae2bf-214">不可定址的啟動器：啟動器位於防火牆後方，回應程式只能透過 HTTP 回應將訊息傳送至啟動器。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-214">Non-Addressable Initiator: Initiator is behind firewall; Responder can deliver messages to Initiator only on HTTP responses.</span></span>  
  
-   <span data-ttu-id="ae2bf-215">可定址的啟動器：可將 HTTP 要求同時傳送給啟動器與回應程式，亦即可建立兩個反向 HTTP 連線。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-215">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>  
  
### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="ae2bf-216">單向、不可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="ae2bf-216">One-way, Non-addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="ae2bf-217">繫結</span><span class="sxs-lookup"><span data-stu-id="ae2bf-217">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-218"> 透過在一個 HTTP 通道上使用一個序列的方式，提供單向的訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-218"> provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-219"> 會使用 HTTP 要求將所有訊息從 RMS 傳送至 RMD，並使用 HTTP 回應將所有訊息從 RMD 傳送至 RMS。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-219"> uses the HTTP requests to transmit all messages from the RMS to the RMD and the HTTP response to transmit all messages from the RMD to the RMS.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="ae2bf-220">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="ae2bf-220">CreateSequence Exchange</span></span>  
 <span data-ttu-id="ae2bf-221">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會產生不含提議的 `CreateSequence` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-221">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="ae2bf-222">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會在建立序列之前，確保 `CreateSequence` 不含提議。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-222">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="ae2bf-223">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會以 `CreateSequence` 訊息來回覆 `CreateSequenceResponse` 要求。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-223">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>  
  
#### <a name="sequenceacknowledgement"></a><span data-ttu-id="ae2bf-224">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="ae2bf-224">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="ae2bf-225">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會處理所有訊息回覆的認可，除了 `CreateSequence` 訊息與錯誤訊息以外。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-225">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="ae2bf-226">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式一律產生獨立認可，以同時回應序列和 `AckRequested` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-226">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder always generates a stand-alone acknowledgement in the response to both sequence and `AckRequested` messages.</span></span>  
  
#### <a name="terminatesequence-message"></a><span data-ttu-id="ae2bf-227">TerminateSequence 訊息</span><span class="sxs-lookup"><span data-stu-id="ae2bf-227">TerminateSequence message</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-228"> 會將 `TerminateSequence` 視為單向作業，代表 HTTP 回應具有空白主體與 HTTP 202 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-228"> treats `TerminateSequence` as a one-way operation, meaning the HTTP response has an empty body and HTTP 202 status code.</span></span>  
  
### <a name="one-way-addressable-initiator"></a><span data-ttu-id="ae2bf-229">單向、可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="ae2bf-229">One Way, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="ae2bf-230">繫結</span><span class="sxs-lookup"><span data-stu-id="ae2bf-230">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-231"> 透過在傳入與傳出 HTTP 通道上使用一個序列的方式，提供單向的訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-231"> provides a one-way message exchange pattern using one sequence over an inbound and an outbound Http channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-232"> 會使用 HTTP 要求來傳送所有訊息。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-232"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="ae2bf-233">所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-233">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="ae2bf-234">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="ae2bf-234">CreateSequence Exchange</span></span>  
 <span data-ttu-id="ae2bf-235">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會產生不含提議的 `CreateSequence` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-235">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="ae2bf-236">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會在建立序列之前，確保 `CreateSequence` 不含提議。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-236">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="ae2bf-237">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會透過以 `CreateSequenceResponse` 端點參考發出的 HTTP 要求來傳送 `ReplyTo` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-237">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder transmits the `CreateSequenceResponse` message on an HTTP request addressed with the `ReplyTo` endpoint reference.</span></span>  
  
### <a name="duplex-addressable-initiator"></a><span data-ttu-id="ae2bf-238">雙工、可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="ae2bf-238">Duplex, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="ae2bf-239">繫結</span><span class="sxs-lookup"><span data-stu-id="ae2bf-239">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-240"> 透過在一個傳入與一個傳出 HTTP 通道上使用兩個序列的方式，提供完全非同步的雙向訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-240"> provides a fully asynchronous two-way message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-241"> 會使用 HTTP 要求來傳送所有訊息。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-241"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="ae2bf-242">所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-242">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="ae2bf-243">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="ae2bf-243">CreateSequence Exchange</span></span>  
 <span data-ttu-id="ae2bf-244">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會產生內含提議的 `CreateSequence` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-244">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="ae2bf-245">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會在建立序列之前，確保 `CreateSequence` 包含提議。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-245">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-246"> 會依定址為 `CreateSequenceResponse` 之 `CreateSequence` 端點參考的 HTTP 要求來傳送 `ReplyTo`。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-246"> sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>  
  
#### <a name="sequence-lifetime"></a><span data-ttu-id="ae2bf-247">序列存留期</span><span class="sxs-lookup"><span data-stu-id="ae2bf-247">Sequence Lifetime</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-248"> 會將兩個序列視為一個全雙工工作階段。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-248"> treats the two sequences as one fully duplex session.</span></span>  
  
 <span data-ttu-id="ae2bf-249">在產生可挑剔某個序列的錯誤時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 預期遠端端點將同時挑剔兩個序列。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-249">Upon generating a fault that faults one sequence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="ae2bf-250">在讀取可挑剔某個序列的錯誤時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 將同時挑剔兩個序列。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-250">Upon reading a fault that faults one sequence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] faults both sequences.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-251"> 可關閉本身的傳出序列並繼續處理其傳入序列中的訊息。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-251"> can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="ae2bf-252">反之，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可以處理傳入序列的關閉作業並繼續傳送其傳出序列中的訊息。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-252">Conversely, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>  
  
### <a name="request-reply-non-addressable-initiator"></a><span data-ttu-id="ae2bf-253">要求-回覆、不可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="ae2bf-253">Request-Reply, Non-Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="ae2bf-254">繫結</span><span class="sxs-lookup"><span data-stu-id="ae2bf-254">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-255"> 透過在一個 HTTP 通道上使用兩個序列的方式，提供單向、要求-回覆的訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-255"> provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-256"> 會使用 HTTP 要求來傳送要求序列的訊息，並透過 HTTP 回應來傳送回覆序列的訊息。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-256"> uses the HTTP requests to transmit the request sequence’s messages and uses the HTTP responses to transmit the reply sequence’s messages.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="ae2bf-257">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="ae2bf-257">CreateSequence Exchange</span></span>  
 <span data-ttu-id="ae2bf-258">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會產生內含提議的 `CreateSequence` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-258">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="ae2bf-259">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會在建立序列之前，確保 `CreateSequence` 包含提議。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-259">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="ae2bf-260">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會以 `CreateSequence` 訊息來回覆 `CreateSequenceResponse` 要求。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-260">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="ae2bf-261">單向訊息</span><span class="sxs-lookup"><span data-stu-id="ae2bf-261">One-way Message</span></span>  
 <span data-ttu-id="ae2bf-262">為了成功完成單向訊息交換通訊協定，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會透過 HTTP 要求傳送要求序列訊息，並透過 HTTP 回應接收獨立的 `SequenceAcknowledgement` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-262">To complete a one-way message exchange protocol successfully, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="ae2bf-263">`SequenceAcknowledgement` 必須認可傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-263">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>  
  
 <span data-ttu-id="ae2bf-264">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式可透過認可、錯誤或是內含空白主體與 HTTP 202 狀態碼的回應來回覆要求。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-264">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder can reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="two-way-messages"></a><span data-ttu-id="ae2bf-265">雙向訊息</span><span class="sxs-lookup"><span data-stu-id="ae2bf-265">Two Way Messages</span></span>  
 <span data-ttu-id="ae2bf-266">為了成功完成雙向訊息交換通訊協定，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會透過 HTTP 要求傳送要求序列訊息，並透過 HTTP 回應接收回覆序列訊息。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-266">To complete a two way message exchange protocol successfully, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="ae2bf-267">回應中必須包含認可傳輸之要求序列訊息的 `SequenceAcknowledgement`。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-267">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>  
  
 <span data-ttu-id="ae2bf-268">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式可透過應用程式回覆、錯誤或是內含空本文與 HTTP 202 狀態碼的回應來回覆要求。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-268">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder can reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>  
  
 <span data-ttu-id="ae2bf-269">由於單向訊息與應用程式回覆時機的緣故，要求序列訊息的序號與回應訊息的序號彼此並未互相關聯。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-269">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>  
  
#### <a name="retrying-replies"></a><span data-ttu-id="ae2bf-270">重試回覆</span><span class="sxs-lookup"><span data-stu-id="ae2bf-270">Retrying Replies</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-271"> 仰賴 HTTP 要求-回覆相互關聯來執行雙向訊息交換通訊協定的相互關聯作業。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-271"> relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="ae2bf-272">由於這個緣故，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器不會在認可要求序列訊息時停止重試要求序列訊息，而會在 HTTP 回應內含認可、使用者訊息，或是錯誤時，才停止重試要求序列訊息。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-272">Because of this, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries an acknowledgement, user message, or fault.</span></span> <span data-ttu-id="ae2bf-273">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會在與回覆相互關聯之要求的 HTTP 要求階段上重試回覆。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-273">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder retries replies on the HTTP request leg of the request to which the reply is correlated.</span></span>  
  
#### <a name="lastmessage-exchange"></a><span data-ttu-id="ae2bf-274">LastMessage 交換</span><span class="sxs-lookup"><span data-stu-id="ae2bf-274">LastMessage Exchange</span></span>  
 <span data-ttu-id="ae2bf-275">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會在 HTTP 要求階段上產生及傳送主體空白的最後一則訊息。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-275">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates and transmits an empty bodied last message on the HTTP request leg.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-276"> 需要回應，但會忽略實際的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-276"> requires a response but ignores the actual response message.</span></span> <span data-ttu-id="ae2bf-277">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會透過回覆序列中主體空白的最後一則訊息，回覆要求序列中主體空白的最後一則訊息。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-277">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder replies to the request sequence’s empty-bodied last message with the reply sequence’s empty-bodied last message.</span></span>  
  
 <span data-ttu-id="ae2bf-278">如果 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式收到的最後一則訊息所包含的動作 URI 不是 http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage，則 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會透過最後一則訊息來回覆。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-278">If the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder receives a last message in which the action URI is not http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] replies with a last message.</span></span> <span data-ttu-id="ae2bf-279">在雙向訊息交換通訊協定的情況中，最後一則訊息包含應用程式訊息；在單向訊息交換通訊協定的情況中，最後一則訊息包含空白主體。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-279">In the case of a two-way message exchange protocol, the last message carries the application message; in the case of a one-way message exchange protocol, the last message is empty.</span></span>  
  
 <span data-ttu-id="ae2bf-280">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式不會要求針對回覆序列中主體空白的最後一則訊息進行認可。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-280">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder does not require an acknowledgement for the reply sequence’s empty-bodied last message.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="ae2bf-281">TerminateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="ae2bf-281">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="ae2bf-282">一旦所有要求都收到有效回覆，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會在 HTTP 要求階段上產生及傳送要求序列的 `TerminateSequence` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-282">When all requests have received a valid reply, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates and transmits the request sequence’s `TerminateSequence` message on the HTTP request leg.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-283"> 需要回應，但會忽略實際的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-283"> requires a response but ignores the actual response message.</span></span> <span data-ttu-id="ae2bf-284">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會透過回覆序列的 `TerminateSequence` 訊息，回覆要求序列的 `TerminateSequence` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-284">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder replies to the request sequence’s `TerminateSequence` message with the reply sequence’s `TerminateSequence` message.</span></span>  
  
 <span data-ttu-id="ae2bf-285">在正常的關機序列中，兩個 `TerminateSequence` 訊息會同時包含完整範圍的 `SequenceAcknowledgement`。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-285">In a normal shutdown sequence, both `TerminateSequence` messages carry a full range `SequenceAcknowledgement`.</span></span>  
  
### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="ae2bf-286">要求/回覆、可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="ae2bf-286">Request/Reply, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="ae2bf-287">繫結</span><span class="sxs-lookup"><span data-stu-id="ae2bf-287">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-288"> 透過在一個傳入與一個傳出 HTTP 通道上使用兩個序列的方式，提供要求-回覆訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-288"> provides a request-reply message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-289"> 會使用 HTTP 要求來傳送所有訊息。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-289"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="ae2bf-290">所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-290">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="ae2bf-291">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="ae2bf-291">CreateSequence Exchange</span></span>  
 <span data-ttu-id="ae2bf-292">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會產生內含提議的 `CreateSequence` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-292">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="ae2bf-293">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會在建立序列之前，確保 `CreateSequence` 包含提議。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-293">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ae2bf-294"> 會依定址為 `CreateSequenceResponse` 之 `CreateSequence` 端點參考的 HTTP 要求來傳送 `ReplyTo`。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-294"> sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>  
  
#### <a name="requestreply-correlation"></a><span data-ttu-id="ae2bf-295">要求/回覆相互關聯</span><span class="sxs-lookup"><span data-stu-id="ae2bf-295">Request/Reply Correlation</span></span>  
 <span data-ttu-id="ae2bf-296">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會確保所有應用程式要求訊息都帶有 `MessageId` 和 `ReplyTo` 端點參考。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-296">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator ensures all application request messages bear a `MessageId` and a `ReplyTo` endpoint reference.</span></span> <span data-ttu-id="ae2bf-297">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會將 `CreateSequence` 訊息的 `ReplyTo` 端點參照套用到每個應用程式要求訊息上。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-297">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator applies the `CreateSequence` message’s `ReplyTo` endpoint reference on each application request message.</span></span> <span data-ttu-id="ae2bf-298">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會要求傳入的要求訊息都帶有 `MessageId` 和 `ReplyTo`。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-298">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder requires that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span> <span data-ttu-id="ae2bf-299">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會確保 `CreateSequence` 和所有應用程式要求訊息的端點參照一模一樣。</span><span class="sxs-lookup"><span data-stu-id="ae2bf-299">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the endpoint reference’s URI of both the `CreateSequence` and all application request messages are identical.</span></span>

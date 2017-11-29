---
title: "Reliable Messaging Protocol 1.1 版"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 98fe8ac04b7ac811802466cf63c58ea4cebd791e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="reliable-messaging-protocol-version-11"></a><span data-ttu-id="c0fd7-102">Reliable Messaging Protocol 1.1 版</span><span class="sxs-lookup"><span data-stu-id="c0fd7-102">Reliable Messaging Protocol version 1.1</span></span>
<span data-ttu-id="c0fd7-103">本主題涵蓋了 WS-ReliableMessaging February 2007 (1.1 版) 通訊協定的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 實作詳細資料，這個通訊協定是使用 HTTP 傳輸來進行交互操作時所需的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-103">This topic covers [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] implementation details for the WS-ReliableMessaging February 2007 (version 1.1) protocol necessary for interoperation using the HTTP transport.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-104"> 遵循本主題所述 WS-ReliableMessaging 規格的條件約束及說明。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-104"> follows the WS-ReliableMessaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="c0fd7-105">請注意開始實作 Ws-reliablemessaging 1.1 版通訊協定[!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-105">Note that the WS-ReliableMessaging version 1.1 protocol is implemented starting with the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].</span></span>  
  
 <span data-ttu-id="c0fd7-106">WS-ReliableMessaging February 2007 通訊協定可透過 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 在 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> 中實作。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-106">The WS-ReliableMessaging February 2007 protocol is implemented in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>  
  
 <span data-ttu-id="c0fd7-107">為了方便起見，本主題將使用下列角色：</span><span class="sxs-lookup"><span data-stu-id="c0fd7-107">For convenience, the topic uses the following roles:</span></span>  
  
-   <span data-ttu-id="c0fd7-108">啟動器：啟動 WS-Reliable 訊息序列建立作業的用戶端。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-108">Initiator: The client that initiates WS-Reliable Message sequence creation.</span></span>  
  
-   <span data-ttu-id="c0fd7-109">回應程式：接收啟動器要求的服務。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-109">Responder: The service that receives the initiator's requests.</span></span>  
  
 <span data-ttu-id="c0fd7-110">本文件會使用下表的前置詞和命名空間。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-110">This document uses the prefixes and namespaces in the following table.</span></span>  
  
|<span data-ttu-id="c0fd7-111">前置詞</span><span class="sxs-lookup"><span data-stu-id="c0fd7-111">Prefix</span></span>|<span data-ttu-id="c0fd7-112">命名空間</span><span class="sxs-lookup"><span data-stu-id="c0fd7-112">Namespace</span></span>|  
|-|-|  
|<span data-ttu-id="c0fd7-113">wsrm</span><span class="sxs-lookup"><span data-stu-id="c0fd7-113">wsrm</span></span>|<span data-ttu-id="c0fd7-114">http://docs.oasis-open.org/ws-rx/wsrm/200702</span><span class="sxs-lookup"><span data-stu-id="c0fd7-114">http://docs.oasis-open.org/ws-rx/wsrm/200702</span></span>|  
|<span data-ttu-id="c0fd7-115">netrm</span><span class="sxs-lookup"><span data-stu-id="c0fd7-115">netrm</span></span>|<span data-ttu-id="c0fd7-116">http://schemas.microsoft.com/ws/2006/05/rm</span><span class="sxs-lookup"><span data-stu-id="c0fd7-116">http://schemas.microsoft.com/ws/2006/05/rm</span></span>|  
|<span data-ttu-id="c0fd7-117">s</span><span class="sxs-lookup"><span data-stu-id="c0fd7-117">s</span></span>|<span data-ttu-id="c0fd7-118">http://www.w3.org/2003/05/soap-envelope</span><span class="sxs-lookup"><span data-stu-id="c0fd7-118">http://www.w3.org/2003/05/soap-envelope</span></span>|  
|<span data-ttu-id="c0fd7-119">wsa</span><span class="sxs-lookup"><span data-stu-id="c0fd7-119">wsa</span></span>|<span data-ttu-id="c0fd7-120">http://schemas.xmlsoap.org/ws/2005/08/addressing</span><span class="sxs-lookup"><span data-stu-id="c0fd7-120">http://schemas.xmlsoap.org/ws/2005/08/addressing</span></span>|  
|<span data-ttu-id="c0fd7-121">wsse</span><span class="sxs-lookup"><span data-stu-id="c0fd7-121">wsse</span></span>|<span data-ttu-id="c0fd7-122">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd</span><span class="sxs-lookup"><span data-stu-id="c0fd7-122">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd</span></span>|  
|<span data-ttu-id="c0fd7-123">wsrmp</span><span class="sxs-lookup"><span data-stu-id="c0fd7-123">wsrmp</span></span>|<span data-ttu-id="c0fd7-124">http://docs.oasis-open.org/ws-rx/wsrmp/200702</span><span class="sxs-lookup"><span data-stu-id="c0fd7-124">http://docs.oasis-open.org/ws-rx/wsrmp/200702</span></span>|  
|<span data-ttu-id="c0fd7-125">netrmp</span><span class="sxs-lookup"><span data-stu-id="c0fd7-125">netrmp</span></span>|<span data-ttu-id="c0fd7-126">http://schemas.microsoft.com/ws-rx/wsrmp/200702</span><span class="sxs-lookup"><span data-stu-id="c0fd7-126">http://schemas.microsoft.com/ws-rx/wsrmp/200702</span></span>|  
|<span data-ttu-id="c0fd7-127">wsp</span><span class="sxs-lookup"><span data-stu-id="c0fd7-127">wsp</span></span>|<span data-ttu-id="c0fd7-128">(WS-Policy 1.2 或 WS-Policy 1.5)</span><span class="sxs-lookup"><span data-stu-id="c0fd7-128">(Either WS-Policy 1.2 or WS-Policy 1.5)</span></span>|  
  
## <a name="messaging"></a><span data-ttu-id="c0fd7-129">傳訊</span><span class="sxs-lookup"><span data-stu-id="c0fd7-129">Messaging</span></span>  
  
### <a name="sequence-creation"></a><span data-ttu-id="c0fd7-130">建立序列</span><span class="sxs-lookup"><span data-stu-id="c0fd7-130">Sequence Creation</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-131"> 會實作 `CreateSequence` 和 `CreateSequenceResponse` 訊息以建立可信賴傳訊序列。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-131"> implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable messaging sequence.</span></span> <span data-ttu-id="c0fd7-132">以下是適用的條件約束：</span><span class="sxs-lookup"><span data-stu-id="c0fd7-132">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="c0fd7-133">B1101：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器使用的端點參照與 `CreateSequence` 訊息的 `ReplyTo`、`AcksTo` 和 `Offer/Endpoint` 使用的端點參照一樣。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-133">B1101: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator uses the same endpoint reference as the `CreateSequence` message’s `ReplyTo`, `AcksTo` and `Offer/Endpoint`.</span></span>  
  
-   <span data-ttu-id="c0fd7-134">R1102：`AcksTo` 訊息中的 `ReplyTo`、`Offer/Endpoint` 和 `CreateSequence` 端點參照必須具有包含相同字串表示的位址值以符合八位元規格。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-134">R1102: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message must have address values with identical string representations such that they match the octet-wise.</span></span>  
  
    -   <span data-ttu-id="c0fd7-135">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式在建立序列之前，會先驗證 `AcksTo`、`ReplyTo` 和 `Endpoint` 端點參照的 URI 部分是否相同。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-135">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder verifies that the URI portion of the `AcksTo`, `ReplyTo` and `Endpoint` endpoint references are identical before creating a sequence.</span></span>  
  
-   <span data-ttu-id="c0fd7-136">R1103：`AcksTo` 訊息中的 `ReplyTo`、`Offer/Endpoint` 和 `CreateSequence` 端點參照應該具有相同的參照參數集合。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-136">R1103: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message should have the same set of reference parameters.</span></span>  
  
    -   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-137"> 不會強制執行，但會假定 `AcksTo` 上的 `ReplyTo`、`Offer/Endpoint` 和 `CreateSequence` 端點參照之參照參數都是一樣，並且使用來自 `ReplyTo` 端點參照的參照參數，以認可並與序列訊息對話。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-137"> does not enforce, but assumes that reference parameters of the `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references on `CreateSequence` are identical and uses reference parameters from the `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>  
  
-   <span data-ttu-id="c0fd7-138">B1104：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器不會在 `Expires` 訊息中產生選用的 `Offer/Expires` 或 `CreateSequence` 項目。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-138">B1104: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator does not generate the optional `Expires` or `Offer/Expires` element in the `CreateSequence` message.</span></span>  
  
-   <span data-ttu-id="c0fd7-139">B1105：在存取 `CreateSequence` 訊息時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會使用 `Expires` 項目中的 `CreateSequence` 值做為 `Expires` 項目中的 `CreateSequenceResponse` 值。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-139">B1105: When accessing the `CreateSequence` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder uses the `Expires` value in the `CreateSequence` element as the `Expires` value in the `CreateSequenceResponse` element.</span></span> <span data-ttu-id="c0fd7-140">否則，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式將讀取並忽略 `Expires` 和 `Offer/Expires` 值。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-140">Otherwise, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder reads and ignores the `Expires` and `Offer/Expires` values.</span></span>  
  
-   <span data-ttu-id="c0fd7-141">B1106：在存取 `CreateSequenceResponse` 訊息時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會讀取選用的 `Expires` 值但不會加以使用。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-141">B1106: When accessing the `CreateSequenceResponse` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator reads the optional `Expires` value but does not use it.</span></span>  
  
-   <span data-ttu-id="c0fd7-142">B1107：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器和回應程式一律在 `IncompleteSequenceBehavior` 和 `CreateSequence/Offer` 項目中產生選用的 `CreateSequenceResponse` 項目。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-142">B1107: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator and Responder always generate the optional `IncompleteSequenceBehavior` element in the `CreateSequence/Offer` and `CreateSequenceResponse` elements.</span></span>  
  
-   <span data-ttu-id="c0fd7-143">B1108：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 只會使用 `DiscardFollowingFirstGap` 項目中的 `NoDiscard` 和 `IncompleteSequenceBehavior` 值。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-143">B1108: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses only the `DiscardFollowingFirstGap` and `NoDiscard` values in the `IncompleteSequenceBehavior` element.</span></span>  
  
    -   <span data-ttu-id="c0fd7-144">WS-ReliableMessaging 會使用 `Offer` 機制來建立兩個反向關聯序列以形成工作階段。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-144">WS-ReliableMessaging utilizes the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>  
  
-   <span data-ttu-id="c0fd7-145">B1109：如果 `CreateSequence` 包含 `Offer` 項目，單向 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會透過不含 `CreateSequenceResponse` 項目的 `Accept` 來回應以拒絕提供的序列。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-145">B1109: If `CreateSequence` contains an `Offer` element, the one way [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder rejects the offered sequence by responding with a `CreateSequenceResponse` without an `Accept` element.</span></span>  
  
-   <span data-ttu-id="c0fd7-146">B1110：如果可信賴傳訊回應程式拒絕了提供的序列，則 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會挑出新建立序列的錯誤。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-146">B1110: If a Reliable Messaging Responder rejects the offered sequence, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator faults the newly established sequence.</span></span>  
  
-   <span data-ttu-id="c0fd7-147">B1111：如果 `CreateSequence` 不包含 `Offer` 項目，雙向 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會透過 `CreateSequenceRefused` 錯誤來回應以拒絕提供的序列。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-147">B1111: If `CreateSequence` does not contain an `Offer` element, the two-way [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder rejects the offered sequence by responding with a `CreateSequenceRefused` fault.</span></span>  
  
-   <span data-ttu-id="c0fd7-148">R1112：當兩個反向序列都是透過 `Offer` 機制建立時，`[address]` 端點參照之 `CreateSequenceResponse/Accept/AcksTo` 屬性的每個位元組必須完全符合 `CreateSequence` 訊息之目的 URI 的每個位元組。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-148">R1112: When two converse sequences are established using the `Offer` mechanism, the `[address]` property of the `CreateSequenceResponse/Accept/AcksTo` endpoint reference must match the destination URI of the `CreateSequence` message byte for byte.</span></span>  
  
-   <span data-ttu-id="c0fd7-149">R1113：當兩個反向序列都是透過 `Offer` 機制建立時，從啟動器流向回應程式之雙邊序列上的所有訊息必須傳送至相同的端點參照。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-149">R1113: When two converse sequences are established using the `Offer` mechanism, all messages on both sequences flowing from the Initiator to the Responder must be sent to the same endpoint reference.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-150"> 使用 WS-ReliableMessaging 在啟動器與回應程式之間建立可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-150"> uses WS-ReliableMessaging to establish reliable sessions between the Initiator and the Responder.</span></span> <span data-ttu-id="c0fd7-151">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-ReliableMessaging 實作會針對單向、要求-回覆與全雙工訊息模式提供可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-151">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-ReliableMessaging implementation provides a reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="c0fd7-152">`Offer` 和 `CreateSequence` 上的 WS-ReliableMessaging `CreateSequenceResponse` 機制可讓您建立兩個相互關聯的反向序列，並提供適用於所有訊息端點的工作階段通訊協定。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-152">The WS-ReliableMessaging `Offer` mechanism on `CreateSequence` and `CreateSequenceResponse` lets you establish two correlated converse sequences and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="c0fd7-153">由於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會針對此類工作階段提供安全性保證，包含工作階段完整性的端對端保護，因此可以實際地確保訊息會抵達預定的相同目的地。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-153">Because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure that messages intended for the same party arrive at the same destination.</span></span> <span data-ttu-id="c0fd7-154">這麼做也可以針對應用程式訊息進行 "piggy-backing" 的序列認可作業。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-154">This also allows "piggy-backing" of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="c0fd7-155">因此，條件約束 R1102、 R1112 和 R1113 適用於[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-155">Therefore, constraints R1102, R1112, and R1113 apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="c0fd7-156">`CreateSequence` 訊息的範例。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-156">An example of a `CreateSequence` message.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequence</wsa:Action>  
    <wsa:MessageID>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:MessageID>  
    <wsa:ReplyTo>  
        <wsa:Address>http://Business456.com/clientA</wsa:Address>   
    </wsa:ReplyTo>  
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CreateSequence>  
      <wsrm:AcksTo>  
        <wsa:Address>http://Business456.com/clientA</wsa:Address>  
      </wsrm:AcksTo>  
      <wsrm:Offer>  
        <wsrm:Identifier>urn:uuid:066b4730-fc82-458a-a5c1-210be4fb4e4e</wsrm:Identifier>  
        <wsrm:Endpoint>  
          <wsa:Address>http://Business456.com/clientA</wsa:Address>  
        </wsrm:Endpoint>  
        <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>  
      </wsrm:Offer>  
    </wsrm:CreateSequence>  
  </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="c0fd7-157">`CreateSequenceResponse` 訊息的範例。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-157">An example of a `CreateSequenceResponse` message.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequenceResponse</wsa:Action>  
    <wsa:RelatesTo>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:RelatesTo>  
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CreateSequenceResponse>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>  
      <wsrm:Accept>  
        <wsrm:AcksTo>  
          <wsa:Address>http://BusinessABC.com/serviceA</wsa:Address>  
        </wsrm:AcksTo>  
      </wsrm:Accept>  
    </wsrm:CreateSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="closing-a-sequence"></a><span data-ttu-id="c0fd7-158">關閉序列</span><span class="sxs-lookup"><span data-stu-id="c0fd7-158">Closing a Sequence</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-159"> 會使用 `CloseSequence` 和 `CloseSequenceResponse` 訊息支援由來源啟始的可信賴傳訊關閉作業。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-159"> uses the `CloseSequence` and `CloseSequenceResponse` messages for a Reliable Messaging source-initiated shutdown.</span></span> <span data-ttu-id="c0fd7-160">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可信賴傳訊目的地不會啟始關閉作業，而且 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可信賴傳訊來源不支援從目的地啟始的可信賴傳訊關閉作業。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-160">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging destination does not initiate shutdown and the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging source does not support a Reliable Messaging destination-initiated shutdown.</span></span> <span data-ttu-id="c0fd7-161">以下是適用的條件約束：</span><span class="sxs-lookup"><span data-stu-id="c0fd7-161">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="c0fd7-162">B1201：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可信賴傳訊來源一律傳送 `CloseSequence` 訊息來關閉序列。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-162">B1201: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging source always sends a `CloseSequence` message to shut down the sequence.</span></span>  
  
-   <span data-ttu-id="c0fd7-163">B1202：可信賴傳訊來源會在傳送 `CloseSequence` 訊息之前，等候整個序列訊息的認可。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-163">B1202: The Reliable Messaging source waits for acknowledgement of the full range of sequence messages before sending the `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="c0fd7-164">B1203：可信賴傳訊來源一律包含選用的 `LastMsgNumber` 項目 (除非序列不包含訊息)。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-164">B1203: The Reliable Messaging source always includes the optional `LastMsgNumber` element unless the sequence does not contain messages.</span></span>  
  
-   <span data-ttu-id="c0fd7-165">R1204：可信賴傳訊目的地不可以藉由傳送 `CloseSequence` 訊息來啟始關閉作業。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-165">R1204: The Reliable Messaging destination must not initiate shutdown by sending a `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="c0fd7-166">B1205：在收到 `CloseSequence` 訊息時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可信賴傳訊來源會將序列視為不完整並傳送錯誤。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-166">B1205: Upon receiving a `CloseSequence` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging source considers the sequence incomplete and sends a fault.</span></span>  
  
 <span data-ttu-id="c0fd7-167">`CloseSequence` 訊息的範例。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-167">An example of a `CloseSequence` message.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequence</wsa:Action>  
    <wsa:MessageID>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:MessageID>  
    <wsa:ReplyTo>  
      <wsa:Address>http://Business456.com/clientA</wsa:Address>  
    </wsa:ReplyTo>  
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CloseSequence>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>  
    </wsrm:CloseSequence>  
  </s:Body>  
</s:Envelope>  
Example CloseSequenceResponse message:  
<s:Envelope>  
  <s:Header>  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>  
      <wsrm:Final></wsrm:Final>  
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequenceResponse</wsa:Action>  
    <wsa:RelatesTo>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:RelatesTo>  
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CloseSequenceResponse>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
    </wsrm:CloseSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="sequence-termination"></a><span data-ttu-id="c0fd7-168">終止序列</span><span class="sxs-lookup"><span data-stu-id="c0fd7-168">Sequence Termination</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-169"> 在完成了 `TerminateSequence/TerminateSequenceResponse` 交握之後，主要使用 `CloseSequence/CloseSequenceResponse` 交握。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-169"> primarily uses the `TerminateSequence/TerminateSequenceResponse` handshake after completing the `CloseSequence/CloseSequenceResponse` handshake.</span></span> <span data-ttu-id="c0fd7-170">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可信賴傳訊目的地不會啟始終止作業，而且可信賴傳訊來源不支援從目的地啟始的可信賴傳訊終止作業。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-170">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging destination does not initiate termination and the Reliable Messaging source does not support a Reliable Messaging destination-initiated termination.</span></span> <span data-ttu-id="c0fd7-171">以下是適用的條件約束：</span><span class="sxs-lookup"><span data-stu-id="c0fd7-171">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="c0fd7-172">B1301：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器只會在成功完成 `TerminateSequence` 交握之後，才傳送 `CloseSequence/CloseSequenceResponse` 訊息。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-172">B1301: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator only sends the `TerminateSequence` message after the successful completion of the `CloseSequence/CloseSequenceResponse` handshake.</span></span>  
  
-   <span data-ttu-id="c0fd7-173">R1302：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會針對特定序列，驗證所有 `LastMsgNumber` 和 `CloseSequence` 訊息上的 `TerminateSequence` 項目是否一致。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-173">R1302: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] validates that the `LastMsgNumber` element is consistent across all `CloseSequence` and `TerminateSequence` messages for a given sequence.</span></span> <span data-ttu-id="c0fd7-174">也就是說，`LastMsgNumber` 不是不存在於所有 `CloseSequence` 和 `TerminateSequence` 訊息上，就是存在於所有 `CloseSequence` 和 `TerminateSequence` 訊息上而且全部一樣。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-174">This means that `LastMsgNumber` is either not present on all `CloseSequence` and `TerminateSequence` messages, or it is present and identical on all `CloseSequence` and `TerminateSequence` messages.</span></span>  
  
-   <span data-ttu-id="c0fd7-175">B1303：在 `TerminateSequence` 交握之後收到 `CloseSequence/CloseSequenceResponse` 訊息時，可信賴傳訊目的地會以 `TerminateSequenceResponse` 訊息來回應。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-175">B1303: When receiving a `TerminateSequence` message after the `CloseSequence/CloseSequenceResponse` handshake, the Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="c0fd7-176">由於可信賴傳訊來源在傳送 `TerminateSequence` 訊息之前已經獲得最後的認可，因此可信賴傳訊目的地毫無疑問地知道序列已結束並立即回收資源。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-176">Because the Reliable Messaging source has the final acknowledgement before sending the `TerminateSequence` message, the Reliable Messaging destination knows without doubt that the sequence ends, and reclaims resources immediately.</span></span>  
  
-   <span data-ttu-id="c0fd7-177">B1304：在 `TerminateSequence` 交握之前收到 `CloseSequence/CloseSequenceResponse` 訊息時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可信賴傳訊目的地會以 `TerminateSequenceResponse` 訊息來回應。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-177">B1304: When receiving a `TerminateSequence` message prior to the `CloseSequence/CloseSequenceResponse` handshake, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="c0fd7-178">如果可信賴傳訊目的地判斷序列中沒有任何不一致的項目，則可信賴傳訊目的地會等候應用程式目的地指定的時間一到再回收資源，以便讓用戶端有機會接收最後的認可。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-178">If the Reliable Messaging destination determines that there are no inconsistencies in the sequence, the Reliable Messaging destination waits for an application destination-specified time before reclaiming resources, to allow the client the chance to receive the final acknowledgement.</span></span> <span data-ttu-id="c0fd7-179">否則，可信賴傳訊目的地會立即回收資源並引發 `Faulted` 事件以向應用程式目的地指出序列是在不確定的情況下結束。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-179">Otherwise, the Reliable Messaging destination reclaims resources immediately and indicates to the application destination that the sequence ends with doubt by raising the `Faulted` event.</span></span>  
  
 <span data-ttu-id="c0fd7-180">`TerminateSequence` 訊息的範例。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-180">An example of a `TerminateSequence` message.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequence</wsa:Action>  
    <wsa:MessageID>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:MessageID>  
    <wsa:ReplyTo>  
      <wsa:Address>http://Business456.com/clientA</wsa:Address>  
    </wsa:ReplyTo>  
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:TerminateSequence>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>  
      </wsrm:TerminateSequence>  
  </s:Body>  
</s:Envelope>  
Example TerminateSequenceResponse message:  
<s:Envelope>  
  <s:Header>  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>  
      <wsrm:Final></wsrm:Final>  
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequenceResponse</wsa:Action>  
    <wsa:RelatesTo>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:RelatesTo>  
    <wsa:To s:mustUnderstand="1">://Business456.com/clientA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:TerminateSequenceResponse>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
    </wsrm:TerminateSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="sequences"></a><span data-ttu-id="c0fd7-181">序列</span><span class="sxs-lookup"><span data-stu-id="c0fd7-181">Sequences</span></span>  
 <span data-ttu-id="c0fd7-182">下列清單列出適用於序列的條件約束：</span><span class="sxs-lookup"><span data-stu-id="c0fd7-182">The following is a list of constraints that apply to sequences:</span></span>  
  
-   <span data-ttu-id="c0fd7-183">B1401:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]會產生並存取序號大於`xs:long`的最大包含值，9223372036854775807。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-183">B1401:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>  
  
 <span data-ttu-id="c0fd7-184">`Sequence` 標頭的範例。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-184">An example of a `Sequence` header.</span></span>  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a><span data-ttu-id="c0fd7-185">要求認可</span><span class="sxs-lookup"><span data-stu-id="c0fd7-185">Request Acknowledgement</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-186"> 會使用 `AckRequested` 標頭做為 Keep-Alive 機制。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-186"> uses the `AckRequested` header as a keep-alive mechanism.</span></span>  
  
 <span data-ttu-id="c0fd7-187">`AckRequested` 標頭的範例。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-187">An example of an `AckRequested` header.</span></span>  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a><span data-ttu-id="c0fd7-188">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="c0fd7-188">SequenceAcknowledgement</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-189"> 會針對 WS-Reliable 訊息所提供的序列認可使用 "piggy-back" 機制。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-189"> uses a "piggy-back" mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span> <span data-ttu-id="c0fd7-190">以下是適用的條件約束：</span><span class="sxs-lookup"><span data-stu-id="c0fd7-190">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="c0fd7-191">R1601： 當兩個反向序列會建立使用`Offer`機制，`SequenceAcknowledgement`標頭可能包含在傳送給預定收件者的任何應用程式訊息。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-191">R1601: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span> <span data-ttu-id="c0fd7-192">遠端端點必須能夠存取以 Piggyback 方式傳送的 `SequenceAcknowledgement` 標頭。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-192">The remote endpoint must be able to access a piggybacked `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="c0fd7-193">B1602：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不會產生包含 `SequenceAcknowledgement` 元素的 `Nack` 標頭。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-193">B1602: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate `SequenceAcknowledgement` headers that contain `Nack` elements.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-194"> 會驗證每個 `Nack` 元素是否都包含序號，但是另一方面會忽略 `Nack` 元素與值。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-194"> validates that each `Nack` element contains a sequence number, but otherwise ignores the `Nack` element and value.</span></span>  
  
 <span data-ttu-id="c0fd7-195">`SequenceAcknowledgement` 標頭的範例。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-195">An example of a `SequenceAcknowledgement` header.</span></span>  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="c0fd7-196">WS-ReliableMessaging 錯誤</span><span class="sxs-lookup"><span data-stu-id="c0fd7-196">WS-ReliableMessaging Faults</span></span>  
 <span data-ttu-id="c0fd7-197">下列清單列出適用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 之 WS-ReliableMessaging 錯誤實作的條件約束：</span><span class="sxs-lookup"><span data-stu-id="c0fd7-197">The following is a list of constraints that apply to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation of WS-ReliableMessaging faults.</span></span> <span data-ttu-id="c0fd7-198">以下是適用的條件約束：</span><span class="sxs-lookup"><span data-stu-id="c0fd7-198">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="c0fd7-199">B1701:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]不會產生`MessageNumberRollover`錯誤。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-199">B1701: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate `MessageNumberRollover` faults.</span></span>  
  
-   <span data-ttu-id="c0fd7-200">B1702：在 SOAP 1.2 中，當服務端點到達其連線限制，而且無法處理新的連線時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 就會產生巢狀 `CreateSequenceRefused` 錯誤子代碼 `netrm:ConnectionLimitReached`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-200">B1702: Over SOAP 1.2, when the service endpoint reaches its connection limit and cannot process new connections, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates a nested `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action>http://docs.oasis-open.org/ws-rx/wsrm/200702/fault</wsa:Action>  
  </s:Header>  
  <s:Body>  
    <s:Fault>  
      <s:Code>  
        <s:Value>s:Receiver</s:Value>  
        <s:Subcode>  
          <s:Value>wsrm:CreateSequenceRefused</s:Value>  
          <s:Subcode>  
            <s:Value>netrm:ConnectionLimitReached</s:Value>  
          </s:Subcode>  
        </s:Subcode>  
      </s:Code>  
      <s:Reason>  
        <s:Text xml:lang="en">Server 'http://BusinessABC.com/serviceA' is too busy to process this request. Try again later.</s:Text>  
      </s:Reason>  
    </s:Fault>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="ws-addressing-faults"></a><span data-ttu-id="c0fd7-201">WS-Addressing 錯誤</span><span class="sxs-lookup"><span data-stu-id="c0fd7-201">WS-Addressing Faults</span></span>  
 <span data-ttu-id="c0fd7-202">由於 WS-ReliableMessaging 是使用 WS-Addressing，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-ReliableMessaging 實作可能會產生並傳送 WS-Addressing 錯誤。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-202">Because WS-ReliableMessaging uses WS-Addressing, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-ReliableMessaging implementation may generate and transmit WS-Addressing faults.</span></span> <span data-ttu-id="c0fd7-203">本節涵蓋 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 所明確產生並在 WS-ReliableMessaging 層加以傳送的 WS-Addressing 錯誤：</span><span class="sxs-lookup"><span data-stu-id="c0fd7-203">This section covers the WS-Addressing faults that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] explicitly generates and transmits at the WS-ReliableMessaging layer:</span></span>  
  
-   <span data-ttu-id="c0fd7-204">B1801:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]會產生並傳輸`Message Addressing Header Required`當下列其中一項條件成立時，發生錯誤：</span><span class="sxs-lookup"><span data-stu-id="c0fd7-204">B1801:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and transmits the `Message Addressing Header Required` fault when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="c0fd7-205">`CreateSequence`、`CloseSequence` 或 `TerminateSequence` 訊息缺少 `MessageId` 標頭。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-205">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `MessageId` header.</span></span>  
  
    -   <span data-ttu-id="c0fd7-206">`CreateSequence`、`CloseSequence` 或 `TerminateSequence` 訊息缺少 `ReplyTo` 標頭。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-206">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `ReplyTo` header.</span></span>  
  
    -   <span data-ttu-id="c0fd7-207">`CreateSequenceResponse`、`CloseSequenceResponse` 或 `TerminateSequenceResponse` 訊息缺少 `RelatesTo` 標頭。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-207">A `CreateSequenceResponse`, `CloseSequenceResponse`, or `TerminateSequenceResponse` message is missing a `RelatesTo` header.</span></span>  
  
-   <span data-ttu-id="c0fd7-208">B1802:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]會產生並傳輸`Endpoint Unavailable`錯誤，表示沒有任何接聽的端點可以根據檢查結果中的定位標頭的順序進行處理`CreateSequence`訊息。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-208">B1802:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and transmits the `Endpoint Unavailable` fault to indicate there is no endpoint listening that can process the sequence based on examination of the addressing headers in the `CreateSequence` message.</span></span>  
  
## <a name="protocol-composition"></a><span data-ttu-id="c0fd7-209">通訊協定組合</span><span class="sxs-lookup"><span data-stu-id="c0fd7-209">Protocol Composition</span></span>  
  
### <a name="composition-with-ws-addressing"></a><span data-ttu-id="c0fd7-210">與 WS-Addressing 組合</span><span class="sxs-lookup"><span data-stu-id="c0fd7-210">Composition with WS-Addressing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-211"> 支援兩種版本的 WS-Addressing：WS-Addressing 2004/08 [WS-ADDR] 和 W3C WS-Addressing 1.0 建議 [WS-ADDR-CORE] 和 [WS-ADDR-SOAP]。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-211"> supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>  
  
 <span data-ttu-id="c0fd7-212">儘管 WS-ReliableMessaging 規格只提到 WS-Addressing 2004/08，它並未限制要使用的 WS-Addressing 版本。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-212">While the WS-ReliableMessaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="c0fd7-213">下列清單列出適用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的條件約束：</span><span class="sxs-lookup"><span data-stu-id="c0fd7-213">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="c0fd7-214">R2101：WS-Addressing 2004/08 和 WS-Addressing 1.0 皆可搭配 WS-Reliable 訊息一起使用。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-214">R2101: Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="c0fd7-215">R2102：單一版本的 WS-Addressing 必須透過 `Offer` 機制，用在整個特定的 WS-ReliableMessaging 序列或是一對相關聯的反向序列上。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-215">R2102: A single version of WS-Addressing must be used throughout a given WS-ReliableMessaging sequence or a pair of converse sequences correlated by using the `Offer` mechanism.</span></span>  
  
### <a name="composition-with-soap"></a><span data-ttu-id="c0fd7-216">與 SOAP 組合</span><span class="sxs-lookup"><span data-stu-id="c0fd7-216">Composition with SOAP</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-217"> 同時支援 SOAP 1.1 和 SOAP 1.2 搭配 WS-Reliable 訊息一起使用。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-217"> supports the use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="c0fd7-218">與 WS-Security 和 WS-SecureConversation 組合</span><span class="sxs-lookup"><span data-stu-id="c0fd7-218">Composition with WS-Security and WS-SecureConversation</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-219"> 透過安全傳輸 (HTTPS)、與 WS-Security 組合，以及與 WS-Secure Conversation 組合，為 WS-ReliableMessaging 序列提供保護。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-219"> provides protection for WS-ReliableMessaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="c0fd7-220">WS-ReliableMessaging 1.1 通訊協定、WS-Security 1.1 和 WS-Secure Conversation 1.3 通訊協定應該一併使用。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-220">The WS-ReliableMessaging 1.1 protocol, WS-Security 1.1 and WS-Secure Conversation 1.3 protocol should be used together.</span></span> <span data-ttu-id="c0fd7-221">下列清單列出適用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的條件約束：</span><span class="sxs-lookup"><span data-stu-id="c0fd7-221">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="c0fd7-222">R2301：為了在個別訊息的完整性與機密性之外保護 WS-ReliableMessaging 序列的完整性，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 要求必須使用 WS-Secure Conversation。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-222">R2301: To protect the integrity of a WS-ReliableMessaging sequence in addition to the integrity and confidentiality of individual messages, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires that WS-Secure Conversation must be used.</span></span>  
  
-   <span data-ttu-id="c0fd7-223">R2302:AWS-必須在建立了 Ws-reliablemessaging 序列前建立安全對話工作階段。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-223">R2302:AWS-Secure Conversation session must be established prior to establishing WS-ReliableMessaging sequence(s).</span></span>  
  
-   <span data-ttu-id="c0fd7-224">R2303：如果 WS-ReliableMessaging 序列的存留期超過 WS-Secure Conversation 工作階段的存留期，則使用 WS-Secure Conversation 建立的 `SecurityContextToken` 必須透過對應的 WS-Secure Conversation 更新繫結來加以更新。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-224">R2303: If the WS-ReliableMessaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>  
  
-   <span data-ttu-id="c0fd7-225">B2304:WS-Ws-reliablemessaging 序列或是一對的相互關聯的反向順序永遠會繫結至單一的 Ws-secureconversation 工作階段。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-225">B2304:WS-ReliableMessaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>  
  
-   <span data-ttu-id="c0fd7-226">R2305：一旦與 WS-Secure Conversation 組合，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式就會要求 `CreateSequence` 訊息必須包含 `wsse:SecurityTokenReference` 項目和 `wsrm:UsesSequenceSTR` 標頭。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-226">R2305: When composed with WS-Secure Conversation, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] responder requires that the `CreateSequence` message contain the `wsse:SecurityTokenReference` element and the `wsrm:UsesSequenceSTR` header.</span></span>  
  
 <span data-ttu-id="c0fd7-227">`UsesSequenceSTR` 標頭的範例。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-227">An example of a `UsesSequenceSTR` header.</span></span>  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a><span data-ttu-id="c0fd7-228">與 SSL/TLS 組合</span><span class="sxs-lookup"><span data-stu-id="c0fd7-228">Composition with SSL/TLS sessions</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-229"> 不支援與 SSL/TLS 工作階段的組合：</span><span class="sxs-lookup"><span data-stu-id="c0fd7-229"> does not support composition with SSL/TLS sessions:</span></span>  
  
-   <span data-ttu-id="c0fd7-230">B2401：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不會產生 `wsrm:UsesSequenceSSL` 標頭。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-230">B2401: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate the `wsrm:UsesSequenceSSL` header.</span></span>  
  
-   <span data-ttu-id="c0fd7-231">R2402：可信賴傳訊啟動器不可以將帶有 `CreateSequence` 標頭的 `wsrm:UsesSequenceSSL` 訊息傳送到 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式中。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-231">R2402: A Reliable Messaging Initiator must not send a `CreateSequence` message with a `wsrm:UsesSequenceSSL` header to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder.</span></span>  
  
### <a name="composition-with-ws-policy"></a><span data-ttu-id="c0fd7-232">與 WS-Policy 組合</span><span class="sxs-lookup"><span data-stu-id="c0fd7-232">Composition with WS-Policy</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-233"> 支援兩種版本的 WS-Policy：WS-Policy 1.2 和 WS-Policy 1.5。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-233"> supports two versions of WS-Policy: WS-Policy 1.2 and WS-Policy 1.5.</span></span>  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a><span data-ttu-id="c0fd7-234">WS-ReliableMessaging WS-Policy 判斷提示</span><span class="sxs-lookup"><span data-stu-id="c0fd7-234">WS-ReliableMessaging WS-Policy Assertion</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-235"> 使用 WS-ReliableMessaging WS-Policy 判斷提示 `wsrm:RMAssertion` 來描述各項端點功能。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-235"> uses WS-ReliableMessaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="c0fd7-236">下列清單列出適用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的條件約束：</span><span class="sxs-lookup"><span data-stu-id="c0fd7-236">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="c0fd7-237">B3001：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會將 `wsrmn:RMAssertion` WS-Policy 判斷提示附加至 `wsdl:binding` 元素。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-237">B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] attaches `wsrmn:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-238"> 同時支援附加至 `wsdl:binding` 和 `wsdl:port` 元素。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-238"> supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>  
  
-   <span data-ttu-id="c0fd7-239">B3002：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 永遠不會產生 `wsp:Optional` 標記。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-239">B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] never generates the `wsp:Optional` tag.</span></span>  
  
-   <span data-ttu-id="c0fd7-240">B3003：存取 `wsrmp:RMAssertion` WS-Policy 判斷提示時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會忽略 `wsp:Optional` 標記並將 WS-RM 原則視為強制執行原則。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-240">B3003: When accessing the `wsrmp:RMAssertion` WS-Policy Assertion, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignores the `wsp:Optional` tag and treats the WS-RM policy as mandatory.</span></span>  
  
-   <span data-ttu-id="c0fd7-241">R3004：由於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 無法與 SSL/TLS 工作階段組合，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不會接受用來指定 `wsrmp:SequenceTransportSecurity` 的原則。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-241">R3004: Because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not compose with SSL/TLS sessions, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not accept policy that specifies `wsrmp:SequenceTransportSecurity`.</span></span>  
  
-   <span data-ttu-id="c0fd7-242">B3005：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 一律產生 `wsrmp:DeliveryAssurance` 項目。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-242">B3005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] always generates the `wsrmp:DeliveryAssurance` element.</span></span>  
  
-   <span data-ttu-id="c0fd7-243">B3006：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 一律指定 `wsrmp:ExactlyOnce` 傳遞保證。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-243">B3006: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] always specifies the `wsrmp:ExactlyOnce` delivery assurance.</span></span>  
  
-   <span data-ttu-id="c0fd7-244">B3007：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會產生並讀取下列 WS-ReliableMessaging 判斷提示屬性，並透過 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]`ReliableSessionBindingElement` 針對這些屬性提供控制權：</span><span class="sxs-lookup"><span data-stu-id="c0fd7-244">B3007: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and reads the following properties of the WS-ReliableMessaging assertion and provides control over them on the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]`ReliableSessionBindingElement`:</span></span>  
  
    -   `netrmp:InactivityTimeout`  
  
    -   `netrmp:AcknowledgementInterval`  
  
     <span data-ttu-id="c0fd7-245">`RMAssertion` 的範例。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-245">An example of a `RMAssertion`.</span></span>  
  
    ```xml  
    <wsrmp:RMAssertion>  
      <wsp:Policy>  
        <wsrmp:SequenceSTR/>  
        <wsrmp:DeliveryAssurance>  
          <wsp:Policy>  
            <wsrmp:ExactlyOnce/>  
            <wsrmp:InOrder/>  
          </wsp:Policy>  
        </wsrmp:DeliveryAssurance>  
      </wsp:Policy>  
      <netrmp:InactivityTimeout Milliseconds="600000"/>  
      <netrmp:AcknowledgementInterval Milliseconds="200"/>  
    </wsrmp:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliablemessaging-extension"></a><span data-ttu-id="c0fd7-246">WS-ReliableMessaging 延伸的流量控制</span><span class="sxs-lookup"><span data-stu-id="c0fd7-246">Flow Control WS-ReliableMessaging Extension</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-247"> 會透過 WS-ReliableMessaging 擴充性，針對序列訊息流量提供其他更嚴格的選擇性控制。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-247"> uses WS-ReliableMessaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>  
  
 <span data-ttu-id="c0fd7-248">藉由設定已啟用流量控制`ReliableSessionBindingElement`的`FlowControlEnabled``boolean`屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-248">Flow control is enabled by setting the `ReliableSessionBindingElement`’s `FlowControlEnabled``boolean` property to `true`.</span></span> <span data-ttu-id="c0fd7-249">下列清單列出適用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的條件約束：</span><span class="sxs-lookup"><span data-stu-id="c0fd7-249">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="c0fd7-250">B4001：一旦啟用了可信賴傳訊流量控制，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會在 `netrm:BufferRemaining` 標頭的項目擴充性中產生 `SequenceAcknowledgement` 項目，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-250">B4001: When Reliable Messaging Flow Control is enabled, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="c0fd7-251">B4002：即使啟用了可信賴傳訊流量控制，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 也不需要 `netrm:BufferRemaining` 標頭中的 `SequenceAcknowledgement` 項目。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-251">B4002: Even when Reliable Messaging Flow Control is enabled, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not require a `netrm:BufferRemaining` element in the `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="c0fd7-252">B4003：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可信賴傳訊目的地使用 `netrm:BufferRemaining` 來指出能夠緩衝處理的新訊息數目。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-252">B4003: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging Destination uses `netrm:BufferRemaining` to indicate how many new messages it can buffer.</span></span>  
  
-   <span data-ttu-id="c0fd7-253">已啟用 B4004:When 可信賴傳訊流量控制，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]可信賴傳訊來源會使用值`netrm:BufferRemaining`節流訊息傳輸。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-253">B4004:When Reliable Messaging Flow Control is enabled, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging Source uses the value of `netrm:BufferRemaining` to throttle message transmission.</span></span>  
  
-   <span data-ttu-id="c0fd7-254">B4005：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會產生介於 0 到 4096 (含) 之間的 `netrm:BufferRemaining` 整數值，並讀取介於 0 和 `xs:int` 的 `maxInclusive` 值 214748364 (含) 之間的整數值。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-254">B4005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>  
  
## <a name="message-exchange-patterns"></a><span data-ttu-id="c0fd7-255">訊息交換模式</span><span class="sxs-lookup"><span data-stu-id="c0fd7-255">Message Exchange Patterns</span></span>  
 <span data-ttu-id="c0fd7-256">本節將說明當不同訊息交換模式使用 WS-ReliableMessaging 時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的行為。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-256">This section describes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]'s behavior when WS-ReliableMessaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="c0fd7-257">在每個訊息交換模式中，會考慮下列兩種部署案例：</span><span class="sxs-lookup"><span data-stu-id="c0fd7-257">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>  
  
-   <span data-ttu-id="c0fd7-258">不可定址的啟動器：啟動器位於防火牆後方，回應程式只能透過 HTTP 回應將訊息傳送至啟動器。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-258">Non-Addressable Initiator: Initiator is behind a firewall; Responder can deliver messages to the Initiator only on HTTP responses.</span></span>  
  
-   <span data-ttu-id="c0fd7-259">可定址的啟動器：可將 HTTP 要求同時傳送給啟動器與回應程式，亦即可建立兩個反向 HTTP 連線。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-259">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>  
  
### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="c0fd7-260">單向、不可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="c0fd7-260">One-way, Non-addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="c0fd7-261">繫結</span><span class="sxs-lookup"><span data-stu-id="c0fd7-261">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-262"> 透過在一個 HTTP 通道上使用一個序列的方式，提供單向的訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-262"> provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-263"> 會使用 HTTP 要求將所有訊息從啟動器傳送至回應程式，並透過 HTTP 回應將所有訊息從回應程式傳送至啟動器。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-263"> uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="c0fd7-264">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="c0fd7-264">CreateSequence Exchange</span></span>  
 <span data-ttu-id="c0fd7-265">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會透過 HTTP 要求將不包含 `CreateSequence` 項目的 `Offer` 訊息傳送出去，並預期透過 HTTP 回應接收 `CreateSequenceResponse` 訊息。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-265">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="c0fd7-266">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會建立序列，並透過 HTTP 回應將不包含 `CreateSequenceResponse` 項目的 `Accept` 訊息傳送出去。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-266">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on the HTTP response.</span></span>  
  
#### <a name="sequenceacknowledgement"></a><span data-ttu-id="c0fd7-267">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="c0fd7-267">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="c0fd7-268">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會處理所有訊息回覆的認可，除了 `CreateSequence` 訊息與錯誤訊息以外。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-268">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="c0fd7-269">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式一律透過 HTTP 回應將獨立認可傳送至所有序列和 `AckRequested` 訊息。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-269">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder always transmits a stand-alone acknowledgement on the HTTP response to all sequence and `AckRequested` messages.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="c0fd7-270">CloseSequence 交換</span><span class="sxs-lookup"><span data-stu-id="c0fd7-270">CloseSequence Exchange</span></span>  
 <span data-ttu-id="c0fd7-271">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會透過 HTTP 要求將 `CloseSequence` 訊息傳送出去，並預期透過 HTTP 回應接收 `CreateSequenceResponse` 訊息。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-271">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CloseSequence` message on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="c0fd7-272">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會透過 HTTP 回應將 `CloseSequenceResponse` 訊息傳送出去。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-272">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="c0fd7-273">TerminateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="c0fd7-273">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="c0fd7-274">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會透過 HTTP 要求將 `TerminateSequence` 訊息傳送出去，並預期透過 HTTP 回應接收 `TerminateSequenceResponse` 訊息。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-274">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `TerminateSequence` message on an HTTP request and expects the `TerminateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="c0fd7-275">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會透過 HTTP 回應將 `TerminateSequenceResponse` 訊息傳送出去。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-275">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="one-way-addressable-initiator"></a><span data-ttu-id="c0fd7-276">單向、可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="c0fd7-276">One Way, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="c0fd7-277">繫結</span><span class="sxs-lookup"><span data-stu-id="c0fd7-277">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-278"> 透過在一個傳入與一個傳出 HTTP 通道上使用一個序列的方式，提供單向的訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-278"> provides a one-way message exchange pattern using one sequence over one inbound and one outbound HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-279"> 會使用 HTTP 要求來傳送所有訊息。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-279"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="c0fd7-280">所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-280">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="c0fd7-281">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="c0fd7-281">CreateSequence Exchange</span></span>  
 <span data-ttu-id="c0fd7-282">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會透過 HTTP 要求將不包含 `CreateSequence` 項目的 `Offer` 訊息傳送出去。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-282">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request.</span></span> <span data-ttu-id="c0fd7-283">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會建立序列，並透過 HTTP 要求將不包含 `CreateSequenceResponse` 項目的 `Accept` 訊息傳送出去。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-283">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on an HTTP request.</span></span>  
  
### <a name="duplex-addressable-initiator"></a><span data-ttu-id="c0fd7-284">雙工、可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="c0fd7-284">Duplex, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="c0fd7-285">繫結</span><span class="sxs-lookup"><span data-stu-id="c0fd7-285">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-286"> 透過在一個傳入與一個傳出 HTTP 通道上使用兩個序列的方式，提供完全非同步、雙向的訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-286"> provides a fully-asynchronous, two-way message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="c0fd7-287">在有限的情況下，此訊息交換模式可與 `Request/Reply`、`Addressable` 啟動器訊息交換模式混合使用。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-287">This message exchange pattern can be mixed with the `Request/Reply`, `Addressable` Initiator message exchange pattern in a limited way.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-288"> 會使用 HTTP 要求來傳送所有訊息。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-288"> uses HTTP requests to transmit all messages.</span></span> <span data-ttu-id="c0fd7-289">所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-289">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="c0fd7-290">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="c0fd7-290">CreateSequence Exchange</span></span>  
 <span data-ttu-id="c0fd7-291">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會透過 HTTP 要求將包含 `CreateSequence` 項目的 `Offer` 訊息傳送出去。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-291">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="c0fd7-292">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會確保 `CreateSequence` 包含 `Offer` 項目，然後建立序列並將包含 `CreateSequenceResponse` 項目的 `Accept` 訊息傳送出去。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-292">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an `Offer` element, then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="sequence-lifetime"></a><span data-ttu-id="c0fd7-293">序列存留期</span><span class="sxs-lookup"><span data-stu-id="c0fd7-293">Sequence Lifetime</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-294"> 會將兩個序列視為一個全雙工工作階段。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-294"> treats the two sequences as one fully-duplex session.</span></span>  
  
 <span data-ttu-id="c0fd7-295">在產生可挑剔某個序列的錯誤時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 預期遠端端點將同時挑剔兩個序列。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-295">Upon generating a fault that faults one sequence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="c0fd7-296">在讀取可挑剔某個序列的錯誤時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 將同時挑剔兩個序列。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-296">Upon reading a fault that faults one sequence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] faults both sequences.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-297"> 可關閉本身的傳出序列並繼續處理其傳入序列中的訊息。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-297"> can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="c0fd7-298">反之，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可以處理傳入序列的關閉作業並繼續傳送其傳出序列中的訊息。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-298">Conversely, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a><span data-ttu-id="c0fd7-299">要求-回覆和單向、不可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="c0fd7-299">Request-Reply and One-Way, Non-Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="c0fd7-300">繫結</span><span class="sxs-lookup"><span data-stu-id="c0fd7-300">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-301"> 透過在一個 HTTP 通道上使用兩個序列的方式，提供單向、要求-回覆的訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-301"> provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-302"> 會使用 HTTP 要求將所有訊息從啟動器傳送至回應程式，並透過 HTTP 回應將所有訊息從回應程式傳送至啟動器。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-302"> uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="c0fd7-303">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="c0fd7-303">CreateSequence Exchange</span></span>  
 <span data-ttu-id="c0fd7-304">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會透過 HTTP 要求將包含 `CreateSequence` 項目的 `Offer` 訊息傳送出去，並預期透過 HTTP 回應接收 `CreateSequenceResponse` 訊息。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-304">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="c0fd7-305">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會建立序列，並透過 HTTP 回應將包含 `CreateSequenceResponse` 項目的 `Accept` 訊息傳送出去。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-305">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element on the HTTP response.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="c0fd7-306">單向訊息</span><span class="sxs-lookup"><span data-stu-id="c0fd7-306">One-way Message</span></span>  
 <span data-ttu-id="c0fd7-307">為了成功完成單向訊息交換，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會在 HTTP 要求上傳送要求序列訊息，並在 HTTP 回應上接收獨立的 `SequenceAcknowledgement` 訊息。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-307">To complete a one-way message exchange successfully, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="c0fd7-308">`SequenceAcknowledgement` 必須認可傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-308">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>  
  
 <span data-ttu-id="c0fd7-309">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式可透過認可、錯誤或是內含空本文與 HTTP 202 狀態碼的回應來回覆要求。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-309">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder may reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="two-way-messages"></a><span data-ttu-id="c0fd7-310">雙向訊息</span><span class="sxs-lookup"><span data-stu-id="c0fd7-310">Two Way Messages</span></span>  
 <span data-ttu-id="c0fd7-311">為了成功完成雙向訊息交換通訊協定，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會透過 HTTP 要求傳送要求序列訊息，並透過 HTTP 回應接收回覆序列訊息。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-311">To complete a two way message exchange protocol successfully, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="c0fd7-312">回應中必須包含認可傳輸之要求序列訊息的 `SequenceAcknowledgement`。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-312">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>  
  
 <span data-ttu-id="c0fd7-313">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式可透過應用程式回覆、錯誤或是內含空本文與 HTTP 202 狀態碼的回應來回覆要求。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-313">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder may reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>  
  
 <span data-ttu-id="c0fd7-314">由於單向訊息與應用程式回覆時機的緣故，要求序列訊息的序號與回應訊息的序號彼此並未互相關聯。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-314">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>  
  
#### <a name="retrying-replies"></a><span data-ttu-id="c0fd7-315">重試回覆</span><span class="sxs-lookup"><span data-stu-id="c0fd7-315">Retrying Replies</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-316"> 仰賴 HTTP 要求-回覆相互關聯來執行雙向訊息交換通訊協定的相互關聯作業。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-316"> relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="c0fd7-317">由於這個緣故，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器不會在認可要求序列訊息時停止重試要求序列訊息，而會在 HTTP 回應內含 `SequenceAcknowledgement`、應用程式回覆，或是錯誤時，才停止重試要求序列訊息。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-317">Because of this, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries a `SequenceAcknowledgement`, application reply, or fault.</span></span> <span data-ttu-id="c0fd7-318">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會在與回覆相互關聯之要求的 HTTP 回應上重試回覆。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-318">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder retries replies on the HTTP response of the request to which the reply is correlated.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="c0fd7-319">CloseSequence 交換</span><span class="sxs-lookup"><span data-stu-id="c0fd7-319">CloseSequence Exchange</span></span>  
 <span data-ttu-id="c0fd7-320">在收到所有單向要求序列訊息的所有回覆序列訊息與認可時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會透過 HTTP 要求傳送要求序列的 `CloseSequence` 訊息，並預期透過 HTTP 回應收到 `CloseSequenceResponse`。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-320">After receiving all reply sequence messages and acknowledgements for all one way request sequence messages, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CloseSequence` message for the request sequence on an HTTP request and expects the `CloseSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="c0fd7-321">隱含地關閉要求序列會一併關閉回覆序列。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-321">Closing the request sequence implicitly closes the reply sequence.</span></span> <span data-ttu-id="c0fd7-322">也就是說，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會在 `SequenceAcknowledgement` 訊息中包含回覆序列的最終 `CloseSequence`，而且回覆序列不會有 `CloseSequence` 交換。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-322">This means the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator includes the reply sequence’s Final `SequenceAcknowledgement` on the `CloseSequence` message and the reply sequence does not have a `CloseSequence` exchange.</span></span>  
  
 <span data-ttu-id="c0fd7-323">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會確保所有回覆都已認可，並透過 HTTP 回應來傳送 `CloseSequenceResponse` 訊息。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-323">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures all replies are acknowledged and transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="c0fd7-324">TerminateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="c0fd7-324">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="c0fd7-325">在收到 `CloseSequenceResponse` 訊息之後，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會透過 HTTP 要求將要求序列的 `TerminateSequence` 訊息傳送出去，並預期透過 HTTP 回應收到 `TerminateSequenceResponse`。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-325">After receiving the `CloseSequenceResponse` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `TerminateSequence` message for the request sequence on an HTTP request and expects the `TerminateSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="c0fd7-326">就像 `CloseSequence` 交換一樣，終止要求序列會隱含地終止回覆序列。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-326">Like the `CloseSequence` exchange, terminating the request sequence implicitly terminates the reply sequence.</span></span> <span data-ttu-id="c0fd7-327">也就是說，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會在 `SequenceAcknowledgement` 訊息中包含回覆序列的最終 `TerminateSequence`，而且回覆序列不會有 `TerminateSequence` 交換。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-327">This means the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator includes the reply sequence’s final `SequenceAcknowledgement` on the `TerminateSequence` message and the reply sequence does not have a `TerminateSequence` exchange.</span></span>  
  
 <span data-ttu-id="c0fd7-328">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會透過 HTTP 回應將 `TerminateSequenceResponse` 訊息傳送出去。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-328">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="c0fd7-329">要求/回覆、可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="c0fd7-329">Request/Reply, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="c0fd7-330">繫結</span><span class="sxs-lookup"><span data-stu-id="c0fd7-330">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-331"> 透過在一個傳入與一個傳出 HTTP 通道上使用兩個序列的方式，提供要求-回覆訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-331"> provides a request-reply message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="c0fd7-332">在有限的情況下，此訊息交換模式可與 `Duplex, Addressable` 啟動器訊息交換模式混合使用。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-332">This message exchange pattern can be mixed with the `Duplex, Addressable` Initiator message exchange pattern in a limited way.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-333"> 會使用 HTTP 要求來傳送所有訊息。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-333"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="c0fd7-334">所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-334">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="c0fd7-335">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="c0fd7-335">CreateSequence Exchange</span></span>  
 <span data-ttu-id="c0fd7-336">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會透過 HTTP 要求將包含 `CreateSequence` 項目的 `Offer` 訊息傳送出去。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-336">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="c0fd7-337">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會確保 `CreateSequence` 包含 `Offer` 項目，然後建立序列並將包含 `CreateSequenceResponse` 項目的 `Accept` 訊息傳送出去。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-337">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an `Offer` element then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="requestreply-correlation"></a><span data-ttu-id="c0fd7-338">要求/回覆相互關聯</span><span class="sxs-lookup"><span data-stu-id="c0fd7-338">Request/Reply Correlation</span></span>  
 <span data-ttu-id="c0fd7-339">下列會套用到所有相互關聯的要求及回覆：</span><span class="sxs-lookup"><span data-stu-id="c0fd7-339">The following applies to all correlated requests and replies:</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-340"> 可確保所有應用程式要求訊息都帶有 `ReplyTo` 端點參照和 `MessageId`。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-340"> ensures all application request messages bear a `ReplyTo` endpoint reference and a `MessageId`.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-341"> 會將本機端點參照當成每個應用程式要求訊息的 `ReplyTo` 來套用。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-341"> applies the local endpoint reference as each application request message’s `ReplyTo`.</span></span> <span data-ttu-id="c0fd7-342">啟動器的本機端點參照是 `CreateSequence` 訊息的 `ReplyTo`，而回應程式的本機端點參照則是 `CreateSequence` 訊息的 `To`。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-342">The local endpoint reference is the `CreateSequence` message’s `ReplyTo` for the Initiator and the `CreateSequence` message’s `To` for the Responder.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-343"> 可確保所有傳入的要求訊息都帶有 `MessageId` 和 `ReplyTo`。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-343"> ensures that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-344"> 可確保所有應用程式要求訊息的 `ReplyTo` 端點參照 URI 都符合如先前定義的本機端點參照。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-344"> ensures the `ReplyTo` endpoint reference’s URI of all application request messages match the local endpoint reference as defined earlier.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c0fd7-345"> 可確保所有回覆都帶有正確且遵循 `RelatesTo` 要求/回覆相互關聯規則的 `To` 和 `wsa` 標頭。</span><span class="sxs-lookup"><span data-stu-id="c0fd7-345"> ensures that all replies bear the correct `RelatesTo` and `To` headers following `wsa` request/reply correlation rules.</span></span>

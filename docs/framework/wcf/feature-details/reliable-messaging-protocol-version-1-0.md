---
title: Reliable Messaging Protocol 1.0 版
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: 6fceb49d107e4268a4b9fad6197335ff9e2af9ab
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662800"
---
# <a name="reliable-messaging-protocol-version-10"></a><span data-ttu-id="9c96f-102">Reliable Messaging Protocol 1.0 版</span><span class="sxs-lookup"><span data-stu-id="9c96f-102">Reliable Messaging Protocol version 1.0</span></span>

<span data-ttu-id="9c96f-103">本主題涵蓋 Windows Communication Foundation (WCF) 實作細節 Ws-reliable messaging February 2005 （1.0 版） 通訊協定所需的互通性，使用 HTTP 傳輸。</span><span class="sxs-lookup"><span data-stu-id="9c96f-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-Reliable Messaging February 2005 (version 1.0) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="9c96f-104">WCF 會遵循本主題所說明的相關限制與說明 Ws-reliable 訊息規格。</span><span class="sxs-lookup"><span data-stu-id="9c96f-104">WCF follows the WS-Reliable Messaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="9c96f-105">請注意 WinFX 從開始實作 WS-ReliableMessaging 1.0 版通訊協定。</span><span class="sxs-lookup"><span data-stu-id="9c96f-105">Note that the WS-ReliableMessaging version 1.0 protocol is implemented starting with the WinFX.</span></span>

<span data-ttu-id="9c96f-106">Ws-reliable Messaging February 2005 通訊協定的實作中的 WCF <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="9c96f-106">The WS-Reliable Messaging February 2005 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>

<span data-ttu-id="9c96f-107">為了方便起見，本主題將使用下列角色：</span><span class="sxs-lookup"><span data-stu-id="9c96f-107">For convenience, the topic uses the following roles:</span></span>

- <span data-ttu-id="9c96f-108">啟動器：啟動 WS-Reliable 訊息序列建立作業的用戶端</span><span class="sxs-lookup"><span data-stu-id="9c96f-108">Initiator: the client that initiates WS-Reliable Message sequence creation</span></span>

- <span data-ttu-id="9c96f-109">回應程式：接收啟動器要求的服務</span><span class="sxs-lookup"><span data-stu-id="9c96f-109">Responder: the service that receives the initiator's requests</span></span>

<span data-ttu-id="9c96f-110">本文件會使用下表的前置詞和命名空間。</span><span class="sxs-lookup"><span data-stu-id="9c96f-110">This document uses the prefixes and namespaces in the following table.</span></span>

|<span data-ttu-id="9c96f-111">前置詞</span><span class="sxs-lookup"><span data-stu-id="9c96f-111">Prefix</span></span>|<span data-ttu-id="9c96f-112">命名空間</span><span class="sxs-lookup"><span data-stu-id="9c96f-112">Namespace</span></span>|
|------------|---------------|
|<span data-ttu-id="9c96f-113">wsrm</span><span class="sxs-lookup"><span data-stu-id="9c96f-113">wsrm</span></span>|http://schemas.xmlsoap.org/ws/2005/02/rm|
|<span data-ttu-id="9c96f-114">netrm</span><span class="sxs-lookup"><span data-stu-id="9c96f-114">netrm</span></span>|http://schemas.microsoft.com/ws/2006/05/rm|
|<span data-ttu-id="9c96f-115">秒</span><span class="sxs-lookup"><span data-stu-id="9c96f-115">s</span></span>|http://www.w3.org/2003/05/soap-envelope|
|<span data-ttu-id="9c96f-116">wsa</span><span class="sxs-lookup"><span data-stu-id="9c96f-116">wsa</span></span>|http://schemas.xmlsoap.org/ws/2005/08/addressing|
|<span data-ttu-id="9c96f-117">wsse</span><span class="sxs-lookup"><span data-stu-id="9c96f-117">wsse</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|

## <a name="messaging"></a><span data-ttu-id="9c96f-118">訊息</span><span class="sxs-lookup"><span data-stu-id="9c96f-118">Messaging</span></span>

### <a name="sequence-establishment-messages"></a><span data-ttu-id="9c96f-119">序列建立訊息</span><span class="sxs-lookup"><span data-stu-id="9c96f-119">Sequence Establishment Messages</span></span>

<span data-ttu-id="9c96f-120">WCF 實作`CreateSequence`和`CreateSequenceResponse`訊息以建立可靠的訊息序列。</span><span class="sxs-lookup"><span data-stu-id="9c96f-120">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable message sequence.</span></span> <span data-ttu-id="9c96f-121">以下是適用的條件約束：</span><span class="sxs-lookup"><span data-stu-id="9c96f-121">The following constraints apply:</span></span>

- <span data-ttu-id="9c96f-122">B1101:WCF 啟動器不會產生選用的 Expires 項目，在`CreateSequence`訊息或情況時`CreateSequence`訊息包含`Offer`項目、 選擇性`Expires`中的項目`Offer`項目。</span><span class="sxs-lookup"><span data-stu-id="9c96f-122">B1101: The WCF Initiator does not generate the optional Expires element in the `CreateSequence` message or, in the cases when the `CreateSequence` message contains an `Offer` element, the optional `Expires` element in the `Offer` element.</span></span>

- <span data-ttu-id="9c96f-123">B1102:存取時`CreateSequence`訊息，WCF`Responder`傳送和接收兩者`Expires`如果它們存在，但不會使用其值的項目。</span><span class="sxs-lookup"><span data-stu-id="9c96f-123">B1102: When accessing the `CreateSequence` message, the WCF`Responder` sends and receives both `Expires` elements if they exist, but does not use their values.</span></span>

<span data-ttu-id="9c96f-124">WS-Reliable 訊息會使用 `Offer` 機制來建立兩個反向關聯序列以形成工作階段。</span><span class="sxs-lookup"><span data-stu-id="9c96f-124">WS-Reliable Messaging introduces the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>

- <span data-ttu-id="9c96f-125">R1103:如果`CreateSequence`包含`Offer`項目，可靠的傳訊回應程式必須接收序列並以回應`CreateSequenceResponse`包含`wsrm:Accept`項目，形成兩個相互關聯的反向序列，或拒絕`CreateSequence`要求。</span><span class="sxs-lookup"><span data-stu-id="9c96f-125">R1103: If `CreateSequence` contains an `Offer` element, the Reliable Messaging Responder must either accept the sequence and respond with `CreateSequenceResponse` that contains a `wsrm:Accept` element, forming two correlated converse sequences or reject the `CreateSequence` request.</span></span>

- <span data-ttu-id="9c96f-126">R1104：流經反向序列的 `SequenceAcknowledgement` 和應用程式訊息必須傳送到 `ReplyTo` 的 `CreateSequence` 端點參考。</span><span class="sxs-lookup"><span data-stu-id="9c96f-126">R1104: `SequenceAcknowledgement` and application messages flowing on converse sequence must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>

- <span data-ttu-id="9c96f-127">R1105：`AcksTo` 中的 `ReplyTo` 和 `CreateSequence` 端點參考必須具有位址值以符合八位元規格。</span><span class="sxs-lookup"><span data-stu-id="9c96f-127">R1105: `AcksTo` and `ReplyTo` endpoint references in the `CreateSequence` must have address values that match the octet-wise.</span></span>

  <span data-ttu-id="9c96f-128">WCF 回應程式會驗證的 URI 部分`AcksTo`和`ReplyTo`Epr 建立序列之前完全相同。</span><span class="sxs-lookup"><span data-stu-id="9c96f-128">The WCF Responder verifies that the URI portion of the `AcksTo` and `ReplyTo` EPRs are identical before creating a sequence.</span></span>

- <span data-ttu-id="9c96f-129">R1106：`AcksTo` 訊息中的 `ReplyTo` 和 `CreateSequence` 端點參照應該具有相同的參照參數集合。</span><span class="sxs-lookup"><span data-stu-id="9c96f-129">R1106: `AcksTo` and `ReplyTo` Endpoint References in the `CreateSequence` should have the same set of reference parameters.</span></span>

  <span data-ttu-id="9c96f-130">WCF 不會強制執行，但假設的之 [reference parameters]`AcksTo`並`ReplyTo`上`CreateSequence`相同，並使用 [參考 parameters] 從`ReplyTo`認可並與序列訊息的端點參考。</span><span class="sxs-lookup"><span data-stu-id="9c96f-130">WCF does not enforce but assumes that [reference parameters] of `AcksTo` and `ReplyTo` on `CreateSequence` are identical and uses [reference parameters] from `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>

- <span data-ttu-id="9c96f-131">R1107:建立兩個反向序列的使用時`Offer`機制`SequenceAcknowledgement`流經反向序列的應用程式訊息必須傳送至`ReplyTo`端點參考`CreateSequence`。</span><span class="sxs-lookup"><span data-stu-id="9c96f-131">R1107: When two converse sequences are established using the `Offer` mechanism, `SequenceAcknowledgement` and application messages flowing on converse sequences must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>

- <span data-ttu-id="9c96f-132">R1108:當兩個反向序列都透過 Offer 機制，來建立`[address]`的屬性`wsrm:AcksTo`端點參考子項目`wsrm:Accept`項目`CreateSequenceResponse`必須符合的位元組規格目的地URI`CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="9c96f-132">R1108: When two converse sequences are established using the Offer mechanism, the `[address]` property of the `wsrm:AcksTo` Endpoint Reference child element of the `wsrm:Accept` element of the `CreateSequenceResponse` must match byte-wise the destination URI of the `CreateSequence`.</span></span>

- <span data-ttu-id="9c96f-133">R1109:建立兩個反向序列的使用時`Offer`機制、 起始端和回應訊息的通知所傳送的訊息必須傳送至相同的端點參考。</span><span class="sxs-lookup"><span data-stu-id="9c96f-133">R1109: When two converse sequences are established using the `Offer` mechanism, messages sent by initiator and acknowledgements to messages by responder must be sent to the same Endpoint Reference.</span></span>

  <span data-ttu-id="9c96f-134">WCF 會使用 Ws-reliable 訊息建立啟動器和回應程式之間的可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="9c96f-134">WCF uses WS-Reliable Messaging to establish reliable sessions between the Initiator and Responder.</span></span> <span data-ttu-id="9c96f-135">WCF 的 Ws-reliable 訊息實作會提供可靠的工作階段的單向、 要求-回覆與全雙工訊息模式。</span><span class="sxs-lookup"><span data-stu-id="9c96f-135">WCF's WS-Reliable Messaging implementation provides reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="9c96f-136">Ws-reliable 訊息`Offer`上的機制`CreateSequence` / `CreateSequenceResponse`可讓您建立兩個相互關聯的反向序列，並提供工作階段通訊協定，可適用於所有訊息端點。</span><span class="sxs-lookup"><span data-stu-id="9c96f-136">The WS-Reliable Messaging `Offer` mechanism on `CreateSequence`/`CreateSequenceResponse` lets you establish two correlated converse sequences, and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="9c96f-137">WCF 會提供包含的工作階段完整性的端對端保護這類的工作階段的安全性保證，因此它會實際地確保相同的合作對象的訊息會抵達相同的目的地。</span><span class="sxs-lookup"><span data-stu-id="9c96f-137">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure messages intended to the same party are arriving at the same destination.</span></span> <span data-ttu-id="9c96f-138">這麼做也可以針對應用程式訊息進行 Piggy-Backing 的序列認可作業。</span><span class="sxs-lookup"><span data-stu-id="9c96f-138">This also allows piggy-backing of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="9c96f-139">因此，R1104、 R1105 和 R1108 的條件約束套用至 WCF。</span><span class="sxs-lookup"><span data-stu-id="9c96f-139">Therefore, constraints R1104, R1105, and R1108 apply to WCF.</span></span>

<span data-ttu-id="9c96f-140">`CreateSequence` 訊息的範例。</span><span class="sxs-lookup"><span data-stu-id="9c96f-140">An example of a `CreateSequence` message.</span></span>

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

 <span data-ttu-id="9c96f-141">`CreateSequenceResponse` 訊息的範例。</span><span class="sxs-lookup"><span data-stu-id="9c96f-141">An example of a `CreateSequenceResponse` message.</span></span>

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

### <a name="sequence"></a><span data-ttu-id="9c96f-142">序列</span><span class="sxs-lookup"><span data-stu-id="9c96f-142">Sequence</span></span>

<span data-ttu-id="9c96f-143">下列清單列出適用於序列的條件約束：</span><span class="sxs-lookup"><span data-stu-id="9c96f-143">The following is a list of constraints that apply to sequences:</span></span>

- <span data-ttu-id="9c96f-144">B1201:WCF 會產生，並存取序號不高於`xs:long`的最大包含值，9223372036854775807。</span><span class="sxs-lookup"><span data-stu-id="9c96f-144">B1201:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>

- <span data-ttu-id="9c96f-145">B1202:WCF 一律會產生主體空白的最後一個訊息，並將動作 URI 的`http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`。</span><span class="sxs-lookup"><span data-stu-id="9c96f-145">B1202:WCF always generates an empty-bodied last message with the action URI of `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>

- <span data-ttu-id="9c96f-146">B1203:WCF 接收與傳遞的訊息序列標頭，其中包含`LastMessage`項目只要動作 URI 不是`http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`。</span><span class="sxs-lookup"><span data-stu-id="9c96f-146">B1203: WCF receives and delivers a message with a Sequence header that contains a `LastMessage` element as long as the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>

<span data-ttu-id="9c96f-147">序列標頭的範例。</span><span class="sxs-lookup"><span data-stu-id="9c96f-147">An example of a Sequence Header.</span></span>

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

### <a name="ackrequested-header"></a><span data-ttu-id="9c96f-148">AckRequested 標頭</span><span class="sxs-lookup"><span data-stu-id="9c96f-148">AckRequested Header</span></span>

<span data-ttu-id="9c96f-149">WCF 會使用`AckRequested`標頭做為 keep-alive 機制。</span><span class="sxs-lookup"><span data-stu-id="9c96f-149">WCF uses `AckRequested` Header as a keep-alive mechanism.</span></span> <span data-ttu-id="9c96f-150">WCF 不會產生選擇性`MessageNumber`項目。</span><span class="sxs-lookup"><span data-stu-id="9c96f-150">WCF does not generate the optional `MessageNumber` element.</span></span> <span data-ttu-id="9c96f-151">收到的訊息`AckRequested`包含的標頭`MessageNumber`元素，WCF 會忽略`MessageNumber`元素的值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="9c96f-151">Upon receiving a message with an `AckRequested` header that contains the `MessageNumber` element, WCF ignores the `MessageNumber` element’s value, as shown in the following example.</span></span>

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement-header"></a><span data-ttu-id="9c96f-152">SequenceAcknowledgement 標頭</span><span class="sxs-lookup"><span data-stu-id="9c96f-152">SequenceAcknowledgement Header</span></span>

<span data-ttu-id="9c96f-153">WCF 所提供的 Ws-reliable 訊息的序列認可使用 piggy-back 機制。</span><span class="sxs-lookup"><span data-stu-id="9c96f-153">WCF uses piggy-back mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span>

- <span data-ttu-id="9c96f-154">R1401:當使用建立兩個反向序列`Offer`機制，`SequenceAcknowledgement`標頭可能包含在傳送到預定的收件者的任何應用程式訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-154">R1401: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span>

- <span data-ttu-id="9c96f-155">B1402:當 WCF 必須先產生認可之前收到任何序列訊息 (例如，若要滿足`AckRequested`訊息)，WCF 會產生`SequenceAcknowledgement`包含範圍 0-0，如下列範例所示的標頭。</span><span class="sxs-lookup"><span data-stu-id="9c96f-155">B1402: When WCF must generate an acknowledgement prior to receiving any sequence messages (for example, to satisfy an `AckRequested` message), WCF generates a `SequenceAcknowledgement` header that contains the range 0-0, as shown in the following example.</span></span>

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="0" Lower="0"/>
  </wsrm:SequenceAcknowledgement>
  ```

- <span data-ttu-id="9c96f-156">B1403:WCF 不會產生`SequenceAcknowledgement`包含的標頭`Nack`項目，但支援`Nack`項目。</span><span class="sxs-lookup"><span data-stu-id="9c96f-156">B1403: WCF does not generate `SequenceAcknowledgement` headers that contain a `Nack` element but supports `Nack` elements.</span></span>

### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="9c96f-157">WS-ReliableMessaging 錯誤</span><span class="sxs-lookup"><span data-stu-id="9c96f-157">WS-ReliableMessaging Faults</span></span>

<span data-ttu-id="9c96f-158">以下是適用於 Ws-reliable 訊息錯誤 WCF 實作的條件約束的清單：</span><span class="sxs-lookup"><span data-stu-id="9c96f-158">The following is a list of constraints that apply to the WCF implementation of WS-Reliable Messaging faults:</span></span>

- <span data-ttu-id="9c96f-159">B1501:WCF 不會產生`MessageNumberRollover`錯誤。</span><span class="sxs-lookup"><span data-stu-id="9c96f-159">B1501: WCF does not generate `MessageNumberRollover` faults.</span></span>

- <span data-ttu-id="9c96f-160">B1502:WCF 端點可能會產生`CreateSequenceRefused`錯誤，如規格所述。</span><span class="sxs-lookup"><span data-stu-id="9c96f-160">B1502:WCF endpoint may generate `CreateSequenceRefused` faults as described in the specification.</span></span>

- <span data-ttu-id="9c96f-161">B1503:When 服務端點到達其連線限制，而且無法處理新的連線時，WCF 會產生額外`CreateSequenceRefused`錯誤子代碼， `netrm:ConnectionLimitReached`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="9c96f-161">B1503:When the service endpoint reaches its connection limit and cannot process new connections, WCF generates an additional `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>

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

### <a name="ws-addressing-faults"></a><span data-ttu-id="9c96f-162">WS-Addressing 錯誤</span><span class="sxs-lookup"><span data-stu-id="9c96f-162">WS-Addressing Faults</span></span>

<span data-ttu-id="9c96f-163">由於 Ws-reliable 訊息會使用 Ws-addressing，WCF Ws-reliable 訊息實作可能會產生 Ws-addressing 錯誤。</span><span class="sxs-lookup"><span data-stu-id="9c96f-163">Because WS-Reliable Messaging uses WS-Addressing, WCF WS-Reliable Messaging implementation may generate WS-Addressing faults.</span></span> <span data-ttu-id="9c96f-164">本節涵蓋了 Ws-reliable 訊息層明確產生 WCF Ws-addressing 錯誤：</span><span class="sxs-lookup"><span data-stu-id="9c96f-164">This section covers the WS-Addressing faults that WCF explicitly generates at the WS-Reliable Messaging layer:</span></span>

- <span data-ttu-id="9c96f-165">當下列其中一項條件成立時，B1601:WCF 就會產生錯誤訊息定址標頭需要：</span><span class="sxs-lookup"><span data-stu-id="9c96f-165">B1601:WCF generates the fault Message Addressing Header Required when one of the following is true:</span></span>

  - <span data-ttu-id="9c96f-166">訊息缺少 `Sequence` 標頭和 `Action` 標頭。</span><span class="sxs-lookup"><span data-stu-id="9c96f-166">A message is missing a `Sequence` header and an `Action` header.</span></span>

  - <span data-ttu-id="9c96f-167">`CreateSequence` 訊息缺少 `MessageId` 標頭。</span><span class="sxs-lookup"><span data-stu-id="9c96f-167">A `CreateSequence` message is missing a `MessageId` header.</span></span>

  - <span data-ttu-id="9c96f-168">`CreateSequence` 訊息缺少 `ReplyTo` 標頭。</span><span class="sxs-lookup"><span data-stu-id="9c96f-168">A `CreateSequence` message is missing a `ReplyTo` header.</span></span>

- <span data-ttu-id="9c96f-169">B1602:WCF 產生時遺失訊息不支援動作的錯誤`Sequence`標頭，且`Action`不是可辨識的 Ws-reliable 訊息規格中的標頭。</span><span class="sxs-lookup"><span data-stu-id="9c96f-169">B1602:WCF generates the fault Action Not Supported in reply to a message that is missing a `Sequence` header and has an `Action` header that is not a recognized in the WS-Reliable Messaging specification.</span></span>

- <span data-ttu-id="9c96f-170">B1603:WCF 產生端點無法使用，表示端點不會處理順序根據檢查錯誤`CreateSequence`訊息之定址標頭。</span><span class="sxs-lookup"><span data-stu-id="9c96f-170">B1603:WCF generates the fault Endpoint Unavailable to indicate that the endpoint does not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>

## <a name="protocol-composition"></a><span data-ttu-id="9c96f-171">通訊協定組合</span><span class="sxs-lookup"><span data-stu-id="9c96f-171">Protocol Composition</span></span>

### <a name="composition-with-ws-addressing"></a><span data-ttu-id="9c96f-172">與 WS-Addressing 組合</span><span class="sxs-lookup"><span data-stu-id="9c96f-172">Composition with WS-Addressing</span></span>

<span data-ttu-id="9c96f-173">WCF 支援兩個 Ws-addressing 版本：Ws-addressing 2004/08 [WS-ADDR] 和 W3C Ws-addressing 1.0 建議 [WS-ADDR-核心] 和 [WS-ADDR-SOAP]。</span><span class="sxs-lookup"><span data-stu-id="9c96f-173">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>

<span data-ttu-id="9c96f-174">儘管 WS-Reliable 訊息規格只提到 WS-Addressing 2004/08，它並未限制要使用的 WS-Addressing 版本。</span><span class="sxs-lookup"><span data-stu-id="9c96f-174">While the WS-Reliable Messaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="9c96f-175">以下是適用於 WCF 的條件約束的清單：</span><span class="sxs-lookup"><span data-stu-id="9c96f-175">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="9c96f-176">R2101： 這兩個 Ws-addressing 2004/08 和 Ws-addressing 1.0 可搭配 Ws-reliable 訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-176">R2101:Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>

- <span data-ttu-id="9c96f-177">在整個特定的 Ws-reliable 訊息序列或是一對使用相互關聯的反向序列，就必須使用 ws-addressing 的 R2102:A 單一版本`wsrm:Offer`機制。</span><span class="sxs-lookup"><span data-stu-id="9c96f-177">R2102:A single version of WS-Addressing must be used throughout a given WS-Reliable Messaging sequence or a pair of converse sequences correlated by using the `wsrm:Offer` mechanism.</span></span>

### <a name="composition-with-soap"></a><span data-ttu-id="9c96f-178">與 SOAP 組合</span><span class="sxs-lookup"><span data-stu-id="9c96f-178">Composition with SOAP</span></span>

<span data-ttu-id="9c96f-179">WCF 支援 SOAP 1.1 和 SOAP 1.2 搭配 Ws-reliable 訊息一起使用。</span><span class="sxs-lookup"><span data-stu-id="9c96f-179">WCF supports use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>

### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="9c96f-180">與 WS-Security 和 WS-SecureConversation 組合</span><span class="sxs-lookup"><span data-stu-id="9c96f-180">Composition with WS-Security and WS-SecureConversation</span></span>

<span data-ttu-id="9c96f-181">WCF 會提供保護 Ws-reliable 訊息序列 (sequence)，透過安全傳輸 (HTTPS)、 與 Ws-security 組合且組合與 Ws-secure Conversation。</span><span class="sxs-lookup"><span data-stu-id="9c96f-181">WCF provides protection for WS-Reliable Messaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="9c96f-182">以下是適用於 WCF 的條件約束的清單：</span><span class="sxs-lookup"><span data-stu-id="9c96f-182">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="9c96f-183">R2301： 若要保護的個別訊息完整性除了 Ws-reliable 訊息序列的完整性與機密性，WCF 要求，必須使用 Ws-secure Conversation。</span><span class="sxs-lookup"><span data-stu-id="9c96f-183">R2301:To protect the integrity of a WS-Reliable Messaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>

- <span data-ttu-id="9c96f-184">R2302:AWS-在建立 Ws-reliable 訊息序列之前，必須建立安全對話工作階段。</span><span class="sxs-lookup"><span data-stu-id="9c96f-184">R2302:AWS-Secure Conversation session must be established prior to establishing WS-Reliable Messaging sequence(s).</span></span>

- <span data-ttu-id="9c96f-185">R2303:如果 Ws-reliable 訊息序列存留期超過 Ws-secure Conversation 工作階段的存留期，`SecurityContextToken`藉由使用 Ws-secure Conversation 必須更新使用對應的 Ws-secure Conversation 更新繫結。</span><span class="sxs-lookup"><span data-stu-id="9c96f-185">R2303: If the WS-Reliable Messaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>

- <span data-ttu-id="9c96f-186">B2304:WS-可靠的訊息序列或是一對相互關聯的反向序列一律繫結至單一 Ws-secureconversation 工作階段。</span><span class="sxs-lookup"><span data-stu-id="9c96f-186">B2304:WS-Reliable Messaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>

  <span data-ttu-id="9c96f-187">WCF 來源會產生`wsse:SecurityTokenReference`的項目擴充性區段中的項目`CreateSequence`訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-187">The WCF source generates the `wsse:SecurityTokenReference` element in the element extensibility section of the `CreateSequence` message.</span></span>

- <span data-ttu-id="9c96f-188">與 Ws-secure Conversation，R2305:When`CreateSequence`訊息必須包含`wsse:SecurityTokenReference`項目。</span><span class="sxs-lookup"><span data-stu-id="9c96f-188">R2305:When composed with WS-Secure Conversation, a `CreateSequence` message must contain the `wsse:SecurityTokenReference` element.</span></span>

## <a name="ws-reliable-messaging-ws-policy-assertion"></a><span data-ttu-id="9c96f-189">WS-Reliable 訊息 WS-Policy 判斷提示</span><span class="sxs-lookup"><span data-stu-id="9c96f-189">WS-Reliable Messaging WS-Policy Assertion</span></span>

<span data-ttu-id="9c96f-190">WCF 會使用 Ws-reliable 訊息 Ws-policy 判斷提示`wsrm:RMAssertion`來描述端點的功能。</span><span class="sxs-lookup"><span data-stu-id="9c96f-190">WCF uses WS-Reliable Messaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="9c96f-191">以下是適用於 WCF 的條件約束的清單：</span><span class="sxs-lookup"><span data-stu-id="9c96f-191">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="9c96f-192">B3001:WCF 會附加`wsrm:RMAssertion`Ws-policy 判斷提示至`wsdl:binding`項目。</span><span class="sxs-lookup"><span data-stu-id="9c96f-192">B3001: WCF attaches `wsrm:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="9c96f-193">WCF 支援這兩個附件`wsdl:binding`和`wsdl:port`項目。</span><span class="sxs-lookup"><span data-stu-id="9c96f-193">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>

- <span data-ttu-id="9c96f-194">B3002:WCF 支援下列選用的 Ws-reliable 訊息判斷提示屬性，並針對它們提供控制的 WCF`ReliableMessagingBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="9c96f-194">B3002: WCF supports the following optional properties of WS-Reliable Messaging assertion and provides control over them on the WCF`ReliableMessagingBindingElement`:</span></span>

  - `wsrm:InactivityTimeout`

  - `wsrm:AcknowledgementInterval`

  <span data-ttu-id="9c96f-195">下列為範例。</span><span class="sxs-lookup"><span data-stu-id="9c96f-195">The following is an example.</span></span>

  ```xml
  <wsrm:RMAssertion>
    <wsrm:InactivityTimeout Milliseconds="600000" />
    <wsrm:AcknowledgementInterval Milliseconds="200" />
  </wsrm:RMAssertion>
  ```

## <a name="flow-control-ws-reliable-messaging-extension"></a><span data-ttu-id="9c96f-196">WS-Reliable 訊息延伸的流量控制</span><span class="sxs-lookup"><span data-stu-id="9c96f-196">Flow Control WS-Reliable Messaging Extension</span></span>

<span data-ttu-id="9c96f-197">WCF 會使用 Ws-reliable 訊息擴充性，提供選擇性的額外更緊密地控制序列訊息流量。</span><span class="sxs-lookup"><span data-stu-id="9c96f-197">WCF uses WS-Reliable Messaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>

<span data-ttu-id="9c96f-198">藉由設定已啟用流量控制<xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="9c96f-198">Flow control is enabled by setting the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="9c96f-199">以下是適用於 WCF 的條件約束的清單：</span><span class="sxs-lookup"><span data-stu-id="9c96f-199">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="9c96f-200">B4001:WCF 啟用信賴傳訊流量控制時，會產生`netrm:BufferRemaining`中的項目擴充性項目`SequenceAcknowledgement`標頭。</span><span class="sxs-lookup"><span data-stu-id="9c96f-200">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="9c96f-201">B4002:啟用信賴傳訊流量控制時，WCF 不需要`netrm:BufferRemaining`項目會出現在`SequenceAcknowledgement`標頭，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="9c96f-201">B4002: When Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element to be present in `SequenceAcknowledgement` header, as shown in the following example.</span></span>

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

- <span data-ttu-id="9c96f-202">B4003:WCF 會使用`netrm:BufferRemaining`指出多少新訊息的可靠的傳訊目的地可以緩衝。</span><span class="sxs-lookup"><span data-stu-id="9c96f-202">B4003: WCF uses `netrm:BufferRemaining` to indicate how many new messages the Reliable Messaging Destination can buffer.</span></span>

- <span data-ttu-id="9c96f-203">B4004: WCF 可靠傳訊服務節流處理的可信賴傳訊目的地應用程式無法快速接收訊息時，傳輸的訊息數目。</span><span class="sxs-lookup"><span data-stu-id="9c96f-203">B4004:The WCF Reliable Messaging Service throttles the number of messages transmitted when the Reliable Messaging destination application cannot receive messages quickly.</span></span> <span data-ttu-id="9c96f-204">可信賴傳訊目的地會緩衝處理訊息，並讓項目值降為 0。</span><span class="sxs-lookup"><span data-stu-id="9c96f-204">The Reliable Messaging destination buffers messages and the element’s value drops to 0.</span></span>

- <span data-ttu-id="9c96f-205">B4005:WCF 會產生`netrm:BufferRemaining`整數值介於 0 到 4096 （含)，並讀取介於 0 的整數值與`xs:int`的`maxInclusive`值 214748364 （含)。</span><span class="sxs-lookup"><span data-stu-id="9c96f-205">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>

## <a name="message-exchange-patterns"></a><span data-ttu-id="9c96f-206">訊息交換模式</span><span class="sxs-lookup"><span data-stu-id="9c96f-206">Message Exchange Patterns</span></span>

<span data-ttu-id="9c96f-207">不同的訊息交換模式使用 Ws-reliable 訊息時，本節會說明 WCF 的行為。</span><span class="sxs-lookup"><span data-stu-id="9c96f-207">This section describes WCF's behavior when WS-Reliable Messaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="9c96f-208">在每個訊息交換模式中，會考慮下列兩種部署案例：</span><span class="sxs-lookup"><span data-stu-id="9c96f-208">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>

- <span data-ttu-id="9c96f-209">不可定址的啟動器：啟動器位於防火牆;回應程式將訊息傳送至啟動器只在 HTTP 回應。</span><span class="sxs-lookup"><span data-stu-id="9c96f-209">Non-Addressable Initiator: Initiator is behind firewall; Responder can deliver messages to Initiator only on HTTP responses.</span></span>

- <span data-ttu-id="9c96f-210">可定址的啟動器：啟動器和回應程式可傳送 HTTP 要求;換句話說，您可以建立兩個反向 HTTP 連線。</span><span class="sxs-lookup"><span data-stu-id="9c96f-210">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>

### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="9c96f-211">單向、不可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="9c96f-211">One-way, Non-addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="9c96f-212">繫結</span><span class="sxs-lookup"><span data-stu-id="9c96f-212">Binding</span></span>

<span data-ttu-id="9c96f-213">WCF 會提供一個 HTTP 通道上使用一個序列的單向訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="9c96f-213">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="9c96f-214">WCF 會使用 HTTP 要求來傳送所有訊息從 RMS 至 RMD，並在 HTTP 回應來都傳送所有訊息從 rmd 傳送至 RMS。</span><span class="sxs-lookup"><span data-stu-id="9c96f-214">WCF uses the HTTP requests to transmit all messages from the RMS to the RMD and the HTTP response to transmit all messages from the RMD to the RMS.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="9c96f-215">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="9c96f-215">CreateSequence Exchange</span></span>

<span data-ttu-id="9c96f-216">WCF 啟動器會產生`CreateSequence`不含提議的訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-216">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="9c96f-217">WCF 回應程式會確保`CreateSequence`建立序列之前不含提議。</span><span class="sxs-lookup"><span data-stu-id="9c96f-217">The WCF Responder ensures the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="9c96f-218">WCF 回應回覆`CreateSequence`要求與`CreateSequenceResponse`訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-218">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>

#### <a name="sequenceacknowledgement"></a><span data-ttu-id="9c96f-219">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="9c96f-219">SequenceAcknowledgement</span></span>

<span data-ttu-id="9c96f-220">WCF 啟動器處理以外的所有訊息的認可回覆`CreateSequence`訊息與錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-220">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="9c96f-221">WCF 回應程式一律產生獨立認可，以回應這兩個序列和`AckRequested`訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-221">The WCF Responder always generates a stand-alone acknowledgement in the response to both sequence and `AckRequested` messages.</span></span>

#### <a name="terminatesequence-message"></a><span data-ttu-id="9c96f-222">TerminateSequence 訊息</span><span class="sxs-lookup"><span data-stu-id="9c96f-222">TerminateSequence message</span></span>

<span data-ttu-id="9c96f-223">WCF 會將`TerminateSequence`視為單向作業，代表 HTTP 回應具有空白主體與 HTTP 202 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="9c96f-223">WCF treats `TerminateSequence` as a one-way operation, meaning the HTTP response has an empty body and HTTP 202 status code.</span></span>

### <a name="one-way-addressable-initiator"></a><span data-ttu-id="9c96f-224">單向、可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="9c96f-224">One Way, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="9c96f-225">繫結</span><span class="sxs-lookup"><span data-stu-id="9c96f-225">Binding</span></span>

<span data-ttu-id="9c96f-226">WCF 會提供使用一個序列，透過在一個傳入與一個傳出 Http 通道的單向訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="9c96f-226">WCF provides a one-way message exchange pattern using one sequence over an inbound and an outbound Http channel.</span></span> <span data-ttu-id="9c96f-227">WCF 會使用 HTTP 要求來傳送所有訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-227">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="9c96f-228">所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="9c96f-228">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="9c96f-229">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="9c96f-229">CreateSequence Exchange</span></span>

<span data-ttu-id="9c96f-230">WCF 啟動器會產生`CreateSequence`不含提議的訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-230">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="9c96f-231">WCF 回應程式會確保`CreateSequence`建立序列之前不含提議。</span><span class="sxs-lookup"><span data-stu-id="9c96f-231">The WCF Responder ensures that the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="9c96f-232">WCF 回應傳輸`CreateSequenceResponse`HTTP 要求訊息而獲得解決`ReplyTo`端點參考。</span><span class="sxs-lookup"><span data-stu-id="9c96f-232">The WCF Responder transmits the `CreateSequenceResponse` message on an HTTP request addressed with the `ReplyTo` endpoint reference.</span></span>

### <a name="duplex-addressable-initiator"></a><span data-ttu-id="9c96f-233">雙工、可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="9c96f-233">Duplex, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="9c96f-234">繫結</span><span class="sxs-lookup"><span data-stu-id="9c96f-234">Binding</span></span>

<span data-ttu-id="9c96f-235">WCF 提供完全非同步的雙向訊息交換模式使用一個傳入與一個傳出 HTTP 通道上的兩個序列。</span><span class="sxs-lookup"><span data-stu-id="9c96f-235">WCF provides a fully asynchronous two-way message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="9c96f-236">WCF 會使用 HTTP 要求來傳送所有訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-236">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="9c96f-237">所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="9c96f-237">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="9c96f-238">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="9c96f-238">CreateSequence Exchange</span></span>

<span data-ttu-id="9c96f-239">WCF 啟動器會產生`CreateSequence`供應項目訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-239">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="9c96f-240">WCF 回應程式會確保`CreateSequence`供應項目中建立序列之前。</span><span class="sxs-lookup"><span data-stu-id="9c96f-240">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="9c96f-241">WCF 傳送`CreateSequenceResponse`HTTP 要求傳送給`CreateSequence`的`ReplyTo`端點參考。</span><span class="sxs-lookup"><span data-stu-id="9c96f-241">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>

#### <a name="sequence-lifetime"></a><span data-ttu-id="9c96f-242">序列存留期</span><span class="sxs-lookup"><span data-stu-id="9c96f-242">Sequence Lifetime</span></span>

<span data-ttu-id="9c96f-243">WCF 會將兩個序列視為一個全雙工工作階段。</span><span class="sxs-lookup"><span data-stu-id="9c96f-243">WCF treats the two sequences as one fully duplex session.</span></span>

<span data-ttu-id="9c96f-244">在產生可挑剔某個序列的錯誤，WCF 會預期遠端端點將同時挑剔兩個序列。</span><span class="sxs-lookup"><span data-stu-id="9c96f-244">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="9c96f-245">在讀取可挑剔某個序列的錯誤，WCF 會挑剔兩個序列。</span><span class="sxs-lookup"><span data-stu-id="9c96f-245">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>

<span data-ttu-id="9c96f-246">WCF 可以關閉其傳出序列並繼續處理其傳入序列的訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-246">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="9c96f-247">相反地，WCF 可以處理傳入序列的關閉，並繼續傳送其傳出序列的訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-247">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>

### <a name="request-reply-non-addressable-initiator"></a><span data-ttu-id="9c96f-248">要求-回覆、不可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="9c96f-248">Request-Reply, Non-Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="9c96f-249">繫結</span><span class="sxs-lookup"><span data-stu-id="9c96f-249">Binding</span></span>

<span data-ttu-id="9c96f-250">WCF 提供單向和要求-回覆訊息交換模式使用兩個序列透過在一個 HTTP 通道。</span><span class="sxs-lookup"><span data-stu-id="9c96f-250">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="9c96f-251">WCF 會使用 HTTP 要求來傳送要求序列訊息，並透過 HTTP 回應來傳送回覆序列的訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-251">WCF uses the HTTP requests to transmit the request sequence’s messages and uses the HTTP responses to transmit the reply sequence’s messages.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="9c96f-252">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="9c96f-252">CreateSequence Exchange</span></span>

<span data-ttu-id="9c96f-253">WCF 啟動器會產生`CreateSequence`供應項目訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-253">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="9c96f-254">WCF 回應程式會確保`CreateSequence`供應項目中建立序列之前。</span><span class="sxs-lookup"><span data-stu-id="9c96f-254">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="9c96f-255">WCF 回應回覆`CreateSequence`要求與`CreateSequenceResponse`訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-255">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="9c96f-256">單向訊息</span><span class="sxs-lookup"><span data-stu-id="9c96f-256">One-way Message</span></span>

<span data-ttu-id="9c96f-257">若要成功完成單向訊息交換通訊協定，WCF 啟動器會傳送要求序列訊息的 HTTP 要求並接收獨立`SequenceAcknowledgement`HTTP 回應的訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-257">To complete a one-way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="9c96f-258">`SequenceAcknowledgement` 必須認可傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-258">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>

<span data-ttu-id="9c96f-259">WCF 回應來回覆要求，並認可、 錯誤或是內含空本文與 HTTP 202 狀態碼的回應。</span><span class="sxs-lookup"><span data-stu-id="9c96f-259">The WCF Responder can reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>

#### <a name="two-way-messages"></a><span data-ttu-id="9c96f-260">雙向訊息</span><span class="sxs-lookup"><span data-stu-id="9c96f-260">Two Way Messages</span></span>

<span data-ttu-id="9c96f-261">若要成功完成雙向訊息交換通訊協定，WCF 啟動者傳送要求序列訊息的 HTTP 要求和接收 HTTP 回應的回覆序列訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-261">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="9c96f-262">回應中必須包含認可傳輸之要求序列訊息的 `SequenceAcknowledgement`。</span><span class="sxs-lookup"><span data-stu-id="9c96f-262">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>

<span data-ttu-id="9c96f-263">WCF 回應來回覆要求應用程式回覆、 錯誤或是內含空本文與 HTTP 202 狀態碼的回應。</span><span class="sxs-lookup"><span data-stu-id="9c96f-263">The WCF Responder can reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>

<span data-ttu-id="9c96f-264">由於單向訊息與應用程式回覆時機的緣故，要求序列訊息的序號與回應訊息的序號彼此並未互相關聯。</span><span class="sxs-lookup"><span data-stu-id="9c96f-264">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>

#### <a name="retrying-replies"></a><span data-ttu-id="9c96f-265">重試回覆</span><span class="sxs-lookup"><span data-stu-id="9c96f-265">Retrying Replies</span></span>

<span data-ttu-id="9c96f-266">WCF 需仰賴雙向訊息交換通訊協定相互關聯的 HTTP 要求-回覆相互關聯。</span><span class="sxs-lookup"><span data-stu-id="9c96f-266">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="9c96f-267">因為這個緣故，WCF 啟動器不會停止重試要求序列訊息，當在認可要求序列訊息，但在 HTTP 回應內含認可、 使用者訊息，或是錯誤時，而不是。</span><span class="sxs-lookup"><span data-stu-id="9c96f-267">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries an acknowledgement, user message, or fault.</span></span> <span data-ttu-id="9c96f-268">WCF 回應重試回覆相互關聯之要求的 HTTP 要求階段上的回覆。</span><span class="sxs-lookup"><span data-stu-id="9c96f-268">The WCF Responder retries replies on the HTTP request leg of the request to which the reply is correlated.</span></span>

#### <a name="lastmessage-exchange"></a><span data-ttu-id="9c96f-269">LastMessage 交換</span><span class="sxs-lookup"><span data-stu-id="9c96f-269">LastMessage Exchange</span></span>

<span data-ttu-id="9c96f-270">WCF 啟動器會產生，並傳送 HTTP 要求階段上的空白主體最後一個訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-270">The WCF Initiator generates and transmits an empty bodied last message on the HTTP request leg.</span></span> <span data-ttu-id="9c96f-271">WCF 需要回應，但會忽略實際的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-271">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="9c96f-272">WCF 回應程式會回覆要求序列的主體空白的最後一則訊息回覆序列的主體空白的最後一個訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-272">The WCF Responder replies to the request sequence’s empty-bodied last message with the reply sequence’s empty-bodied last message.</span></span>

<span data-ttu-id="9c96f-273">如果 WCF 回應者收到的最後一則訊息中的動作 URI 不是`http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`，WCF 則會以最後一則訊息回覆。</span><span class="sxs-lookup"><span data-stu-id="9c96f-273">If the WCF Responder receives a last message in which the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`, WCF replies with a last message.</span></span> <span data-ttu-id="9c96f-274">在雙向訊息交換通訊協定的情況中，最後一則訊息包含應用程式訊息；在單向訊息交換通訊協定的情況中，最後一則訊息包含空白主體。</span><span class="sxs-lookup"><span data-stu-id="9c96f-274">In the case of a two-way message exchange protocol, the last message carries the application message; in the case of a one-way message exchange protocol, the last message is empty.</span></span>

<span data-ttu-id="9c96f-275">WCF 回應程式不需要回覆序列的主體空白的最後一則訊息的通知。</span><span class="sxs-lookup"><span data-stu-id="9c96f-275">The WCF Responder does not require an acknowledgement for the reply sequence’s empty-bodied last message.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="9c96f-276">TerminateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="9c96f-276">TerminateSequence Exchange</span></span>

<span data-ttu-id="9c96f-277">一旦所有要求都收到有效回覆，WCF 啟動器會產生，並傳送要求序列的`TerminateSequence`HTTP 要求階段上的訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-277">When all requests have received a valid reply, the WCF Initiator generates and transmits the request sequence’s `TerminateSequence` message on the HTTP request leg.</span></span> <span data-ttu-id="9c96f-278">WCF 需要回應，但會忽略實際的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-278">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="9c96f-279">回覆要求序列的 WCF 回應`TerminateSequence`透過回覆序列訊息`TerminateSequence`訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-279">The WCF Responder replies to the request sequence’s `TerminateSequence` message with the reply sequence’s `TerminateSequence` message.</span></span>

<span data-ttu-id="9c96f-280">在正常的關機序列中，兩個 `TerminateSequence` 訊息會同時包含完整範圍的 `SequenceAcknowledgement`。</span><span class="sxs-lookup"><span data-stu-id="9c96f-280">In a normal shutdown sequence, both `TerminateSequence` messages carry a full range `SequenceAcknowledgement`.</span></span>

### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="9c96f-281">要求/回覆、可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="9c96f-281">Request/Reply, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="9c96f-282">繫結</span><span class="sxs-lookup"><span data-stu-id="9c96f-282">Binding</span></span>

<span data-ttu-id="9c96f-283">WCF 會提供使用兩個序列，透過在一個傳入與一個傳出 HTTP 通道要求-回覆訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="9c96f-283">WCF provides a request-reply message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="9c96f-284">WCF 會使用 HTTP 要求來傳送所有訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-284">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="9c96f-285">所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="9c96f-285">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="9c96f-286">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="9c96f-286">CreateSequence Exchange</span></span>

<span data-ttu-id="9c96f-287">WCF 啟動器會產生`CreateSequence`供應項目訊息。</span><span class="sxs-lookup"><span data-stu-id="9c96f-287">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="9c96f-288">WCF 回應程式會確保`CreateSequence`供應項目中建立序列之前。</span><span class="sxs-lookup"><span data-stu-id="9c96f-288">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="9c96f-289">WCF 傳送`CreateSequenceResponse`HTTP 要求傳送給`CreateSequence`的`ReplyTo`端點參考。</span><span class="sxs-lookup"><span data-stu-id="9c96f-289">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>

#### <a name="requestreply-correlation"></a><span data-ttu-id="9c96f-290">要求/回覆相互關聯</span><span class="sxs-lookup"><span data-stu-id="9c96f-290">Request/Reply Correlation</span></span>

<span data-ttu-id="9c96f-291">WCF 啟動者可確保所有的應用程式要求訊息都帶有`MessageId`和`ReplyTo`端點參考。</span><span class="sxs-lookup"><span data-stu-id="9c96f-291">The WCF Initiator ensures all application request messages bear a `MessageId` and a `ReplyTo` endpoint reference.</span></span> <span data-ttu-id="9c96f-292">適用於 WCF 啟動器`CreateSequence`訊息的`ReplyTo`上每個應用程式要求訊息的端點參考。</span><span class="sxs-lookup"><span data-stu-id="9c96f-292">The WCF Initiator applies the `CreateSequence` message’s `ReplyTo` endpoint reference on each application request message.</span></span> <span data-ttu-id="9c96f-293">WCF 回應程式會要求傳入的要求訊息都帶有`MessageId`和`ReplyTo`。</span><span class="sxs-lookup"><span data-stu-id="9c96f-293">The WCF Responder requires that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span> <span data-ttu-id="9c96f-294">WCF 回應程式會確保兩個端點參照 URI `CreateSequence` ，而且所有的應用程式要求訊息完全相同。</span><span class="sxs-lookup"><span data-stu-id="9c96f-294">The WCF Responder ensures that the endpoint reference’s URI of both the `CreateSequence` and all application request messages are identical.</span></span>

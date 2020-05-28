---
title: Reliable Messaging Protocol 1.0 版
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: ef45df0f1cae1f20cf34d07d154baee2cad34b29
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2020
ms.locfileid: "84143441"
---
# <a name="reliable-messaging-protocol-version-10"></a><span data-ttu-id="9ed2d-102">Reliable Messaging Protocol 1.0 版</span><span class="sxs-lookup"><span data-stu-id="9ed2d-102">Reliable Messaging Protocol version 1.0</span></span>

<span data-ttu-id="9ed2d-103">本主題涵蓋使用 HTTP 傳輸進行交互操作所需的 WS-TRUST 訊息2月2005（版本1.0）通訊協定 Windows Communication Foundation （WCF）的執行詳細資料。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-Reliable Messaging February 2005 (version 1.0) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="9ed2d-104">WCF 遵循 WS-TRUST 訊息規格與本主題所述的條件約束和說明。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-104">WCF follows the WS-Reliable Messaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="9ed2d-105">請注意，ws-reliablemessaging 版本1.0 通訊協定是從 WinFX 開始實行。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-105">Note that the WS-ReliableMessaging version 1.0 protocol is implemented starting with the WinFX.</span></span>

<span data-ttu-id="9ed2d-106">WS-可靠訊息2月2005通訊協定是在 WCF 中由所執行 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> 。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-106">The WS-Reliable Messaging February 2005 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>

<span data-ttu-id="9ed2d-107">為了方便起見，本主題將使用下列角色：</span><span class="sxs-lookup"><span data-stu-id="9ed2d-107">For convenience, the topic uses the following roles:</span></span>

- <span data-ttu-id="9ed2d-108">啟動器：啟動 WS-Reliable 訊息序列建立作業的用戶端</span><span class="sxs-lookup"><span data-stu-id="9ed2d-108">Initiator: the client that initiates WS-Reliable Message sequence creation</span></span>

- <span data-ttu-id="9ed2d-109">回應程式：接收啟動器要求的服務</span><span class="sxs-lookup"><span data-stu-id="9ed2d-109">Responder: the service that receives the initiator's requests</span></span>

<span data-ttu-id="9ed2d-110">本文件會使用下表的前置詞和命名空間。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-110">This document uses the prefixes and namespaces in the following table.</span></span>

|<span data-ttu-id="9ed2d-111">前置詞</span><span class="sxs-lookup"><span data-stu-id="9ed2d-111">Prefix</span></span>|<span data-ttu-id="9ed2d-112">命名空間</span><span class="sxs-lookup"><span data-stu-id="9ed2d-112">Namespace</span></span>|
|------------|---------------|
|<span data-ttu-id="9ed2d-113">wsrm</span><span class="sxs-lookup"><span data-stu-id="9ed2d-113">wsrm</span></span>|`http://schemas.xmlsoap.org/ws/2005/02/rm`|
|<span data-ttu-id="9ed2d-114">netrm</span><span class="sxs-lookup"><span data-stu-id="9ed2d-114">netrm</span></span>|`http://schemas.microsoft.com/ws/2006/05/rm`|
|<span data-ttu-id="9ed2d-115">s</span><span class="sxs-lookup"><span data-stu-id="9ed2d-115">s</span></span>|`http://www.w3.org/2003/05/soap-envelope`|
|<span data-ttu-id="9ed2d-116">wsa</span><span class="sxs-lookup"><span data-stu-id="9ed2d-116">wsa</span></span>|`http://schemas.xmlsoap.org/ws/2005/08/addressing|
|<span data-ttu-id="9ed2d-117">wsse</span><span class="sxs-lookup"><span data-stu-id="9ed2d-117">wsse</span></span>|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd`|

## <a name="messaging"></a><span data-ttu-id="9ed2d-118">Messaging (傳訊)</span><span class="sxs-lookup"><span data-stu-id="9ed2d-118">Messaging</span></span>

### <a name="sequence-establishment-messages"></a><span data-ttu-id="9ed2d-119">序列建立訊息</span><span class="sxs-lookup"><span data-stu-id="9ed2d-119">Sequence Establishment Messages</span></span>

<span data-ttu-id="9ed2d-120">WCF 會執行 `CreateSequence` 和 `CreateSequenceResponse` 訊息，以建立可靠的訊息順序。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-120">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable message sequence.</span></span> <span data-ttu-id="9ed2d-121">以下是適用的條件約束：</span><span class="sxs-lookup"><span data-stu-id="9ed2d-121">The following constraints apply:</span></span>

- <span data-ttu-id="9ed2d-122">B1101： WCF 啟動器不會在訊息中產生選擇性的 Expires 元素， `CreateSequence` 或在訊息包含專案的情況下，在專案 `CreateSequence` `Offer` 中使用選擇性的 `Expires` 元素 `Offer` 。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-122">B1101: The WCF Initiator does not generate the optional Expires element in the `CreateSequence` message or, in the cases when the `CreateSequence` message contains an `Offer` element, the optional `Expires` element in the `Offer` element.</span></span>

- <span data-ttu-id="9ed2d-123">B1102：存取訊息時 `CreateSequence` ，WCF 會傳送 `Responder` 和接收兩個 `Expires` 元素（如果有的話），但不會使用它們的值。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-123">B1102: When accessing the `CreateSequence` message, the WCF`Responder` sends and receives both `Expires` elements if they exist, but does not use their values.</span></span>

<span data-ttu-id="9ed2d-124">WS-Reliable 訊息會使用 `Offer` 機制來建立兩個反向關聯序列以形成工作階段。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-124">WS-Reliable Messaging introduces the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>

- <span data-ttu-id="9ed2d-125">R1103：如果 `CreateSequence` 包含 `Offer` 項目，則可信賴傳訊回應程式必須接收序列並以包含 `CreateSequenceResponse` 項目的 `wsrm:Accept` 來回應，以形成兩個相互關聯的反向序列，或是拒絕 `CreateSequence` 要求。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-125">R1103: If `CreateSequence` contains an `Offer` element, the Reliable Messaging Responder must either accept the sequence and respond with `CreateSequenceResponse` that contains a `wsrm:Accept` element, forming two correlated converse sequences or reject the `CreateSequence` request.</span></span>

- <span data-ttu-id="9ed2d-126">R1104：流經反向序列的 `SequenceAcknowledgement` 和應用程式訊息必須傳送到 `ReplyTo` 的 `CreateSequence` 端點參考。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-126">R1104: `SequenceAcknowledgement` and application messages flowing on converse sequence must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>

- <span data-ttu-id="9ed2d-127">R1105：`AcksTo` 中的 `ReplyTo` 和 `CreateSequence` 端點參考必須具有位址值以符合八位元規格。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-127">R1105: `AcksTo` and `ReplyTo` endpoint references in the `CreateSequence` must have address values that match the octet-wise.</span></span>

  <span data-ttu-id="9ed2d-128">WCF 回應程式 `AcksTo` 會在建立序列之前，確認和 EPRs 的 URI 部分 `ReplyTo` 是否相同。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-128">The WCF Responder verifies that the URI portion of the `AcksTo` and `ReplyTo` EPRs are identical before creating a sequence.</span></span>

- <span data-ttu-id="9ed2d-129">R1106：`AcksTo` 訊息中的 `ReplyTo` 和 `CreateSequence` 端點參照應該具有相同的參照參數集合。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-129">R1106: `AcksTo` and `ReplyTo` Endpoint References in the `CreateSequence` should have the same set of reference parameters.</span></span>

  <span data-ttu-id="9ed2d-130">WCF 不會強制執行，但會假設和 on 的 [參考參數] `AcksTo` `ReplyTo` `CreateSequence` 相同，並使用來自端點參考的 [參考參數] `ReplyTo` 來取得通知和反向順序訊息。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-130">WCF does not enforce but assumes that [reference parameters] of `AcksTo` and `ReplyTo` on `CreateSequence` are identical and uses [reference parameters] from `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>

- <span data-ttu-id="9ed2d-131">R1107：當兩個反向序列都是透過 `Offer` 機制建立時，流經反向序列的 `SequenceAcknowledgement` 和應用程式訊息必須傳送至 `ReplyTo` 的 `CreateSequence` 端點參考。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-131">R1107: When two converse sequences are established using the `Offer` mechanism, `SequenceAcknowledgement` and application messages flowing on converse sequences must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>

- <span data-ttu-id="9ed2d-132">R1108：當兩個反向序列都透過 Offer 機制建立時，`[address]` 端點參考子項目 (屬於 `wsrm:AcksTo` 的 `wsrm:Accept` 項目) 的 `CreateSequenceResponse` 屬性必須符合 `CreateSequence` 的目的地 URI 的位元組規格。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-132">R1108: When two converse sequences are established using the Offer mechanism, the `[address]` property of the `wsrm:AcksTo` Endpoint Reference child element of the `wsrm:Accept` element of the `CreateSequenceResponse` must match byte-wise the destination URI of the `CreateSequence`.</span></span>

- <span data-ttu-id="9ed2d-133">R1109：當兩個反向序列都是透過 `Offer` 機制建立時，從啟動器傳送的訊息以及透過回應程式對訊息的認可，必須傳送至相同的端點參考。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-133">R1109: When two converse sequences are established using the `Offer` mechanism, messages sent by initiator and acknowledgements to messages by responder must be sent to the same Endpoint Reference.</span></span>

  <span data-ttu-id="9ed2d-134">WCF 使用 WS-TRUST 訊息，在啟動器和回應程式之間建立可靠的會話。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-134">WCF uses WS-Reliable Messaging to establish reliable sessions between the Initiator and Responder.</span></span> <span data-ttu-id="9ed2d-135">WCF 的 WS-TRUST 訊息執行可為單向、要求-回復與全雙工訊息模式提供可靠的會話。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-135">WCF's WS-Reliable Messaging implementation provides reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="9ed2d-136">上的 WS-可靠訊息 `Offer` 機制 `CreateSequence` / `CreateSequenceResponse` 可讓您建立兩個相互關聯的反向序列，並提供適用于所有訊息端點的會話通訊協定。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-136">The WS-Reliable Messaging `Offer` mechanism on `CreateSequence`/`CreateSequenceResponse` lets you establish two correlated converse sequences, and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="9ed2d-137">因為 WCF 會針對這類會話提供安全性保證，包括會話完整性的端對端保護，所以確保適用于同一方的訊息會抵達相同的目的地。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-137">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure messages intended to the same party are arriving at the same destination.</span></span> <span data-ttu-id="9ed2d-138">這麼做也可以針對應用程式訊息進行 Piggy-Backing 的序列認可作業。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-138">This also allows piggy-backing of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="9ed2d-139">因此，條件約束 R1104、R1105 和 R1108 適用于 WCF。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-139">Therefore, constraints R1104, R1105, and R1108 apply to WCF.</span></span>

<span data-ttu-id="9ed2d-140">`CreateSequence` 訊息的範例。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-140">An example of a `CreateSequence` message.</span></span>

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

 <span data-ttu-id="9ed2d-141">`CreateSequenceResponse` 訊息的範例。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-141">An example of a `CreateSequenceResponse` message.</span></span>

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

### <a name="sequence"></a><span data-ttu-id="9ed2d-142">順序</span><span class="sxs-lookup"><span data-stu-id="9ed2d-142">Sequence</span></span>

<span data-ttu-id="9ed2d-143">下列清單列出適用於序列的條件約束：</span><span class="sxs-lookup"><span data-stu-id="9ed2d-143">The following is a list of constraints that apply to sequences:</span></span>

- <span data-ttu-id="9ed2d-144">B1201： WCF 會產生並存取不超過 `xs:long` 最大內含值9223372036854775807的序號。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-144">B1201:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>

- <span data-ttu-id="9ed2d-145">B1202： WCF 一律會產生具有動作 URI 的空白主體最後訊息 `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` 。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-145">B1202:WCF always generates an empty-bodied last message with the action URI of `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>

- <span data-ttu-id="9ed2d-146">B1203： `LastMessage` 只要動作 URI 不是，WCF 就會接收並傳遞包含專案之 Sequence 標頭的訊息 `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` 。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-146">B1203: WCF receives and delivers a message with a Sequence header that contains a `LastMessage` element as long as the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>

<span data-ttu-id="9ed2d-147">序列標頭的範例。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-147">An example of a Sequence Header.</span></span>

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

### <a name="ackrequested-header"></a><span data-ttu-id="9ed2d-148">AckRequested 標頭</span><span class="sxs-lookup"><span data-stu-id="9ed2d-148">AckRequested Header</span></span>

<span data-ttu-id="9ed2d-149">WCF 會使用 `AckRequested` 標頭做為 keep-alive 機制。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-149">WCF uses `AckRequested` Header as a keep-alive mechanism.</span></span> <span data-ttu-id="9ed2d-150">WCF 不會產生選擇性的 `MessageNumber` 元素。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-150">WCF does not generate the optional `MessageNumber` element.</span></span> <span data-ttu-id="9ed2d-151">接收包含專案的 `AckRequested` 標頭訊息時 `MessageNumber` ，WCF 會忽略 `MessageNumber` 元素的值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-151">Upon receiving a message with an `AckRequested` header that contains the `MessageNumber` element, WCF ignores the `MessageNumber` element’s value, as shown in the following example.</span></span>

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement-header"></a><span data-ttu-id="9ed2d-152">SequenceAcknowledgement 標頭</span><span class="sxs-lookup"><span data-stu-id="9ed2d-152">SequenceAcknowledgement Header</span></span>

<span data-ttu-id="9ed2d-153">WCF 會針對 WS-TRUST 訊息中提供的順序通知使用 piggy-back 回溯機制。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-153">WCF uses piggy-back mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span>

- <span data-ttu-id="9ed2d-154">R1401：當兩個反向序列透過 `Offer` 機制建立時，`SequenceAcknowledgement` 標頭可以包含在任何傳送至目的收件者的應用程式訊息中。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-154">R1401: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span>

- <span data-ttu-id="9ed2d-155">B1402：當 WCF 必須在接收任何序列訊息（例如，為了滿足訊息）之前產生認可時 `AckRequested` ，wcf `SequenceAcknowledgement` 會產生包含範圍0-0 的標頭，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-155">B1402: When WCF must generate an acknowledgement prior to receiving any sequence messages (for example, to satisfy an `AckRequested` message), WCF generates a `SequenceAcknowledgement` header that contains the range 0-0, as shown in the following example.</span></span>

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="0" Lower="0"/>
  </wsrm:SequenceAcknowledgement>
  ```

- <span data-ttu-id="9ed2d-156">B1403： WCF 不會產生 `SequenceAcknowledgement` 包含 `Nack` 元素但支援元素的標頭 `Nack` 。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-156">B1403: WCF does not generate `SequenceAcknowledgement` headers that contain a `Nack` element but supports `Nack` elements.</span></span>

### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="9ed2d-157">WS-ReliableMessaging 錯誤</span><span class="sxs-lookup"><span data-stu-id="9ed2d-157">WS-ReliableMessaging Faults</span></span>

<span data-ttu-id="9ed2d-158">以下是適用于 WS-TRUST 訊息錯誤之 WCF 實作為條件約束的清單：</span><span class="sxs-lookup"><span data-stu-id="9ed2d-158">The following is a list of constraints that apply to the WCF implementation of WS-Reliable Messaging faults:</span></span>

- <span data-ttu-id="9ed2d-159">B1501： WCF 不會產生 `MessageNumberRollover` 錯誤。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-159">B1501: WCF does not generate `MessageNumberRollover` faults.</span></span>

- <span data-ttu-id="9ed2d-160">B1502： WCF 端點可能會產生 `CreateSequenceRefused` 錯誤，如規格中所述。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-160">B1502:WCF endpoint may generate `CreateSequenceRefused` faults as described in the specification.</span></span>

- <span data-ttu-id="9ed2d-161">B1503：當服務端點達到其連線限制，而且無法處理新的連線時，WCF 會產生額外的 `CreateSequenceRefused` 錯誤子代碼， `netrm:ConnectionLimitReached` 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-161">B1503:When the service endpoint reaches its connection limit and cannot process new connections, WCF generates an additional `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>

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

### <a name="ws-addressing-faults"></a><span data-ttu-id="9ed2d-162">WS-Addressing 錯誤</span><span class="sxs-lookup"><span data-stu-id="9ed2d-162">WS-Addressing Faults</span></span>

<span data-ttu-id="9ed2d-163">因為 WS-TRUST 訊息使用 WS-ADDRESSING，所以 WCF WS-TRUST 訊息執行可能會產生 WS-ADDRESSING 錯誤。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-163">Because WS-Reliable Messaging uses WS-Addressing, WCF WS-Reliable Messaging implementation may generate WS-Addressing faults.</span></span> <span data-ttu-id="9ed2d-164">本節涵蓋 WCF 在 WS-TRUST 訊息層上明確產生的 WS-ADDRESSING 錯誤：</span><span class="sxs-lookup"><span data-stu-id="9ed2d-164">This section covers the WS-Addressing faults that WCF explicitly generates at the WS-Reliable Messaging layer:</span></span>

- <span data-ttu-id="9ed2d-165">B1601：當下列其中一項為真時，WCF 會產生所需的錯誤訊息定址標頭：</span><span class="sxs-lookup"><span data-stu-id="9ed2d-165">B1601:WCF generates the fault Message Addressing Header Required when one of the following is true:</span></span>

  - <span data-ttu-id="9ed2d-166">訊息缺少 `Sequence` 標頭和 `Action` 標頭。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-166">A message is missing a `Sequence` header and an `Action` header.</span></span>

  - <span data-ttu-id="9ed2d-167">`CreateSequence` 訊息缺少 `MessageId` 標頭。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-167">A `CreateSequence` message is missing a `MessageId` header.</span></span>

  - <span data-ttu-id="9ed2d-168">`CreateSequence` 訊息缺少 `ReplyTo` 標頭。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-168">A `CreateSequence` message is missing a `ReplyTo` header.</span></span>

- <span data-ttu-id="9ed2d-169">B1602： WCF 會在回復遺失標頭的訊息時產生不支援的錯誤動作 `Sequence` ，而且具有 `Action` 不能在 ws-trust 訊息規格中辨識的標頭。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-169">B1602:WCF generates the fault Action Not Supported in reply to a message that is missing a `Sequence` header and has an `Action` header that is not a recognized in the WS-Reliable Messaging specification.</span></span>

- <span data-ttu-id="9ed2d-170">B1603： WCF 會產生無法使用的錯誤端點，以指出端點不會根據 `CreateSequence` 訊息的定址標頭檢查來處理序列。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-170">B1603:WCF generates the fault Endpoint Unavailable to indicate that the endpoint does not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>

## <a name="protocol-composition"></a><span data-ttu-id="9ed2d-171">通訊協定組合</span><span class="sxs-lookup"><span data-stu-id="9ed2d-171">Protocol Composition</span></span>

### <a name="composition-with-ws-addressing"></a><span data-ttu-id="9ed2d-172">與 WS-Addressing 組合</span><span class="sxs-lookup"><span data-stu-id="9ed2d-172">Composition with WS-Addressing</span></span>

<span data-ttu-id="9ed2d-173">WCF 支援兩種 WS-ADDRESSING 版本： WS-ADDRESSING 2004/08 [WS-ATOMICTRANSACTION] 和 W3C WS-ADDRESSING 1.0 建議 [WS-ADDRESSING-CORE] 和 [WS-ATOMICTRANSACTION-SOAP]。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-173">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>

<span data-ttu-id="9ed2d-174">儘管 WS-Reliable 訊息規格只提到 WS-Addressing 2004/08，它並未限制要使用的 WS-Addressing 版本。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-174">While the WS-Reliable Messaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="9ed2d-175">以下是適用于 WCF 的條件約束清單：</span><span class="sxs-lookup"><span data-stu-id="9ed2d-175">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="9ed2d-176">R2101：WS-Addressing 2004/08 和 WS-Addressing 1.0 皆可搭配 WS-Reliable 訊息一起使用。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-176">R2101:Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>

- <span data-ttu-id="9ed2d-177">R2102：必須在指定的 WS-TRUST 訊息序列或一對使用機制相互關聯的反向序列中使用 WS-ADDRESSING 的單一版本 `wsrm:Offer` 。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-177">R2102:A single version of WS-Addressing must be used throughout a given WS-Reliable Messaging sequence or a pair of converse sequences correlated by using the `wsrm:Offer` mechanism.</span></span>

### <a name="composition-with-soap"></a><span data-ttu-id="9ed2d-178">與 SOAP 組合</span><span class="sxs-lookup"><span data-stu-id="9ed2d-178">Composition with SOAP</span></span>

<span data-ttu-id="9ed2d-179">WCF 支援搭配使用 SOAP 1.1 和 SOAP 1.2 與 WS-可靠的訊息。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-179">WCF supports use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>

### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="9ed2d-180">與 WS-Security 和 WS-SecureConversation 組合</span><span class="sxs-lookup"><span data-stu-id="9ed2d-180">Composition with WS-Security and WS-SecureConversation</span></span>

<span data-ttu-id="9ed2d-181">WCF 藉由使用安全傳輸（HTTPS）、以 WS-MANAGEMENT 撰寫，以及與 WS-安全交談組合，為 WS-TRUST 訊息序列提供保護。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-181">WCF provides protection for WS-Reliable Messaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="9ed2d-182">以下是適用于 WCF 的條件約束清單：</span><span class="sxs-lookup"><span data-stu-id="9ed2d-182">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="9ed2d-183">R2301：除了個別訊息的完整性和機密性以外，若要保護 WS-TRUST 訊息順序的完整性，WCF 會要求必須使用 WS-安全交談。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-183">R2301:To protect the integrity of a WS-Reliable Messaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>

- <span data-ttu-id="9ed2d-184">R2302：在建立 WS-Reliable 訊息序列之前，必須先建立 WS-Secure Conversation 工作階段。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-184">R2302:AWS-Secure Conversation session must be established prior to establishing WS-Reliable Messaging sequence(s).</span></span>

- <span data-ttu-id="9ed2d-185">R2303：如果 WS-Reliable 訊息序列的存留期超過 WS-Secure Conversation 工作階段的存留期，則使用 WS-Secure Conversation 建立的 `SecurityContextToken` 必須透過對應的 WS-Secure Conversation 更新繫結來加以更新。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-185">R2303: If the WS-Reliable Messaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>

- <span data-ttu-id="9ed2d-186">B2304：WS-Reliable 訊息序列或是一對相互關聯的反向序列一律繫結至單一 WS-SecureConversation 工作階段。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-186">B2304:WS-Reliable Messaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>

  <span data-ttu-id="9ed2d-187">WCF 來源會 `wsse:SecurityTokenReference` 在訊息的元素擴充性區段中產生元素 `CreateSequence` 。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-187">The WCF source generates the `wsse:SecurityTokenReference` element in the element extensibility section of the `CreateSequence` message.</span></span>

- <span data-ttu-id="9ed2d-188">R2305：以 WS-安全對話撰寫時， `CreateSequence` 訊息必須包含 `wsse:SecurityTokenReference` 元素。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-188">R2305:When composed with WS-Secure Conversation, a `CreateSequence` message must contain the `wsse:SecurityTokenReference` element.</span></span>

## <a name="ws-reliable-messaging-ws-policy-assertion"></a><span data-ttu-id="9ed2d-189">WS-Reliable 訊息 WS-Policy 判斷提示</span><span class="sxs-lookup"><span data-stu-id="9ed2d-189">WS-Reliable Messaging WS-Policy Assertion</span></span>

<span data-ttu-id="9ed2d-190">WCF 使用 WS-可靠的訊息 WS-原則判斷提示 `wsrm:RMAssertion` 來描述端點功能。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-190">WCF uses WS-Reliable Messaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="9ed2d-191">以下是適用于 WCF 的條件約束清單：</span><span class="sxs-lookup"><span data-stu-id="9ed2d-191">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="9ed2d-192">B3001： WCF 會 `wsrm:RMAssertion` 將 WS-原則判斷提示附加至 `wsdl:binding` 元素。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-192">B3001: WCF attaches `wsrm:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="9ed2d-193">WCF 同時支援 `wsdl:binding` 和元素的附件 `wsdl:port` 。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-193">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>

- <span data-ttu-id="9ed2d-194">B3002： WCF 支援 WS-可靠訊息判斷提示的下列選擇性屬性，並可在 WCF 上進行控制 `ReliableMessagingBindingElement` ：</span><span class="sxs-lookup"><span data-stu-id="9ed2d-194">B3002: WCF supports the following optional properties of WS-Reliable Messaging assertion and provides control over them on the WCF`ReliableMessagingBindingElement`:</span></span>

  - `wsrm:InactivityTimeout`

  - `wsrm:AcknowledgementInterval`

  <span data-ttu-id="9ed2d-195">以下是一個範例。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-195">The following is an example.</span></span>

  ```xml
  <wsrm:RMAssertion>
    <wsrm:InactivityTimeout Milliseconds="600000" />
    <wsrm:AcknowledgementInterval Milliseconds="200" />
  </wsrm:RMAssertion>
  ```

## <a name="flow-control-ws-reliable-messaging-extension"></a><span data-ttu-id="9ed2d-196">WS-Reliable 訊息延伸的流量控制</span><span class="sxs-lookup"><span data-stu-id="9ed2d-196">Flow Control WS-Reliable Messaging Extension</span></span>

<span data-ttu-id="9ed2d-197">WCF 使用 WS-TRUST 訊息擴充性來提供選擇性額外的更緊密控制序列訊息流程。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-197">WCF uses WS-Reliable Messaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>

<span data-ttu-id="9ed2d-198">藉由將屬性設定為，即可啟用流量控制 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> `true` 。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-198">Flow control is enabled by setting the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="9ed2d-199">以下是適用于 WCF 的條件約束清單：</span><span class="sxs-lookup"><span data-stu-id="9ed2d-199">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="9ed2d-200">B4001 一旦：啟用可靠的訊息流程式控制制時，WCF 會在標頭的專案擴充性 `netrm:BufferRemaining` 中產生元素 `SequenceAcknowledgement` 。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-200">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="9ed2d-201">B4002：啟用可靠的訊息流程式控制制時，WCF 不需要 `netrm:BufferRemaining` 在標頭中出現元素 `SequenceAcknowledgement` ，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-201">B4002: When Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element to be present in `SequenceAcknowledgement` header, as shown in the following example.</span></span>

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

- <span data-ttu-id="9ed2d-202">B4003： WCF `netrm:BufferRemaining` 會使用來指出可靠訊息目的地可以緩衝處理的新訊息數目。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-202">B4003: WCF uses `netrm:BufferRemaining` to indicate how many new messages the Reliable Messaging Destination can buffer.</span></span>

- <span data-ttu-id="9ed2d-203">B4004： WCF 可靠的訊息處理服務會在可靠的訊息目的地應用程式無法快速接收訊息時，限制傳輸的訊息數目。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-203">B4004:The WCF Reliable Messaging Service throttles the number of messages transmitted when the Reliable Messaging destination application cannot receive messages quickly.</span></span> <span data-ttu-id="9ed2d-204">可信賴傳訊目的地會緩衝處理訊息，並讓項目值降為 0。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-204">The Reliable Messaging destination buffers messages and the element’s value drops to 0.</span></span>

- <span data-ttu-id="9ed2d-205">B4005： WCF 會產生 `netrm:BufferRemaining` 介於0到4096（含）之間的整數值，並讀取介於0和 `xs:int` 的 `maxInclusive` 值214748364（含）之間的整數值。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-205">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>

## <a name="message-exchange-patterns"></a><span data-ttu-id="9ed2d-206">訊息交換模式</span><span class="sxs-lookup"><span data-stu-id="9ed2d-206">Message Exchange Patterns</span></span>

<span data-ttu-id="9ed2d-207">本節說明當您針對不同的訊息交換模式使用 WS-TRUST 訊息時，WCF 的行為。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-207">This section describes WCF's behavior when WS-Reliable Messaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="9ed2d-208">在每個訊息交換模式中，會考慮下列兩種部署案例：</span><span class="sxs-lookup"><span data-stu-id="9ed2d-208">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>

- <span data-ttu-id="9ed2d-209">不可定址的啟動器：啟動器位於防火牆後方，回應程式只能透過 HTTP 回應將訊息傳送至啟動器。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-209">Non-Addressable Initiator: Initiator is behind firewall; Responder can deliver messages to Initiator only on HTTP responses.</span></span>

- <span data-ttu-id="9ed2d-210">可定址的啟動器：可將 HTTP 要求同時傳送給啟動器與回應程式，亦即可建立兩個反向 HTTP 連線。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-210">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>

### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="9ed2d-211">單向、不可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="9ed2d-211">One-way, Non-addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="9ed2d-212">繫結</span><span class="sxs-lookup"><span data-stu-id="9ed2d-212">Binding</span></span>

<span data-ttu-id="9ed2d-213">WCF 會在一個 HTTP 通道上使用一個序列來提供單向的訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-213">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="9ed2d-214">WCF 會使用 HTTP 要求，將所有訊息從 RMS 傳送至 RMD 和 HTTP 回應，以將所有訊息從 RMD 傳送至 RMS。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-214">WCF uses the HTTP requests to transmit all messages from the RMS to the RMD and the HTTP response to transmit all messages from the RMD to the RMS.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="9ed2d-215">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="9ed2d-215">CreateSequence Exchange</span></span>

<span data-ttu-id="9ed2d-216">WCF 啟動器會產生 `CreateSequence` 不含供應專案的訊息。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-216">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="9ed2d-217">WCF 回應程式會在 `CreateSequence` 建立序列之前，確保沒有任何供應專案。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-217">The WCF Responder ensures the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="9ed2d-218">WCF 回應程式會 `CreateSequence` 使用訊息來回複要求 `CreateSequenceResponse` 。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-218">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>

#### <a name="sequenceacknowledgement"></a><span data-ttu-id="9ed2d-219">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="9ed2d-219">SequenceAcknowledgement</span></span>

<span data-ttu-id="9ed2d-220">除了訊息和錯誤訊息以外，WCF 啟動器會處理所有訊息回復的 `CreateSequence` 通知。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-220">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="9ed2d-221">WCF 回應者一律會在對序列和訊息的回應中產生獨立的認可 `AckRequested` 。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-221">The WCF Responder always generates a stand-alone acknowledgement in the response to both sequence and `AckRequested` messages.</span></span>

#### <a name="terminatesequence-message"></a><span data-ttu-id="9ed2d-222">TerminateSequence 訊息</span><span class="sxs-lookup"><span data-stu-id="9ed2d-222">TerminateSequence message</span></span>

<span data-ttu-id="9ed2d-223">WCF 會將視為 `TerminateSequence` 單向作業，這表示 HTTP 回應具有空白主體和 HTTP 202 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-223">WCF treats `TerminateSequence` as a one-way operation, meaning the HTTP response has an empty body and HTTP 202 status code.</span></span>

### <a name="one-way-addressable-initiator"></a><span data-ttu-id="9ed2d-224">單向、可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="9ed2d-224">One Way, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="9ed2d-225">繫結</span><span class="sxs-lookup"><span data-stu-id="9ed2d-225">Binding</span></span>

<span data-ttu-id="9ed2d-226">WCF 會在傳入和傳出 Http 通道上使用一個序列來提供單向訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-226">WCF provides a one-way message exchange pattern using one sequence over an inbound and an outbound Http channel.</span></span> <span data-ttu-id="9ed2d-227">WCF 會使用 HTTP 要求來傳送所有訊息。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-227">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="9ed2d-228">所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-228">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="9ed2d-229">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="9ed2d-229">CreateSequence Exchange</span></span>

<span data-ttu-id="9ed2d-230">WCF 啟動器會產生 `CreateSequence` 不含供應專案的訊息。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-230">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="9ed2d-231">WCF 回應程式會在 `CreateSequence` 建立序列之前，確保沒有任何供應專案。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-231">The WCF Responder ensures that the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="9ed2d-232">WCF 回應 `CreateSequenceResponse` 程式會在以端點參考定址的 HTTP 要求上傳輸訊息 `ReplyTo` 。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-232">The WCF Responder transmits the `CreateSequenceResponse` message on an HTTP request addressed with the `ReplyTo` endpoint reference.</span></span>

### <a name="duplex-addressable-initiator"></a><span data-ttu-id="9ed2d-233">雙工、可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="9ed2d-233">Duplex, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="9ed2d-234">繫結</span><span class="sxs-lookup"><span data-stu-id="9ed2d-234">Binding</span></span>

<span data-ttu-id="9ed2d-235">WCF 會在輸入和輸出 HTTP 通道上使用兩個序列，以提供完全非同步雙向訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-235">WCF provides a fully asynchronous two-way message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="9ed2d-236">WCF 會使用 HTTP 要求來傳送所有訊息。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-236">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="9ed2d-237">所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-237">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="9ed2d-238">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="9ed2d-238">CreateSequence Exchange</span></span>

<span data-ttu-id="9ed2d-239">WCF 啟動器會產生 `CreateSequence` 包含供應專案的訊息。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-239">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="9ed2d-240">WCF 回應程式會在 `CreateSequence` 建立序列之前，確保具有供應專案。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-240">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="9ed2d-241">WCF 會將 `CreateSequenceResponse` HTTP 要求的傳送至已定址 `CreateSequence` 的 `ReplyTo` 端點參考。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-241">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>

#### <a name="sequence-lifetime"></a><span data-ttu-id="9ed2d-242">序列存留期</span><span class="sxs-lookup"><span data-stu-id="9ed2d-242">Sequence Lifetime</span></span>

<span data-ttu-id="9ed2d-243">WCF 會將這兩個序列視為一個全雙工會話。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-243">WCF treats the two sequences as one fully duplex session.</span></span>

<span data-ttu-id="9ed2d-244">在產生錯誤一個序列的錯誤時，WCF 會預期遠端端點會同時容錯這兩個序列。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-244">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="9ed2d-245">當讀取錯誤發生一系列的錯誤時，WCF 會同時錯誤這兩個序列。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-245">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>

<span data-ttu-id="9ed2d-246">WCF 可以關閉其輸出序列，並繼續處理其輸入序列的訊息。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-246">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="9ed2d-247">相反地，WCF 可以處理輸入序列的關閉，並繼續以輸出序列來傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-247">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>

### <a name="request-reply-non-addressable-initiator"></a><span data-ttu-id="9ed2d-248">要求-回覆、不可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="9ed2d-248">Request-Reply, Non-Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="9ed2d-249">繫結</span><span class="sxs-lookup"><span data-stu-id="9ed2d-249">Binding</span></span>

<span data-ttu-id="9ed2d-250">WCF 透過在一個 HTTP 通道上使用兩個序列的方式，提供單向和要求-回復訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-250">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="9ed2d-251">WCF 會使用 HTTP 要求來傳送要求序列的訊息，並使用 HTTP 回應來傳送回復序列的訊息。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-251">WCF uses the HTTP requests to transmit the request sequence’s messages and uses the HTTP responses to transmit the reply sequence’s messages.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="9ed2d-252">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="9ed2d-252">CreateSequence Exchange</span></span>

<span data-ttu-id="9ed2d-253">WCF 啟動器會產生 `CreateSequence` 包含供應專案的訊息。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-253">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="9ed2d-254">WCF 回應程式會在 `CreateSequence` 建立序列之前，確保具有供應專案。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-254">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="9ed2d-255">WCF 回應程式會 `CreateSequence` 使用訊息來回複要求 `CreateSequenceResponse` 。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-255">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="9ed2d-256">單向訊息</span><span class="sxs-lookup"><span data-stu-id="9ed2d-256">One-way Message</span></span>

<span data-ttu-id="9ed2d-257">為了成功完成單向訊息交換通訊協定，WCF 啟動器會在 HTTP 要求上傳輸要求序列訊息，並 `SequenceAcknowledgement` 在 HTTP 回應上接收獨立的訊息。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-257">To complete a one-way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="9ed2d-258">`SequenceAcknowledgement` 必須認可傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-258">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>

<span data-ttu-id="9ed2d-259">WCF 回應者可以使用通知、錯誤或具有空白本文和 HTTP 202 狀態碼的回應來回複要求。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-259">The WCF Responder can reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>

#### <a name="two-way-messages"></a><span data-ttu-id="9ed2d-260">雙向訊息</span><span class="sxs-lookup"><span data-stu-id="9ed2d-260">Two Way Messages</span></span>

<span data-ttu-id="9ed2d-261">為了成功完成雙向訊息交換通訊協定，WCF 啟動器會在 HTTP 要求上傳輸要求序列訊息，並在 HTTP 回應上接收回複序列訊息。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-261">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="9ed2d-262">回應中必須包含認可傳輸之要求序列訊息的 `SequenceAcknowledgement`。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-262">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>

<span data-ttu-id="9ed2d-263">WCF 回應者可以透過應用程式回復、錯誤或具有空白本文的回應，以及 HTTP 202 狀態碼來回複要求。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-263">The WCF Responder can reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>

<span data-ttu-id="9ed2d-264">由於單向訊息與應用程式回覆時機的緣故，要求序列訊息的序號與回應訊息的序號彼此並未互相關聯。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-264">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>

#### <a name="retrying-replies"></a><span data-ttu-id="9ed2d-265">重試回覆</span><span class="sxs-lookup"><span data-stu-id="9ed2d-265">Retrying Replies</span></span>

<span data-ttu-id="9ed2d-266">WCF 依賴雙向訊息交換通訊協定相互關聯的 HTTP 要求-回復相互關聯。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-266">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="9ed2d-267">因此，在認可要求序列訊息時，WCF 啟動器不會停止重試要求序列訊息，而是在 HTTP 回應攜帶通知、使用者訊息或錯誤時發生。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-267">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries an acknowledgement, user message, or fault.</span></span> <span data-ttu-id="9ed2d-268">WCF 回應程式會在與回復相互關聯之要求的 HTTP 要求階段上，重試回復。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-268">The WCF Responder retries replies on the HTTP request leg of the request to which the reply is correlated.</span></span>

#### <a name="lastmessage-exchange"></a><span data-ttu-id="9ed2d-269">LastMessage 交換</span><span class="sxs-lookup"><span data-stu-id="9ed2d-269">LastMessage Exchange</span></span>

<span data-ttu-id="9ed2d-270">WCF 啟動器會在 HTTP 要求階段上產生並傳送空的主體最後一則訊息。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-270">The WCF Initiator generates and transmits an empty bodied last message on the HTTP request leg.</span></span> <span data-ttu-id="9ed2d-271">WCF 需要回應，但會忽略實際的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-271">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="9ed2d-272">WCF 回應程式會以回復序列的主體最後一則訊息來回複要求序列的空白主體最後一則訊息。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-272">The WCF Responder replies to the request sequence’s empty-bodied last message with the reply sequence’s empty-bodied last message.</span></span>

<span data-ttu-id="9ed2d-273">如果 WCF 回應程式收到動作 URI 不是的最後一則訊息 `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` ，則 WCF 會回復最後一則訊息。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-273">If the WCF Responder receives a last message in which the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`, WCF replies with a last message.</span></span> <span data-ttu-id="9ed2d-274">在雙向訊息交換通訊協定的情況中，最後一則訊息包含應用程式訊息；在單向訊息交換通訊協定的情況中，最後一則訊息包含空白主體。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-274">In the case of a two-way message exchange protocol, the last message carries the application message; in the case of a one-way message exchange protocol, the last message is empty.</span></span>

<span data-ttu-id="9ed2d-275">WCF 回應程式不需要對回復序列的空白主體最後一個訊息進行認可。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-275">The WCF Responder does not require an acknowledgement for the reply sequence’s empty-bodied last message.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="9ed2d-276">TerminateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="9ed2d-276">TerminateSequence Exchange</span></span>

<span data-ttu-id="9ed2d-277">當所有要求都收到有效回復時，WCF 啟動器會在 HTTP 要求階段上產生並傳送要求序列的 `TerminateSequence` 訊息。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-277">When all requests have received a valid reply, the WCF Initiator generates and transmits the request sequence’s `TerminateSequence` message on the HTTP request leg.</span></span> <span data-ttu-id="9ed2d-278">WCF 需要回應，但會忽略實際的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-278">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="9ed2d-279">WCF 回應程式會 `TerminateSequence` 使用回復序列的訊息來回複要求序列的訊息 `TerminateSequence` 。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-279">The WCF Responder replies to the request sequence’s `TerminateSequence` message with the reply sequence’s `TerminateSequence` message.</span></span>

<span data-ttu-id="9ed2d-280">在正常的關機序列中，兩個 `TerminateSequence` 訊息會同時包含完整範圍的 `SequenceAcknowledgement`。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-280">In a normal shutdown sequence, both `TerminateSequence` messages carry a full range `SequenceAcknowledgement`.</span></span>

### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="9ed2d-281">要求/回覆、可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="9ed2d-281">Request/Reply, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="9ed2d-282">繫結</span><span class="sxs-lookup"><span data-stu-id="9ed2d-282">Binding</span></span>

<span data-ttu-id="9ed2d-283">WCF 會在輸入和輸出 HTTP 通道上使用兩個序列，以提供要求-回復訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-283">WCF provides a request-reply message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="9ed2d-284">WCF 會使用 HTTP 要求來傳送所有訊息。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-284">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="9ed2d-285">所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-285">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="9ed2d-286">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="9ed2d-286">CreateSequence Exchange</span></span>

<span data-ttu-id="9ed2d-287">WCF 啟動器會產生 `CreateSequence` 包含供應專案的訊息。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-287">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="9ed2d-288">WCF 回應程式會在 `CreateSequence` 建立序列之前，確保具有供應專案。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-288">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="9ed2d-289">WCF 會將 `CreateSequenceResponse` HTTP 要求的傳送至已定址 `CreateSequence` 的 `ReplyTo` 端點參考。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-289">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>

#### <a name="requestreply-correlation"></a><span data-ttu-id="9ed2d-290">要求/回覆相互關聯</span><span class="sxs-lookup"><span data-stu-id="9ed2d-290">Request/Reply Correlation</span></span>

<span data-ttu-id="9ed2d-291">WCF 啟動器可確保所有應用程式要求訊息都具有 `MessageId` 和 `ReplyTo` 端點參考。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-291">The WCF Initiator ensures all application request messages bear a `MessageId` and a `ReplyTo` endpoint reference.</span></span> <span data-ttu-id="9ed2d-292">WCF 啟動器會 `CreateSequence` `ReplyTo` 在每個應用程式要求訊息上套用訊息的端點參考。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-292">The WCF Initiator applies the `CreateSequence` message’s `ReplyTo` endpoint reference on each application request message.</span></span> <span data-ttu-id="9ed2d-293">WCF 回應程式要求傳入的要求訊息必須具有 `MessageId` 和 `ReplyTo` 。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-293">The WCF Responder requires that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span> <span data-ttu-id="9ed2d-294">WCF 回應者可確保 `CreateSequence` 和所有應用程式要求訊息的端點參考 URI 都相同。</span><span class="sxs-lookup"><span data-stu-id="9ed2d-294">The WCF Responder ensures that the endpoint reference’s URI of both the `CreateSequence` and all application request messages are identical.</span></span>

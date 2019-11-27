---
title: Reliable Messaging Protocol 1.1 版
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: 9320787317131f42c4a82c6114a16fdea87567f4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283304"
---
# <a name="reliable-messaging-protocol-version-11"></a><span data-ttu-id="ad9d8-102">Reliable Messaging Protocol 1.1 版</span><span class="sxs-lookup"><span data-stu-id="ad9d8-102">Reliable Messaging Protocol version 1.1</span></span>

<span data-ttu-id="ad9d8-103">本主題涵蓋使用 HTTP 傳輸進行交互操作所需之 WS-RELIABLEMESSAGING 2007 （1.1 版）通訊協定的 Windows Communication Foundation （WCF）執行詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-ReliableMessaging February 2007 (version 1.1) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="ad9d8-104">WCF 遵循 WS-RELIABLEMESSAGING 規格與本主題所述的條件約束和說明。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-104">WCF follows the WS-ReliableMessaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="ad9d8-105">請注意，ws-reliablemessaging 1.1 通訊協定是從 .NET Framework 3.5 開始實行。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-105">Note that the WS-ReliableMessaging version 1.1 protocol is implemented starting with .NET Framework 3.5.</span></span>

<span data-ttu-id="ad9d8-106">Ws-reliablemessaging 2007 通訊協定會由 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>在 WCF 中執行。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-106">The WS-ReliableMessaging February 2007 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>

<span data-ttu-id="ad9d8-107">為了方便起見，本主題將使用下列角色：</span><span class="sxs-lookup"><span data-stu-id="ad9d8-107">For convenience, the topic uses the following roles:</span></span>

- <span data-ttu-id="ad9d8-108">啟動器：啟動 WS-Reliable 訊息序列建立作業的用戶端。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-108">Initiator: The client that initiates WS-Reliable Message sequence creation.</span></span>

- <span data-ttu-id="ad9d8-109">回應程式：接收啟動器要求的服務。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-109">Responder: The service that receives the initiator's requests.</span></span>

 <span data-ttu-id="ad9d8-110">本文件會使用下表的前置詞和命名空間。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-110">This document uses the prefixes and namespaces in the following table.</span></span>

|<span data-ttu-id="ad9d8-111">前置詞</span><span class="sxs-lookup"><span data-stu-id="ad9d8-111">Prefix</span></span>|<span data-ttu-id="ad9d8-112">命名空間</span><span class="sxs-lookup"><span data-stu-id="ad9d8-112">Namespace</span></span>|
|-|-|
|<span data-ttu-id="ad9d8-113">wsrm</span><span class="sxs-lookup"><span data-stu-id="ad9d8-113">wsrm</span></span>|http://docs.oasis-open.org/ws-rx/wsrm/200702|
|<span data-ttu-id="ad9d8-114">netrm</span><span class="sxs-lookup"><span data-stu-id="ad9d8-114">netrm</span></span>|http://schemas.microsoft.com/ws/2006/05/rm|
|<span data-ttu-id="ad9d8-115">s</span><span class="sxs-lookup"><span data-stu-id="ad9d8-115">s</span></span>|http://www.w3.org/2003/05/soap-envelope|
|<span data-ttu-id="ad9d8-116">wsa</span><span class="sxs-lookup"><span data-stu-id="ad9d8-116">wsa</span></span>|http://schemas.xmlsoap.org/ws/2005/08/addressing|
|<span data-ttu-id="ad9d8-117">wsse</span><span class="sxs-lookup"><span data-stu-id="ad9d8-117">wsse</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|
|<span data-ttu-id="ad9d8-118">wsrmp</span><span class="sxs-lookup"><span data-stu-id="ad9d8-118">wsrmp</span></span>|http://docs.oasis-open.org/ws-rx/wsrmp/200702|
|<span data-ttu-id="ad9d8-119">netrmp</span><span class="sxs-lookup"><span data-stu-id="ad9d8-119">netrmp</span></span>|http://schemas.microsoft.com/ws-rx/wsrmp/200702|
|<span data-ttu-id="ad9d8-120">wsp</span><span class="sxs-lookup"><span data-stu-id="ad9d8-120">wsp</span></span>|<span data-ttu-id="ad9d8-121">(WS-Policy 1.2 或 WS-Policy 1.5)</span><span class="sxs-lookup"><span data-stu-id="ad9d8-121">(Either WS-Policy 1.2 or WS-Policy 1.5)</span></span>|

## <a name="messaging"></a><span data-ttu-id="ad9d8-122">訊息</span><span class="sxs-lookup"><span data-stu-id="ad9d8-122">Messaging</span></span>

### <a name="sequence-creation"></a><span data-ttu-id="ad9d8-123">建立序列</span><span class="sxs-lookup"><span data-stu-id="ad9d8-123">Sequence Creation</span></span>

<span data-ttu-id="ad9d8-124">WCF 會執行 `CreateSequence` 和 `CreateSequenceResponse` 訊息，以建立可靠的訊息順序。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-124">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable messaging sequence.</span></span> <span data-ttu-id="ad9d8-125">以下是適用的條件約束：</span><span class="sxs-lookup"><span data-stu-id="ad9d8-125">The following constraints apply:</span></span>

- <span data-ttu-id="ad9d8-126">B1101： WCF 啟動器會使用與 `CreateSequence` 訊息 `ReplyTo`、`AcksTo` 和 `Offer/Endpoint`相同的端點參考。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-126">B1101: The WCF Initiator uses the same endpoint reference as the `CreateSequence` message’s `ReplyTo`, `AcksTo` and `Offer/Endpoint`.</span></span>

- <span data-ttu-id="ad9d8-127">R1102：`AcksTo` 訊息中的 `ReplyTo`、`Offer/Endpoint` 和 `CreateSequence` 端點參照必須具有包含相同字串表示的位址值以符合八位元規格。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-127">R1102: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message must have address values with identical string representations such that they match the octet-wise.</span></span>

  - <span data-ttu-id="ad9d8-128">WCF 回應程式會在建立序列之前，確認 `AcksTo`、`ReplyTo` 和 `Endpoint` 端點參考的 URI 部分都相同。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-128">The WCF Responder verifies that the URI portion of the `AcksTo`, `ReplyTo` and `Endpoint` endpoint references are identical before creating a sequence.</span></span>

- <span data-ttu-id="ad9d8-129">R1103：`AcksTo` 訊息中的 `ReplyTo`、`Offer/Endpoint` 和 `CreateSequence` 端點參照應該具有相同的參照參數集合。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-129">R1103: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message should have the same set of reference parameters.</span></span>

  - <span data-ttu-id="ad9d8-130">WCF 不會強制執行，但會假設 `CreateSequence` 上的 `AcksTo`、`ReplyTo` 和 `Offer/Endpoint` 端點參考的參考參數完全相同，並使用來自 `ReplyTo` 端點參考的參考參數來取得通知和反向序列訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-130">WCF does not enforce, but assumes that reference parameters of the `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references on `CreateSequence` are identical and uses reference parameters from the `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>

- <span data-ttu-id="ad9d8-131">B1104： WCF 啟動器不會在 `CreateSequence` 訊息中產生選擇性的 `Expires` 或 `Offer/Expires` 元素。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-131">B1104: The WCF Initiator does not generate the optional `Expires` or `Offer/Expires` element in the `CreateSequence` message.</span></span>

- <span data-ttu-id="ad9d8-132">B1105：存取 `CreateSequence` 訊息時，WCF 回應者會使用 `CreateSequence` 元素中的 `Expires` 值，做為 `CreateSequenceResponse` 元素中的 `Expires` 值。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-132">B1105: When accessing the `CreateSequence` message, the WCF Responder uses the `Expires` value in the `CreateSequence` element as the `Expires` value in the `CreateSequenceResponse` element.</span></span> <span data-ttu-id="ad9d8-133">否則，WCF 回應程式會讀取並忽略 `Expires` 和 `Offer/Expires` 值。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-133">Otherwise, the WCF Responder reads and ignores the `Expires` and `Offer/Expires` values.</span></span>

- <span data-ttu-id="ad9d8-134">B1106：存取 `CreateSequenceResponse` 訊息時，WCF 啟動器會讀取選用的 `Expires` 值，但不會使用它。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-134">B1106: When accessing the `CreateSequenceResponse` message, the WCF Initiator reads the optional `Expires` value but does not use it.</span></span>

- <span data-ttu-id="ad9d8-135">B1107： WCF 啟動器和回應程式一律會在 `CreateSequence/Offer` 和 `CreateSequenceResponse` 專案中產生選擇性的 `IncompleteSequenceBehavior` 元素。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-135">B1107: The WCF Initiator and Responder always generate the optional `IncompleteSequenceBehavior` element in the `CreateSequence/Offer` and `CreateSequenceResponse` elements.</span></span>

- <span data-ttu-id="ad9d8-136">B1108： WCF 只會使用 `IncompleteSequenceBehavior` 元素中的 `DiscardFollowingFirstGap` 和 `NoDiscard` 值。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-136">B1108: WCF uses only the `DiscardFollowingFirstGap` and `NoDiscard` values in the `IncompleteSequenceBehavior` element.</span></span>

  - <span data-ttu-id="ad9d8-137">WS-ReliableMessaging 會使用 `Offer` 機制來建立兩個反向關聯序列以形成工作階段。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-137">WS-ReliableMessaging utilizes the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>

- <span data-ttu-id="ad9d8-138">B1109：如果 `CreateSequence` 包含 `Offer` 元素，則 WCF 回應程式會以不含 `Accept` 元素的 `CreateSequenceResponse` 回應，來拒絕所提供的序列。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-138">B1109: If `CreateSequence` contains an `Offer` element, the one way WCF Responder rejects the offered sequence by responding with a `CreateSequenceResponse` without an `Accept` element.</span></span>

- <span data-ttu-id="ad9d8-139">B1110：如果可靠的訊息回應程式拒絕所提供的順序，WCF 啟動器會將新建立的序列錯誤。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-139">B1110: If a Reliable Messaging Responder rejects the offered sequence, the WCF Initiator faults the newly established sequence.</span></span>

- <span data-ttu-id="ad9d8-140">B1111：如果 `CreateSequence` 不包含 `Offer` 元素，雙向 WCF 回應程式會藉由回應 `CreateSequenceRefused` 錯誤來拒絕提供的序列。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-140">B1111: If `CreateSequence` does not contain an `Offer` element, the two-way WCF Responder rejects the offered sequence by responding with a `CreateSequenceRefused` fault.</span></span>

- <span data-ttu-id="ad9d8-141">R1112：當兩個反向序列都是透過 `Offer` 機制建立時，`[address]` 端點參照之 `CreateSequenceResponse/Accept/AcksTo` 屬性的每個位元組必須完全符合 `CreateSequence` 訊息之目的 URI 的每個位元組。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-141">R1112: When two converse sequences are established using the `Offer` mechanism, the `[address]` property of the `CreateSequenceResponse/Accept/AcksTo` endpoint reference must match the destination URI of the `CreateSequence` message byte for byte.</span></span>

- <span data-ttu-id="ad9d8-142">R1113：當兩個反向序列都是透過 `Offer` 機制建立時，從啟動器流向回應程式之雙邊序列上的所有訊息必須傳送至相同的端點參照。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-142">R1113: When two converse sequences are established using the `Offer` mechanism, all messages on both sequences flowing from the Initiator to the Responder must be sent to the same endpoint reference.</span></span>

<span data-ttu-id="ad9d8-143">WCF 使用 WS-RELIABLEMESSAGING 在啟動器和回應程式之間建立可靠的會話。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-143">WCF uses WS-ReliableMessaging to establish reliable sessions between the Initiator and the Responder.</span></span> <span data-ttu-id="ad9d8-144">WCF ws-reliablemessaging 實行會針對單向、要求-回復與全雙工訊息模式提供可靠的會話。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-144">The WCF WS-ReliableMessaging implementation provides a reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="ad9d8-145">`Offer` 和 `CreateSequence` 上的 WS-ReliableMessaging `CreateSequenceResponse` 機制可讓您建立兩個相互關聯的反向序列，並提供適用於所有訊息端點的工作階段通訊協定。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-145">The WS-ReliableMessaging `Offer` mechanism on `CreateSequence` and `CreateSequenceResponse` lets you establish two correlated converse sequences and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="ad9d8-146">因為 WCF 會針對這類會話提供安全性保證，包括會話完整性的端對端保護，所以確保適用于同一方的訊息會到達相同的目的地。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-146">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure that messages intended for the same party arrive at the same destination.</span></span> <span data-ttu-id="ad9d8-147">這麼做也可以針對應用程式訊息進行 "piggy-backing" 的序列認可作業。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-147">This also allows "piggy-backing" of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="ad9d8-148">因此，條件約束 R1102、R1112 和 R1113 適用于 WCF。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-148">Therefore, constraints R1102, R1112, and R1113 apply to WCF.</span></span>

<span data-ttu-id="ad9d8-149">`CreateSequence` 訊息的範例。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-149">An example of a `CreateSequence` message.</span></span>

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

<span data-ttu-id="ad9d8-150">`CreateSequenceResponse` 訊息的範例。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-150">An example of a `CreateSequenceResponse` message.</span></span>

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

### <a name="closing-a-sequence"></a><span data-ttu-id="ad9d8-151">關閉序列</span><span class="sxs-lookup"><span data-stu-id="ad9d8-151">Closing a Sequence</span></span>

<span data-ttu-id="ad9d8-152">WCF 會使用 `CloseSequence` 並 `CloseSequenceResponse` 訊息，以取得可靠的訊息來源起始的關機。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-152">WCF uses the `CloseSequence` and `CloseSequenceResponse` messages for a Reliable Messaging source-initiated shutdown.</span></span> <span data-ttu-id="ad9d8-153">WCF 可靠訊息目的地不會起始關機，而且 WCF 可靠的訊息來源不支援可靠的訊息目的地起始的關閉。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-153">The WCF Reliable Messaging destination does not initiate shutdown and the WCF Reliable Messaging source does not support a Reliable Messaging destination-initiated shutdown.</span></span> <span data-ttu-id="ad9d8-154">以下是適用的條件約束：</span><span class="sxs-lookup"><span data-stu-id="ad9d8-154">The following constraints apply:</span></span>

- <span data-ttu-id="ad9d8-155">B1201： WCF 可靠的訊息來源一律會傳送 `CloseSequence` 訊息，以關閉順序。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-155">B1201: The WCF Reliable Messaging source always sends a `CloseSequence` message to shut down the sequence.</span></span>

- <span data-ttu-id="ad9d8-156">B1202：可信賴傳訊來源會在傳送 `CloseSequence` 訊息之前，等候整個序列訊息的認可。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-156">B1202: The Reliable Messaging source waits for acknowledgement of the full range of sequence messages before sending the `CloseSequence` message.</span></span>

- <span data-ttu-id="ad9d8-157">B1203：可信賴傳訊來源一律包含選用的 `LastMsgNumber` 項目 (除非序列不包含訊息)。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-157">B1203: The Reliable Messaging source always includes the optional `LastMsgNumber` element unless the sequence does not contain messages.</span></span>

- <span data-ttu-id="ad9d8-158">R1204：可信賴傳訊目的地不可以藉由傳送 `CloseSequence` 訊息來啟始關閉作業。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-158">R1204: The Reliable Messaging destination must not initiate shutdown by sending a `CloseSequence` message.</span></span>

- <span data-ttu-id="ad9d8-159">B1205：收到 `CloseSequence` 訊息時，WCF 可靠訊息來源會將序列視為不完整，並傳送錯誤。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-159">B1205: Upon receiving a `CloseSequence` message, the WCF Reliable Messaging source considers the sequence incomplete and sends a fault.</span></span>

 <span data-ttu-id="ad9d8-160">`CloseSequence` 訊息的範例。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-160">An example of a `CloseSequence` message.</span></span>

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
```

<span data-ttu-id="ad9d8-161">範例 `CloseSequenceResponse` 訊息：</span><span class="sxs-lookup"><span data-stu-id="ad9d8-161">Example `CloseSequenceResponse` message:</span></span>

```xml
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

### <a name="sequence-termination"></a><span data-ttu-id="ad9d8-162">終止序列</span><span class="sxs-lookup"><span data-stu-id="ad9d8-162">Sequence Termination</span></span>

<span data-ttu-id="ad9d8-163">WCF 在完成 `CloseSequence/CloseSequenceResponse` 交握之後，主要會使用 `TerminateSequence/TerminateSequenceResponse` 交握。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-163">WCF primarily uses the `TerminateSequence/TerminateSequenceResponse` handshake after completing the `CloseSequence/CloseSequenceResponse` handshake.</span></span> <span data-ttu-id="ad9d8-164">WCF 可靠訊息目的地不會起始終止，而且可靠的訊息來源不支援可靠的訊息目的地起始的終止。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-164">The WCF Reliable Messaging destination does not initiate termination and the Reliable Messaging source does not support a Reliable Messaging destination-initiated termination.</span></span> <span data-ttu-id="ad9d8-165">以下是適用的條件約束：</span><span class="sxs-lookup"><span data-stu-id="ad9d8-165">The following constraints apply:</span></span>

- <span data-ttu-id="ad9d8-166">B1301： WCF 啟動器只會在成功完成 `CloseSequence/CloseSequenceResponse` 交握之後傳送 `TerminateSequence` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-166">B1301: The WCF Initiator only sends the `TerminateSequence` message after the successful completion of the `CloseSequence/CloseSequenceResponse` handshake.</span></span>

- <span data-ttu-id="ad9d8-167">R1302： WCF 會驗證指定序列的所有 `CloseSequence` 和 `TerminateSequence` 訊息中的 `LastMsgNumber` 元素是否一致。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-167">R1302: WCF validates that the `LastMsgNumber` element is consistent across all `CloseSequence` and `TerminateSequence` messages for a given sequence.</span></span> <span data-ttu-id="ad9d8-168">也就是說，`LastMsgNumber` 不是不存在於所有 `CloseSequence` 和 `TerminateSequence` 訊息上，就是存在於所有 `CloseSequence` 和 `TerminateSequence` 訊息上而且全部一樣。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-168">This means that `LastMsgNumber` is either not present on all `CloseSequence` and `TerminateSequence` messages, or it is present and identical on all `CloseSequence` and `TerminateSequence` messages.</span></span>

- <span data-ttu-id="ad9d8-169">B1303：在 `TerminateSequence` 交握之後收到 `CloseSequence/CloseSequenceResponse` 訊息時，可信賴傳訊目的地會以 `TerminateSequenceResponse` 訊息來回應。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-169">B1303: When receiving a `TerminateSequence` message after the `CloseSequence/CloseSequenceResponse` handshake, the Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="ad9d8-170">由於可信賴傳訊來源在傳送 `TerminateSequence` 訊息之前已經獲得最後的認可，因此可信賴傳訊目的地毫無疑問地知道序列已結束並立即回收資源。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-170">Because the Reliable Messaging source has the final acknowledgement before sending the `TerminateSequence` message, the Reliable Messaging destination knows without doubt that the sequence ends, and reclaims resources immediately.</span></span>

- <span data-ttu-id="ad9d8-171">B1304：在 `CloseSequence/CloseSequenceResponse` 交握之前收到 `TerminateSequence` 訊息時，WCF 可靠的訊息目的地會以 `TerminateSequenceResponse` 訊息回應。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-171">B1304: When receiving a `TerminateSequence` message prior to the `CloseSequence/CloseSequenceResponse` handshake, the WCF Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="ad9d8-172">如果可信賴傳訊目的地判斷序列中沒有任何不一致的項目，則可信賴傳訊目的地會等候應用程式目的地指定的時間一到再回收資源，以便讓用戶端有機會接收最後的認可。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-172">If the Reliable Messaging destination determines that there are no inconsistencies in the sequence, the Reliable Messaging destination waits for an application destination-specified time before reclaiming resources, to allow the client the chance to receive the final acknowledgement.</span></span> <span data-ttu-id="ad9d8-173">否則，可信賴傳訊目的地會立即回收資源並引發 `Faulted` 事件以向應用程式目的地指出序列是在不確定的情況下結束。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-173">Otherwise, the Reliable Messaging destination reclaims resources immediately and indicates to the application destination that the sequence ends with doubt by raising the `Faulted` event.</span></span>

<span data-ttu-id="ad9d8-174">`TerminateSequence` 訊息的範例。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-174">An example of a `TerminateSequence` message.</span></span>

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
```

<span data-ttu-id="ad9d8-175">範例 `TerminateSequenceResponse` 訊息：</span><span class="sxs-lookup"><span data-stu-id="ad9d8-175">Example `TerminateSequenceResponse` message:</span></span>

```xml
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

### <a name="sequences"></a><span data-ttu-id="ad9d8-176">序列</span><span class="sxs-lookup"><span data-stu-id="ad9d8-176">Sequences</span></span>

<span data-ttu-id="ad9d8-177">下列清單列出適用於序列的條件約束：</span><span class="sxs-lookup"><span data-stu-id="ad9d8-177">The following is a list of constraints that apply to sequences:</span></span>

- <span data-ttu-id="ad9d8-178">B1401： WCF 會產生並存取不超過 `xs:long`的最大內含值9223372036854775807的序號。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-178">B1401:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>

<span data-ttu-id="ad9d8-179">`Sequence` 標頭的範例。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-179">An example of a `Sequence` header.</span></span>

```xml
<wsrm:Sequence s:mustUnderstand="1">
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:MessageNumber>1</wsrm:MessageNumber>
</wsrm:Sequence>
```

### <a name="request-acknowledgement"></a><span data-ttu-id="ad9d8-180">要求認可</span><span class="sxs-lookup"><span data-stu-id="ad9d8-180">Request Acknowledgement</span></span>

<span data-ttu-id="ad9d8-181">WCF 使用 `AckRequested` 標頭做為 keep-alive 機制。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-181">WCF uses the `AckRequested` header as a keep-alive mechanism.</span></span>

<span data-ttu-id="ad9d8-182">`AckRequested` 標頭的範例。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-182">An example of an `AckRequested` header.</span></span>

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement"></a><span data-ttu-id="ad9d8-183">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="ad9d8-183">SequenceAcknowledgement</span></span>

<span data-ttu-id="ad9d8-184">WCF 會針對 WS-TRUST 訊息中提供的順序通知使用「piggy-back 後」機制。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-184">WCF uses a "piggy-back" mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span> <span data-ttu-id="ad9d8-185">以下是適用的條件約束：</span><span class="sxs-lookup"><span data-stu-id="ad9d8-185">The following constraints apply:</span></span>

- <span data-ttu-id="ad9d8-186">R1601：當兩個反向序列是使用 `Offer` 機制建立時，`SequenceAcknowledgement` 標頭可能會包含在傳送給預定收件者的任何應用程式訊息中。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-186">R1601: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span> <span data-ttu-id="ad9d8-187">遠端端點必須能夠存取以 Piggyback 方式傳送的 `SequenceAcknowledgement` 標頭。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-187">The remote endpoint must be able to access a piggybacked `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="ad9d8-188">B1602： WCF 不會產生包含 `Nack` 元素 `SequenceAcknowledgement` 標頭。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-188">B1602: WCF does not generate `SequenceAcknowledgement` headers that contain `Nack` elements.</span></span> <span data-ttu-id="ad9d8-189">WCF 會驗證每個 `Nack` 元素都包含序號，否則會忽略 `Nack` 元素和值。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-189">WCF validates that each `Nack` element contains a sequence number, but otherwise ignores the `Nack` element and value.</span></span>

 <span data-ttu-id="ad9d8-190">`SequenceAcknowledgement` 標頭的範例。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-190">An example of a `SequenceAcknowledgement` header.</span></span>

```xml
<wsrm:SequenceAcknowledgement>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>
</wsrm:SequenceAcknowledgement>
```

### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="ad9d8-191">WS-ReliableMessaging 錯誤</span><span class="sxs-lookup"><span data-stu-id="ad9d8-191">WS-ReliableMessaging Faults</span></span>

<span data-ttu-id="ad9d8-192">以下是適用于 WS-RELIABLEMESSAGING 錯誤之 WCF 執行條件約束的清單。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-192">The following is a list of constraints that apply to the WCF implementation of WS-ReliableMessaging faults.</span></span> <span data-ttu-id="ad9d8-193">以下是適用的條件約束：</span><span class="sxs-lookup"><span data-stu-id="ad9d8-193">The following constraints apply:</span></span>

- <span data-ttu-id="ad9d8-194">B1701： WCF 不會產生 `MessageNumberRollover` 錯誤。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-194">B1701: WCF does not generate `MessageNumberRollover` faults.</span></span>

- <span data-ttu-id="ad9d8-195">B1702： Over SOAP 1.2，當服務端點達到其連線限制，而且無法處理新的連線時，WCF 會產生一個嵌套的 `CreateSequenceRefused` 錯誤子代碼，`netrm:ConnectionLimitReached`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-195">B1702: Over SOAP 1.2, when the service endpoint reaches its connection limit and cannot process new connections, WCF generates a nested `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>

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

### <a name="ws-addressing-faults"></a><span data-ttu-id="ad9d8-196">WS-Addressing 錯誤</span><span class="sxs-lookup"><span data-stu-id="ad9d8-196">WS-Addressing Faults</span></span>

<span data-ttu-id="ad9d8-197">因為 ws-reliablemessaging 使用 WS-ADDRESSING，所以 WCF ws-reliablemessaging 執行可能會產生並傳輸 WS-ADDRESSING 錯誤。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-197">Because WS-ReliableMessaging uses WS-Addressing, the WCF WS-ReliableMessaging implementation may generate and transmit WS-Addressing faults.</span></span> <span data-ttu-id="ad9d8-198">本節涵蓋 WCF 在 ws-reliablemessaging 層明確產生和傳輸的 WS-ADDRESSING 錯誤：</span><span class="sxs-lookup"><span data-stu-id="ad9d8-198">This section covers the WS-Addressing faults that WCF explicitly generates and transmits at the WS-ReliableMessaging layer:</span></span>

- <span data-ttu-id="ad9d8-199">B1801：當下列其中一項為真時，WCF 會產生並傳輸 `Message Addressing Header Required` 錯誤：</span><span class="sxs-lookup"><span data-stu-id="ad9d8-199">B1801:WCF generates and transmits the `Message Addressing Header Required` fault when one of the following is true:</span></span>

  - <span data-ttu-id="ad9d8-200">`CreateSequence`、`CloseSequence` 或 `TerminateSequence` 訊息缺少 `MessageId` 標頭。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-200">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `MessageId` header.</span></span>

  - <span data-ttu-id="ad9d8-201">`CreateSequence`、`CloseSequence` 或 `TerminateSequence` 訊息缺少 `ReplyTo` 標頭。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-201">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `ReplyTo` header.</span></span>

  - <span data-ttu-id="ad9d8-202">`CreateSequenceResponse`、`CloseSequenceResponse` 或 `TerminateSequenceResponse` 訊息缺少 `RelatesTo` 標頭。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-202">A `CreateSequenceResponse`, `CloseSequenceResponse`, or `TerminateSequenceResponse` message is missing a `RelatesTo` header.</span></span>

- <span data-ttu-id="ad9d8-203">B1802： WCF 會產生並傳輸 `Endpoint Unavailable` 錯誤，指出沒有任何接聽的端點可以根據 `CreateSequence` 訊息中的定址標頭檢查來處理序列。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-203">B1802:WCF generates and transmits the `Endpoint Unavailable` fault to indicate there is no endpoint listening that can process the sequence based on examination of the addressing headers in the `CreateSequence` message.</span></span>

## <a name="protocol-composition"></a><span data-ttu-id="ad9d8-204">通訊協定組合</span><span class="sxs-lookup"><span data-stu-id="ad9d8-204">Protocol Composition</span></span>

### <a name="composition-with-ws-addressing"></a><span data-ttu-id="ad9d8-205">與 WS-Addressing 組合</span><span class="sxs-lookup"><span data-stu-id="ad9d8-205">Composition with WS-Addressing</span></span>

<span data-ttu-id="ad9d8-206">WCF 支援兩種 WS-ADDRESSING 版本： WS-ADDRESSING 2004/08 [WS-ATOMICTRANSACTION] 和 W3C WS-ADDRESSING 1.0 建議 [WS-ADDRESSING-CORE] 和 [WS-ATOMICTRANSACTION-SOAP]。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-206">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>

<span data-ttu-id="ad9d8-207">儘管 WS-ReliableMessaging 規格只提到 WS-Addressing 2004/08，它並未限制要使用的 WS-Addressing 版本。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-207">While the WS-ReliableMessaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="ad9d8-208">以下是適用于 WCF 的條件約束清單：</span><span class="sxs-lookup"><span data-stu-id="ad9d8-208">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="ad9d8-209">R2101：WS-Addressing 2004/08 和 WS-Addressing 1.0 皆可搭配 WS-Reliable 訊息一起使用。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-209">R2101: Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>

- <span data-ttu-id="ad9d8-210">R2102：單一版本的 WS-Addressing 必須透過 `Offer` 機制，用在整個特定的 WS-ReliableMessaging 序列或是一對相關聯的反向序列上。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-210">R2102: A single version of WS-Addressing must be used throughout a given WS-ReliableMessaging sequence or a pair of converse sequences correlated by using the `Offer` mechanism.</span></span>

### <a name="composition-with-soap"></a><span data-ttu-id="ad9d8-211">與 SOAP 組合</span><span class="sxs-lookup"><span data-stu-id="ad9d8-211">Composition with SOAP</span></span>

<span data-ttu-id="ad9d8-212">WCF 支援搭配使用 SOAP 1.1 和 SOAP 1.2 與 WS-可靠的訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-212">WCF supports the use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>

### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="ad9d8-213">與 WS-Security 和 WS-SecureConversation 組合</span><span class="sxs-lookup"><span data-stu-id="ad9d8-213">Composition with WS-Security and WS-SecureConversation</span></span>

<span data-ttu-id="ad9d8-214">WCF 藉由使用安全傳輸（HTTPS）、以 WS-MANAGEMENT 撰寫，以及與 WS-安全交談組合，來提供 WS-RELIABLEMESSAGING 序列的保護。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-214">WCF provides protection for WS-ReliableMessaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="ad9d8-215">WS-ReliableMessaging 1.1 通訊協定、WS-Security 1.1 和 WS-Secure Conversation 1.3 通訊協定應該一併使用。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-215">The WS-ReliableMessaging 1.1 protocol, WS-Security 1.1 and WS-Secure Conversation 1.3 protocol should be used together.</span></span> <span data-ttu-id="ad9d8-216">以下是適用于 WCF 的條件約束清單：</span><span class="sxs-lookup"><span data-stu-id="ad9d8-216">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="ad9d8-217">R2301：若要保護 ws-reliablemessaging 序列的完整性，以及個別訊息的完整性和機密性，WCF 需要使用 WS-安全交談。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-217">R2301: To protect the integrity of a WS-ReliableMessaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>

- <span data-ttu-id="ad9d8-218">R2302：在建立 WS-ReliableMessaging 序列之前，必須先建立 WS-Secure Conversation 工作階段。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-218">R2302:AWS-Secure Conversation session must be established prior to establishing WS-ReliableMessaging sequence(s).</span></span>

- <span data-ttu-id="ad9d8-219">R2303：如果 WS-ReliableMessaging 序列的存留期超過 WS-Secure Conversation 工作階段的存留期，則使用 WS-Secure Conversation 建立的 `SecurityContextToken` 必須透過對應的 WS-Secure Conversation 更新繫結來加以更新。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-219">R2303: If the WS-ReliableMessaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>

- <span data-ttu-id="ad9d8-220">B2304：WS-ReliableMessaging 序列或是一對相互關聯的反向序列一律繫結至單一 WS-SecureConversation 工作階段。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-220">B2304:WS-ReliableMessaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>

- <span data-ttu-id="ad9d8-221">R2305：當以 WS-安全對話撰寫時，WCF 回應者會要求 `CreateSequence` 訊息包含 `wsse:SecurityTokenReference` 元素和 `wsrm:UsesSequenceSTR` 標頭。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-221">R2305: When composed with WS-Secure Conversation, the WCF responder requires that the `CreateSequence` message contain the `wsse:SecurityTokenReference` element and the `wsrm:UsesSequenceSTR` header.</span></span>

 <span data-ttu-id="ad9d8-222">`UsesSequenceSTR` 標頭的範例。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-222">An example of a `UsesSequenceSTR` header.</span></span>

```xml
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>
```

### <a name="composition-with-ssltls-sessions"></a><span data-ttu-id="ad9d8-223">與 SSL/TLS 組合</span><span class="sxs-lookup"><span data-stu-id="ad9d8-223">Composition with SSL/TLS sessions</span></span>

<span data-ttu-id="ad9d8-224">WCF 不支援使用 SSL/TLS 會話撰寫：</span><span class="sxs-lookup"><span data-stu-id="ad9d8-224">WCF does not support composition with SSL/TLS sessions:</span></span>

- <span data-ttu-id="ad9d8-225">B2401： WCF 不會產生 `wsrm:UsesSequenceSSL` 標頭。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-225">B2401: WCF does not generate the `wsrm:UsesSequenceSSL` header.</span></span>

- <span data-ttu-id="ad9d8-226">R2402：可靠的訊息啟動器不得將具有 `wsrm:UsesSequenceSSL` 標頭的 `CreateSequence` 訊息傳送至 WCF 回應程式。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-226">R2402: A Reliable Messaging Initiator must not send a `CreateSequence` message with a `wsrm:UsesSequenceSSL` header to a WCF Responder.</span></span>

### <a name="composition-with-ws-policy"></a><span data-ttu-id="ad9d8-227">與 WS-Policy 組合</span><span class="sxs-lookup"><span data-stu-id="ad9d8-227">Composition with WS-Policy</span></span>

<span data-ttu-id="ad9d8-228">WCF 支援兩種版本的 WS 原則： WS-Policy 1.2 和 WS-Policy 1.5。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-228">WCF supports two versions of WS-Policy: WS-Policy 1.2 and WS-Policy 1.5.</span></span>

## <a name="ws-reliablemessaging-ws-policy-assertion"></a><span data-ttu-id="ad9d8-229">WS-ReliableMessaging WS-Policy 判斷提示</span><span class="sxs-lookup"><span data-stu-id="ad9d8-229">WS-ReliableMessaging WS-Policy Assertion</span></span>

<span data-ttu-id="ad9d8-230">WCF 使用 WS-RELIABLEMESSAGING WS-原則判斷提示 `wsrm:RMAssertion` 來描述端點功能。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-230">WCF uses WS-ReliableMessaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="ad9d8-231">以下是適用于 WCF 的條件約束清單：</span><span class="sxs-lookup"><span data-stu-id="ad9d8-231">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="ad9d8-232">B3001： WCF 會將 `wsrmn:RMAssertion` WS-原則判斷提示附加至 `wsdl:binding` 元素。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-232">B3001: WCF attaches `wsrmn:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="ad9d8-233">WCF 同時支援 `wsdl:binding` 和 `wsdl:port` 元素的附件。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-233">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>

- <span data-ttu-id="ad9d8-234">B3002： WCF 絕不會產生 `wsp:Optional` 標記。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-234">B3002: WCF never generates the `wsp:Optional` tag.</span></span>

- <span data-ttu-id="ad9d8-235">B3003：存取 `wsrmp:RMAssertion` WS-原則判斷提示時，WCF 會忽略 `wsp:Optional` 標記，並將 WS-RM 原則視為強制。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-235">B3003: When accessing the `wsrmp:RMAssertion` WS-Policy Assertion, WCF ignores the `wsp:Optional` tag and treats the WS-RM policy as mandatory.</span></span>

- <span data-ttu-id="ad9d8-236">R3004：因為 WCF 不是以 SSL/TLS 會話撰寫，所以 WCF 不接受指定 `wsrmp:SequenceTransportSecurity`的原則。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-236">R3004: Because WCF does not compose with SSL/TLS sessions, WCF does not accept policy that specifies `wsrmp:SequenceTransportSecurity`.</span></span>

- <span data-ttu-id="ad9d8-237">B3005： WCF 一律會產生 `wsrmp:DeliveryAssurance` 元素。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-237">B3005: WCF always generates the `wsrmp:DeliveryAssurance` element.</span></span>

- <span data-ttu-id="ad9d8-238">B3006： WCF 一律會指定 `wsrmp:ExactlyOnce` 傳遞保證。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-238">B3006: WCF always specifies the `wsrmp:ExactlyOnce` delivery assurance.</span></span>

- <span data-ttu-id="ad9d8-239">B3007： WCF 會產生並讀取 WS-RELIABLEMESSAGING 判斷提示的下列屬性，並在 WCF`ReliableSessionBindingElement`上提供其控制：</span><span class="sxs-lookup"><span data-stu-id="ad9d8-239">B3007: WCF generates and reads the following properties of the WS-ReliableMessaging assertion and provides control over them on the WCF`ReliableSessionBindingElement`:</span></span>

  - `netrmp:InactivityTimeout`

  - `netrmp:AcknowledgementInterval`

  <span data-ttu-id="ad9d8-240">`RMAssertion` 的範例。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-240">An example of a `RMAssertion`.</span></span>

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

## <a name="flow-control-ws-reliablemessaging-extension"></a><span data-ttu-id="ad9d8-241">WS-ReliableMessaging 延伸的流量控制</span><span class="sxs-lookup"><span data-stu-id="ad9d8-241">Flow Control WS-ReliableMessaging Extension</span></span>

<span data-ttu-id="ad9d8-242">WCF 使用 WS-RELIABLEMESSAGING 擴充性，對序列訊息流程提供選擇性的額外更緊密的控制。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-242">WCF uses WS-ReliableMessaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>

<span data-ttu-id="ad9d8-243">藉由將 [<xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType>] 屬性設定為 [`true`]，即可啟用流量控制。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-243">Flow control is enabled by setting the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="ad9d8-244">以下是適用于 WCF 的條件約束清單：</span><span class="sxs-lookup"><span data-stu-id="ad9d8-244">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="ad9d8-245">B4001 一旦：當可靠的訊息流量控制啟用時，WCF 會在 `SequenceAcknowledgement` 標頭的專案擴充性中產生 `netrm:BufferRemaining` 元素，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-245">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header, as shown in the following example.</span></span>

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="1" Lower="1"/>
    <netrm:BufferRemaining>8</netrm:BufferRemaining>
  </wsrm:SequenceAcknowledgement>
  ```

- <span data-ttu-id="ad9d8-246">B4002：即使啟用可靠的訊息流程式控制制，WCF 也不需要 `SequenceAcknowledgement` 標頭中的 `netrm:BufferRemaining` 元素。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-246">B4002: Even when Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element in the `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="ad9d8-247">B4003： WCF 可靠的訊息目的地會使用 `netrm:BufferRemaining` 來指示它可以緩衝處理的新訊息數目。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-247">B4003: WCF Reliable Messaging Destination uses `netrm:BufferRemaining` to indicate how many new messages it can buffer.</span></span>

- <span data-ttu-id="ad9d8-248">B4004：當可靠的訊息流量控制啟用時，WCF 可靠的訊息來源會使用 `netrm:BufferRemaining` 的值來節流訊息傳輸。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-248">B4004:When Reliable Messaging Flow Control is enabled, the WCF Reliable Messaging Source uses the value of `netrm:BufferRemaining` to throttle message transmission.</span></span>

- <span data-ttu-id="ad9d8-249">B4005： WCF 會 `netrm:BufferRemaining` 產生介於0到4096（含）之間的整數值，並讀取介於0和 `xs:int`的 `maxInclusive` 值214748364（含）之間的整數值。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-249">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>

## <a name="message-exchange-patterns"></a><span data-ttu-id="ad9d8-250">訊息交換模式</span><span class="sxs-lookup"><span data-stu-id="ad9d8-250">Message Exchange Patterns</span></span>

<span data-ttu-id="ad9d8-251">本節說明在不同的訊息交換模式使用 WS-RELIABLEMESSAGING 時，WCF 的行為。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-251">This section describes WCF's behavior when WS-ReliableMessaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="ad9d8-252">在每個訊息交換模式中，會考慮下列兩種部署案例：</span><span class="sxs-lookup"><span data-stu-id="ad9d8-252">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>

- <span data-ttu-id="ad9d8-253">不可定址的啟動器：啟動器位於防火牆後方，回應程式只能透過 HTTP 回應將訊息傳送至啟動器。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-253">Non-Addressable Initiator: Initiator is behind a firewall; Responder can deliver messages to the Initiator only on HTTP responses.</span></span>

- <span data-ttu-id="ad9d8-254">可定址的啟動器：可將 HTTP 要求同時傳送給啟動器與回應程式，亦即可建立兩個反向 HTTP 連線。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-254">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>

### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="ad9d8-255">單向、不可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="ad9d8-255">One-way, Non-addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="ad9d8-256">繫結</span><span class="sxs-lookup"><span data-stu-id="ad9d8-256">Binding</span></span>

<span data-ttu-id="ad9d8-257">WCF 會在一個 HTTP 通道上使用一個序列來提供單向的訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-257">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="ad9d8-258">WCF 使用 HTTP 要求將所有訊息從啟動器傳送至回應程式，而 HTTP 回應則將所有訊息從回應傳送至啟動器。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-258">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="ad9d8-259">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="ad9d8-259">CreateSequence Exchange</span></span>

<span data-ttu-id="ad9d8-260">WCF 啟動器會在 HTTP 要求上傳輸沒有 `Offer` 元素的 `CreateSequence` 訊息，並預期 HTTP 回應上的 `CreateSequenceResponse` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-260">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="ad9d8-261">WCF 回應程式會建立序列，並在 HTTP 回應上傳輸沒有 `Accept` 元素的 `CreateSequenceResponse` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-261">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on the HTTP response.</span></span>

#### <a name="sequenceacknowledgement"></a><span data-ttu-id="ad9d8-262">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="ad9d8-262">SequenceAcknowledgement</span></span>

<span data-ttu-id="ad9d8-263">除了 `CreateSequence` 訊息和錯誤訊息以外，WCF 啟動器會處理所有訊息的回復通知。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-263">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="ad9d8-264">WCF 回應者一律會將 HTTP 回應上的獨立認可傳送至所有序列和 `AckRequested` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-264">The WCF Responder always transmits a stand-alone acknowledgement on the HTTP response to all sequence and `AckRequested` messages.</span></span>

#### <a name="closesequence-exchange"></a><span data-ttu-id="ad9d8-265">CloseSequence 交換</span><span class="sxs-lookup"><span data-stu-id="ad9d8-265">CloseSequence Exchange</span></span>

<span data-ttu-id="ad9d8-266">WCF 啟動器會在 HTTP 要求上傳輸 `CloseSequence` 訊息，並在 HTTP 回應上預期 `CreateSequenceResponse` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-266">The WCF Initiator transmits a `CloseSequence` message on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="ad9d8-267">WCF 回應程式會傳送 HTTP 回應上的 `CloseSequenceResponse` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-267">The WCF Responder transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="ad9d8-268">TerminateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="ad9d8-268">TerminateSequence Exchange</span></span>

<span data-ttu-id="ad9d8-269">WCF 啟動器會在 HTTP 要求上傳輸 `TerminateSequence` 訊息，並在 HTTP 回應上預期 `TerminateSequenceResponse` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-269">The WCF Initiator transmits a `TerminateSequence` message on an HTTP request and expects the `TerminateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="ad9d8-270">WCF 回應程式會傳送 HTTP 回應上的 `TerminateSequenceResponse` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-270">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>

### <a name="one-way-addressable-initiator"></a><span data-ttu-id="ad9d8-271">單向、可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="ad9d8-271">One Way, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="ad9d8-272">繫結</span><span class="sxs-lookup"><span data-stu-id="ad9d8-272">Binding</span></span>

<span data-ttu-id="ad9d8-273">WCF 會在一個輸入和一個傳出 HTTP 通道上使用一個序列來提供單向訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-273">WCF provides a one-way message exchange pattern using one sequence over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="ad9d8-274">WCF 會使用 HTTP 要求來傳送所有訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-274">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="ad9d8-275">所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-275">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="ad9d8-276">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="ad9d8-276">CreateSequence Exchange</span></span>

<span data-ttu-id="ad9d8-277">WCF 啟動器會在 HTTP 要求上傳輸沒有 `Offer` 元素的 `CreateSequence` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-277">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request.</span></span> <span data-ttu-id="ad9d8-278">WCF 回應程式會建立序列，並在 HTTP 要求上傳輸沒有 `Accept` 元素的 `CreateSequenceResponse` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-278">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on an HTTP request.</span></span>

### <a name="duplex-addressable-initiator"></a><span data-ttu-id="ad9d8-279">雙工、可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="ad9d8-279">Duplex, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="ad9d8-280">繫結</span><span class="sxs-lookup"><span data-stu-id="ad9d8-280">Binding</span></span>

<span data-ttu-id="ad9d8-281">WCF 會在一個輸入和一個傳出 HTTP 通道上使用兩個序列，以提供完全非同步、雙向的訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-281">WCF provides a fully-asynchronous, two-way message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="ad9d8-282">在有限的情況下，此訊息交換模式可與 `Request/Reply`、`Addressable` 啟動器訊息交換模式混合使用。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-282">This message exchange pattern can be mixed with the `Request/Reply`, `Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="ad9d8-283">WCF 會使用 HTTP 要求來傳送所有訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-283">WCF uses HTTP requests to transmit all messages.</span></span> <span data-ttu-id="ad9d8-284">所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-284">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="ad9d8-285">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="ad9d8-285">CreateSequence Exchange</span></span>

<span data-ttu-id="ad9d8-286">WCF 啟動器會使用 HTTP 要求上的 `Offer` 元素來傳輸 `CreateSequence` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-286">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="ad9d8-287">WCF 回應程式可確保 `CreateSequence` 具有 `Offer` 元素，然後建立序列，並使用 `Accept` 專案來傳輸 `CreateSequenceResponse` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-287">The WCF Responder ensures that the `CreateSequence` has an `Offer` element, then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>

#### <a name="sequence-lifetime"></a><span data-ttu-id="ad9d8-288">序列存留期</span><span class="sxs-lookup"><span data-stu-id="ad9d8-288">Sequence Lifetime</span></span>

<span data-ttu-id="ad9d8-289">WCF 會將這兩個序列視為一個全雙工會話。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-289">WCF treats the two sequences as one fully-duplex session.</span></span>

<span data-ttu-id="ad9d8-290">在產生錯誤一個序列的錯誤時，WCF 會預期遠端端點會同時容錯這兩個序列。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-290">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="ad9d8-291">當讀取錯誤發生一系列的錯誤時，WCF 會同時錯誤這兩個序列。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-291">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>

<span data-ttu-id="ad9d8-292">WCF 可以關閉其輸出序列，並繼續處理其輸入序列的訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-292">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="ad9d8-293">相反地，WCF 可以處理輸入序列的關閉，並繼續以輸出序列來傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-293">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>

### <a name="request-reply-and-one-way-non-addressable-initiator"></a><span data-ttu-id="ad9d8-294">要求-回覆和單向、不可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="ad9d8-294">Request-Reply and One-Way, Non-Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="ad9d8-295">繫結</span><span class="sxs-lookup"><span data-stu-id="ad9d8-295">Binding</span></span>

<span data-ttu-id="ad9d8-296">WCF 透過在一個 HTTP 通道上使用兩個序列的方式，提供單向和要求-回復訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-296">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="ad9d8-297">WCF 使用 HTTP 要求將所有訊息從啟動器傳送至回應程式，而 HTTP 回應則將所有訊息從回應傳送至啟動器。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-297">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="ad9d8-298">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="ad9d8-298">CreateSequence Exchange</span></span>

<span data-ttu-id="ad9d8-299">WCF 啟動器會使用 HTTP 要求上的 `Offer` 元素來傳輸 `CreateSequence` 訊息，並預期 HTTP 回應上會有 `CreateSequenceResponse` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-299">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="ad9d8-300">WCF 回應程式會建立序列，並使用 HTTP 回應上的 `Accept` 元素來傳輸 `CreateSequenceResponse` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-300">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element on the HTTP response.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="ad9d8-301">單向訊息</span><span class="sxs-lookup"><span data-stu-id="ad9d8-301">One-way Message</span></span>

<span data-ttu-id="ad9d8-302">為了成功完成單向訊息交換，WCF 啟動器會透過 HTTP 要求傳送要求序列訊息，並在 HTTP 回應上接收獨立的 `SequenceAcknowledgement` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-302">To complete a one-way message exchange successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="ad9d8-303">`SequenceAcknowledgement` 必須認可傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-303">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>

<span data-ttu-id="ad9d8-304">WCF 回應者可以使用通知、錯誤或具有空白本文和 HTTP 202 狀態碼的回應來回複要求。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-304">The WCF Responder may reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>

#### <a name="two-way-messages"></a><span data-ttu-id="ad9d8-305">雙向訊息</span><span class="sxs-lookup"><span data-stu-id="ad9d8-305">Two Way Messages</span></span>

<span data-ttu-id="ad9d8-306">為了成功完成雙向訊息交換通訊協定，WCF 啟動器會在 HTTP 要求上傳輸要求序列訊息，並在 HTTP 回應上接收回複序列訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-306">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="ad9d8-307">回應中必須包含認可傳輸之要求序列訊息的 `SequenceAcknowledgement`。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-307">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>

<span data-ttu-id="ad9d8-308">WCF 回應者可以透過應用程式回復、錯誤或具有空白本文的回應，以及 HTTP 202 狀態碼來回複要求。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-308">The WCF Responder may reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>

<span data-ttu-id="ad9d8-309">由於單向訊息與應用程式回覆時機的緣故，要求序列訊息的序號與回應訊息的序號彼此並未互相關聯。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-309">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>

#### <a name="retrying-replies"></a><span data-ttu-id="ad9d8-310">重試回覆</span><span class="sxs-lookup"><span data-stu-id="ad9d8-310">Retrying Replies</span></span>

<span data-ttu-id="ad9d8-311">WCF 依賴雙向訊息交換通訊協定相互關聯的 HTTP 要求-回復相互關聯。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-311">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="ad9d8-312">因此，WCF 啟動器不會在認可要求序列訊息時停止重試要求序列訊息，而是在 HTTP 回應攜帶 `SequenceAcknowledgement`、應用程式回復或錯誤時發生。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-312">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries a `SequenceAcknowledgement`, application reply, or fault.</span></span> <span data-ttu-id="ad9d8-313">WCF 回應程式會在與回復相互關聯之要求的 HTTP 回應上重試回復。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-313">The WCF Responder retries replies on the HTTP response of the request to which the reply is correlated.</span></span>

#### <a name="closesequence-exchange"></a><span data-ttu-id="ad9d8-314">CloseSequence 交換</span><span class="sxs-lookup"><span data-stu-id="ad9d8-314">CloseSequence Exchange</span></span>

<span data-ttu-id="ad9d8-315">收到所有單向要求順序訊息的所有回復順序訊息和通知之後，WCF 啟動器會針對 HTTP 要求傳送要求序列的 `CloseSequence` 訊息，並預期 HTTP 回應上的 `CloseSequenceResponse`。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-315">After receiving all reply sequence messages and acknowledgements for all one way request sequence messages, the WCF Initiator transmits a `CloseSequence` message for the request sequence on an HTTP request and expects the `CloseSequenceResponse` on the HTTP response.</span></span>

<span data-ttu-id="ad9d8-316">隱含地關閉要求序列會一併關閉回覆序列。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-316">Closing the request sequence implicitly closes the reply sequence.</span></span> <span data-ttu-id="ad9d8-317">這表示 WCF 啟動器會在 `CloseSequence` 訊息上包含回復序列的最終 `SequenceAcknowledgement`，而回復順序則不會有 `CloseSequence` 交換。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-317">This means the WCF Initiator includes the reply sequence’s Final `SequenceAcknowledgement` on the `CloseSequence` message and the reply sequence does not have a `CloseSequence` exchange.</span></span>

<span data-ttu-id="ad9d8-318">WCF 回應程式可確保所有回復都已認可，並在 HTTP 回應上傳輸 `CloseSequenceResponse` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-318">The WCF Responder ensures all replies are acknowledged and transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="ad9d8-319">TerminateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="ad9d8-319">TerminateSequence Exchange</span></span>

<span data-ttu-id="ad9d8-320">收到 `CloseSequenceResponse` 訊息之後，WCF 啟動器會針對 HTTP 要求傳送要求序列的 `TerminateSequence` 訊息，並預期 HTTP 回應中的 `TerminateSequenceResponse`。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-320">After receiving the `CloseSequenceResponse` message, the WCF Initiator transmits a `TerminateSequence` message for the request sequence on an HTTP request and expects the `TerminateSequenceResponse` on the HTTP response.</span></span>

<span data-ttu-id="ad9d8-321">就像 `CloseSequence` 交換一樣，終止要求序列會隱含地終止回覆序列。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-321">Like the `CloseSequence` exchange, terminating the request sequence implicitly terminates the reply sequence.</span></span> <span data-ttu-id="ad9d8-322">這表示 WCF 啟動器會在 `TerminateSequence` 訊息上包含回復序列的最終 `SequenceAcknowledgement`，而回復順序則不會有 `TerminateSequence` 交換。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-322">This means the WCF Initiator includes the reply sequence’s final `SequenceAcknowledgement` on the `TerminateSequence` message and the reply sequence does not have a `TerminateSequence` exchange.</span></span>

<span data-ttu-id="ad9d8-323">WCF 回應程式會傳送 HTTP 回應上的 `TerminateSequenceResponse` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-323">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>

### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="ad9d8-324">要求/回覆、可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="ad9d8-324">Request/Reply, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="ad9d8-325">繫結</span><span class="sxs-lookup"><span data-stu-id="ad9d8-325">Binding</span></span>

<span data-ttu-id="ad9d8-326">WCF 會在一個輸入和一個傳出 HTTP 通道上使用兩個序列，以提供要求-回復訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-326">WCF provides a request-reply message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="ad9d8-327">在有限的情況下，此訊息交換模式可與 `Duplex, Addressable` 啟動器訊息交換模式混合使用。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-327">This message exchange pattern can be mixed with the `Duplex, Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="ad9d8-328">WCF 會使用 HTTP 要求來傳送所有訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-328">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="ad9d8-329">所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-329">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="ad9d8-330">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="ad9d8-330">CreateSequence Exchange</span></span>

<span data-ttu-id="ad9d8-331">WCF 啟動器會使用 HTTP 要求上的 `Offer` 元素來傳輸 `CreateSequence` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-331">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="ad9d8-332">WCF 回應程式可確保 `CreateSequence` 具有 `Offer` 元素，然後建立序列，並使用 `Accept` 專案來傳輸 `CreateSequenceResponse` 訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-332">The WCF Responder ensures that the `CreateSequence` has an `Offer` element then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>

#### <a name="requestreply-correlation"></a><span data-ttu-id="ad9d8-333">要求/回覆相互關聯</span><span class="sxs-lookup"><span data-stu-id="ad9d8-333">Request/Reply Correlation</span></span>

<span data-ttu-id="ad9d8-334">下列會套用到所有相互關聯的要求及回覆：</span><span class="sxs-lookup"><span data-stu-id="ad9d8-334">The following applies to all correlated requests and replies:</span></span>

- <span data-ttu-id="ad9d8-335">WCF 可確保所有應用程式要求訊息都有 `ReplyTo` 端點參考和 `MessageId`。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-335">WCF ensures all application request messages bear a `ReplyTo` endpoint reference and a `MessageId`.</span></span>

- <span data-ttu-id="ad9d8-336">當每個應用程式要求訊息的 `ReplyTo`時，WCF 會套用本機端點參考。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-336">WCF applies the local endpoint reference as each application request message’s `ReplyTo`.</span></span> <span data-ttu-id="ad9d8-337">啟動器的本機端點參照是 `CreateSequence` 訊息的 `ReplyTo`，而回應程式的本機端點參照則是 `CreateSequence` 訊息的 `To`。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-337">The local endpoint reference is the `CreateSequence` message’s `ReplyTo` for the Initiator and the `CreateSequence` message’s `To` for the Responder.</span></span>

- <span data-ttu-id="ad9d8-338">WCF 可確保傳入的要求訊息會擲出 `MessageId` 和 `ReplyTo`。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-338">WCF ensures that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span>

- <span data-ttu-id="ad9d8-339">WCF 可確保所有應用程式要求訊息的 `ReplyTo` 端點參考 URI 符合先前所定義的本機端點參考。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-339">WCF ensures the `ReplyTo` endpoint reference’s URI of all application request messages match the local endpoint reference as defined earlier.</span></span>

- <span data-ttu-id="ad9d8-340">WCF 可確保所有回復都具有正確的 `RelatesTo`，並遵循 `wsa` 要求/回復相互關聯規則的 `To` 標頭。</span><span class="sxs-lookup"><span data-stu-id="ad9d8-340">WCF ensures that all replies bear the correct `RelatesTo` and `To` headers following `wsa` request/reply correlation rules.</span></span>

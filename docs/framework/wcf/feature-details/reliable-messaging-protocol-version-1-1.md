---
title: Reliable Messaging Protocol 1.1 版
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: 6b8732e0b48797c219b53bb8bf70e1ba57e25c42
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933987"
---
# <a name="reliable-messaging-protocol-version-11"></a><span data-ttu-id="dacbe-102">Reliable Messaging Protocol 1.1 版</span><span class="sxs-lookup"><span data-stu-id="dacbe-102">Reliable Messaging Protocol version 1.1</span></span>
<span data-ttu-id="dacbe-103">本主題涵蓋 Windows Communication Foundation (WCF) 實作細節的 WS-ReliableMessaging February 2007 （1.1 版） 通訊協定所需的互通性，使用 HTTP 傳輸。</span><span class="sxs-lookup"><span data-stu-id="dacbe-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-ReliableMessaging February 2007 (version 1.1) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="dacbe-104">WCF 會遵循條件約束和釐清這個主題所述 WS-ReliableMessaging 規格。</span><span class="sxs-lookup"><span data-stu-id="dacbe-104">WCF follows the WS-ReliableMessaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="dacbe-105">請注意開始實作 WS-ReliableMessaging 1.1 版通訊協定[!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="dacbe-105">Note that the WS-ReliableMessaging version 1.1 protocol is implemented starting with the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].</span></span>  
  
 <span data-ttu-id="dacbe-106">WS-ReliableMessaging February 2007 通訊協定的實作中的 WCF <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="dacbe-106">The WS-ReliableMessaging February 2007 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>  
  
 <span data-ttu-id="dacbe-107">為了方便起見，本主題將使用下列角色：</span><span class="sxs-lookup"><span data-stu-id="dacbe-107">For convenience, the topic uses the following roles:</span></span>  
  
-   <span data-ttu-id="dacbe-108">啟動者：啟動 Ws-reliable 訊息序列建立用戶端。</span><span class="sxs-lookup"><span data-stu-id="dacbe-108">Initiator: The client that initiates WS-Reliable Message sequence creation.</span></span>  
  
-   <span data-ttu-id="dacbe-109">回應程式：接收啟動器要求的服務。</span><span class="sxs-lookup"><span data-stu-id="dacbe-109">Responder: The service that receives the initiator's requests.</span></span>  
  
 <span data-ttu-id="dacbe-110">本文件會使用下表的前置詞和命名空間。</span><span class="sxs-lookup"><span data-stu-id="dacbe-110">This document uses the prefixes and namespaces in the following table.</span></span>  
  
|<span data-ttu-id="dacbe-111">前置詞</span><span class="sxs-lookup"><span data-stu-id="dacbe-111">Prefix</span></span>|<span data-ttu-id="dacbe-112">命名空間</span><span class="sxs-lookup"><span data-stu-id="dacbe-112">Namespace</span></span>|  
|-|-|  
|<span data-ttu-id="dacbe-113">wsrm</span><span class="sxs-lookup"><span data-stu-id="dacbe-113">wsrm</span></span>|http://docs.oasis-open.org/ws-rx/wsrm/200702|  
|<span data-ttu-id="dacbe-114">netrm</span><span class="sxs-lookup"><span data-stu-id="dacbe-114">netrm</span></span>|http://schemas.microsoft.com/ws/2006/05/rm|  
|<span data-ttu-id="dacbe-115">秒</span><span class="sxs-lookup"><span data-stu-id="dacbe-115">s</span></span>|http://www.w3.org/2003/05/soap-envelope|  
|<span data-ttu-id="dacbe-116">wsa</span><span class="sxs-lookup"><span data-stu-id="dacbe-116">wsa</span></span>|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|<span data-ttu-id="dacbe-117">wsse</span><span class="sxs-lookup"><span data-stu-id="dacbe-117">wsse</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
|<span data-ttu-id="dacbe-118">wsrmp</span><span class="sxs-lookup"><span data-stu-id="dacbe-118">wsrmp</span></span>|http://docs.oasis-open.org/ws-rx/wsrmp/200702|  
|<span data-ttu-id="dacbe-119">netrmp</span><span class="sxs-lookup"><span data-stu-id="dacbe-119">netrmp</span></span>|http://schemas.microsoft.com/ws-rx/wsrmp/200702|  
|<span data-ttu-id="dacbe-120">wsp</span><span class="sxs-lookup"><span data-stu-id="dacbe-120">wsp</span></span>|<span data-ttu-id="dacbe-121">(WS-Policy 1.2 或 WS-Policy 1.5)</span><span class="sxs-lookup"><span data-stu-id="dacbe-121">(Either WS-Policy 1.2 or WS-Policy 1.5)</span></span>|  
  
## <a name="messaging"></a><span data-ttu-id="dacbe-122">訊息</span><span class="sxs-lookup"><span data-stu-id="dacbe-122">Messaging</span></span>  
  
### <a name="sequence-creation"></a><span data-ttu-id="dacbe-123">建立序列</span><span class="sxs-lookup"><span data-stu-id="dacbe-123">Sequence Creation</span></span>  
 <span data-ttu-id="dacbe-124">WCF 實作`CreateSequence`和`CreateSequenceResponse`訊息以建立可信賴傳訊序列。</span><span class="sxs-lookup"><span data-stu-id="dacbe-124">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable messaging sequence.</span></span> <span data-ttu-id="dacbe-125">以下是適用的條件約束：</span><span class="sxs-lookup"><span data-stu-id="dacbe-125">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="dacbe-126">B1101:WCF 啟動者會使用相同的端點參照一樣`CreateSequence`訊息的`ReplyTo`，`AcksTo`和`Offer/Endpoint`。</span><span class="sxs-lookup"><span data-stu-id="dacbe-126">B1101: The WCF Initiator uses the same endpoint reference as the `CreateSequence` message’s `ReplyTo`, `AcksTo` and `Offer/Endpoint`.</span></span>  
  
-   <span data-ttu-id="dacbe-127">R1102:`AcksTo`，`ReplyTo`並`Offer/Endpoint`端點參考`CreateSequence`訊息必須使用相同的字串表示法的位址值，使它們符合八位元規格。</span><span class="sxs-lookup"><span data-stu-id="dacbe-127">R1102: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message must have address values with identical string representations such that they match the octet-wise.</span></span>  
  
    -   <span data-ttu-id="dacbe-128">WCF 回應程式會驗證的 URI 部分`AcksTo`，`ReplyTo`和`Endpoint`端點參考建立序列之前完全相同。</span><span class="sxs-lookup"><span data-stu-id="dacbe-128">The WCF Responder verifies that the URI portion of the `AcksTo`, `ReplyTo` and `Endpoint` endpoint references are identical before creating a sequence.</span></span>  
  
-   <span data-ttu-id="dacbe-129">R1103:`AcksTo`，`ReplyTo`並`Offer/Endpoint`端點參考`CreateSequence`訊息應該有相同的參照參數集合。</span><span class="sxs-lookup"><span data-stu-id="dacbe-129">R1103: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message should have the same set of reference parameters.</span></span>  
  
    -   <span data-ttu-id="dacbe-130">WCF 不會強制執行，但會假設該參考的參數`AcksTo`，`ReplyTo`並`Offer/Endpoint`端點會參考上`CreateSequence`完全相同，並使用參考參數，從`ReplyTo`端點參考認可並與序列訊息對話。</span><span class="sxs-lookup"><span data-stu-id="dacbe-130">WCF does not enforce, but assumes that reference parameters of the `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references on `CreateSequence` are identical and uses reference parameters from the `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>  
  
-   <span data-ttu-id="dacbe-131">B1104:WCF 啟動器不會產生選用`Expires`或是`Offer/Expires`中的項目`CreateSequence`訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-131">B1104: The WCF Initiator does not generate the optional `Expires` or `Offer/Expires` element in the `CreateSequence` message.</span></span>  
  
-   <span data-ttu-id="dacbe-132">B1105:存取時`CreateSequence`訊息，WCF 回應程式會使用`Expires`中的值`CreateSequence`項目做為`Expires`中的值`CreateSequenceResponse`項目。</span><span class="sxs-lookup"><span data-stu-id="dacbe-132">B1105: When accessing the `CreateSequence` message, the WCF Responder uses the `Expires` value in the `CreateSequence` element as the `Expires` value in the `CreateSequenceResponse` element.</span></span> <span data-ttu-id="dacbe-133">否則，WCF 回應讀取，並忽略`Expires`和`Offer/Expires`值。</span><span class="sxs-lookup"><span data-stu-id="dacbe-133">Otherwise, the WCF Responder reads and ignores the `Expires` and `Offer/Expires` values.</span></span>  
  
-   <span data-ttu-id="dacbe-134">B1106:存取時`CreateSequenceResponse`訊息，WCF 啟動器會讀取選用`Expires`值，但不會使用它。</span><span class="sxs-lookup"><span data-stu-id="dacbe-134">B1106: When accessing the `CreateSequenceResponse` message, the WCF Initiator reads the optional `Expires` value but does not use it.</span></span>  
  
-   <span data-ttu-id="dacbe-135">B1107:WCF 啟動器和回應程式一律會產生選用`IncompleteSequenceBehavior`中的項目`CreateSequence/Offer`和`CreateSequenceResponse`項目。</span><span class="sxs-lookup"><span data-stu-id="dacbe-135">B1107: The WCF Initiator and Responder always generate the optional `IncompleteSequenceBehavior` element in the `CreateSequence/Offer` and `CreateSequenceResponse` elements.</span></span>  
  
-   <span data-ttu-id="dacbe-136">B1108:只會使用 WCF`DiscardFollowingFirstGap`並`NoDiscard`中的值`IncompleteSequenceBehavior`項目。</span><span class="sxs-lookup"><span data-stu-id="dacbe-136">B1108: WCF uses only the `DiscardFollowingFirstGap` and `NoDiscard` values in the `IncompleteSequenceBehavior` element.</span></span>  
  
    -   <span data-ttu-id="dacbe-137">WS-ReliableMessaging 會使用 `Offer` 機制來建立兩個反向關聯序列以形成工作階段。</span><span class="sxs-lookup"><span data-stu-id="dacbe-137">WS-ReliableMessaging utilizes the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>  
  
-   <span data-ttu-id="dacbe-138">B1109:如果`CreateSequence`包含`Offer`項目，其中一種方式的 WCF 回應程式拒絕提供的序列來回應以`CreateSequenceResponse`而不需要`Accept`項目。</span><span class="sxs-lookup"><span data-stu-id="dacbe-138">B1109: If `CreateSequence` contains an `Offer` element, the one way WCF Responder rejects the offered sequence by responding with a `CreateSequenceResponse` without an `Accept` element.</span></span>  
  
-   <span data-ttu-id="dacbe-139">B1110:如果使用可靠的傳訊回應程式會拒絕提供的序列，WCF 啟動器錯誤新建立的序列。</span><span class="sxs-lookup"><span data-stu-id="dacbe-139">B1110: If a Reliable Messaging Responder rejects the offered sequence, the WCF Initiator faults the newly established sequence.</span></span>  
  
-   <span data-ttu-id="dacbe-140">B1111:如果`CreateSequence`neobsahuje`Offer`項目，雙向 WCF 回應程式拒絕提供的序列來回應以`CreateSequenceRefused`錯誤。</span><span class="sxs-lookup"><span data-stu-id="dacbe-140">B1111: If `CreateSequence` does not contain an `Offer` element, the two-way WCF Responder rejects the offered sequence by responding with a `CreateSequenceRefused` fault.</span></span>  
  
-   <span data-ttu-id="dacbe-141">R1112:建立兩個反向序列的使用時`Offer`機制`[address]`屬性`CreateSequenceResponse/Accept/AcksTo`端點參考必須符合目的地 URI 的`CreateSequence`位元組的訊息位元組。</span><span class="sxs-lookup"><span data-stu-id="dacbe-141">R1112: When two converse sequences are established using the `Offer` mechanism, the `[address]` property of the `CreateSequenceResponse/Accept/AcksTo` endpoint reference must match the destination URI of the `CreateSequence` message byte for byte.</span></span>  
  
-   <span data-ttu-id="dacbe-142">R1113:建立兩個反向序列的使用時`Offer`機制，從啟動器流向回應程式的兩個序列上的所有訊息必須都傳送至相同的端點參考。</span><span class="sxs-lookup"><span data-stu-id="dacbe-142">R1113: When two converse sequences are established using the `Offer` mechanism, all messages on both sequences flowing from the Initiator to the Responder must be sent to the same endpoint reference.</span></span>  
  
 <span data-ttu-id="dacbe-143">WCF 會建立啟動器和回應程式之間的可靠工作階段使用 WS-ReliableMessaging。</span><span class="sxs-lookup"><span data-stu-id="dacbe-143">WCF uses WS-ReliableMessaging to establish reliable sessions between the Initiator and the Responder.</span></span> <span data-ttu-id="dacbe-144">WCF WS-ReliableMessaging 實作提供可靠的工作階段，針對單向、 要求-回覆與全雙工訊息模式。</span><span class="sxs-lookup"><span data-stu-id="dacbe-144">The WCF WS-ReliableMessaging implementation provides a reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="dacbe-145">`Offer` 和 `CreateSequence` 上的 WS-ReliableMessaging `CreateSequenceResponse` 機制可讓您建立兩個相互關聯的反向序列，並提供適用於所有訊息端點的工作階段通訊協定。</span><span class="sxs-lookup"><span data-stu-id="dacbe-145">The WS-ReliableMessaging `Offer` mechanism on `CreateSequence` and `CreateSequenceResponse` lets you establish two correlated converse sequences and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="dacbe-146">WCF 會提供包含的工作階段完整性的端對端保護這類的工作階段的安全性保證，因此它會實際地確保適用於相同的合作對象的訊息抵達相同的目的地。</span><span class="sxs-lookup"><span data-stu-id="dacbe-146">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure that messages intended for the same party arrive at the same destination.</span></span> <span data-ttu-id="dacbe-147">這麼做也可以針對應用程式訊息進行 "piggy-backing" 的序列認可作業。</span><span class="sxs-lookup"><span data-stu-id="dacbe-147">This also allows "piggy-backing" of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="dacbe-148">因此，R1102、 R1112，以及 R1113 條件約束套用至 WCF。</span><span class="sxs-lookup"><span data-stu-id="dacbe-148">Therefore, constraints R1102, R1112, and R1113 apply to WCF.</span></span>  
  
 <span data-ttu-id="dacbe-149">`CreateSequence` 訊息的範例。</span><span class="sxs-lookup"><span data-stu-id="dacbe-149">An example of a `CreateSequence` message.</span></span>  
  
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
  
 <span data-ttu-id="dacbe-150">`CreateSequenceResponse` 訊息的範例。</span><span class="sxs-lookup"><span data-stu-id="dacbe-150">An example of a `CreateSequenceResponse` message.</span></span>  
  
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
  
### <a name="closing-a-sequence"></a><span data-ttu-id="dacbe-151">關閉序列</span><span class="sxs-lookup"><span data-stu-id="dacbe-151">Closing a Sequence</span></span>  
 <span data-ttu-id="dacbe-152">WCF 會使用`CloseSequence`和`CloseSequenceResponse`的可信賴傳訊來源起始關閉訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-152">WCF uses the `CloseSequence` and `CloseSequenceResponse` messages for a Reliable Messaging source-initiated shutdown.</span></span> <span data-ttu-id="dacbe-153">WCF 可信賴傳訊目的地不會起始關機，WCF 可信賴傳訊來源不支援可信賴傳訊目的地啟始關閉。</span><span class="sxs-lookup"><span data-stu-id="dacbe-153">The WCF Reliable Messaging destination does not initiate shutdown and the WCF Reliable Messaging source does not support a Reliable Messaging destination-initiated shutdown.</span></span> <span data-ttu-id="dacbe-154">以下是適用的條件約束：</span><span class="sxs-lookup"><span data-stu-id="dacbe-154">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="dacbe-155">B1201:WCF 可信賴傳訊來源一律傳送`CloseSequence`關閉序列的訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-155">B1201: The WCF Reliable Messaging source always sends a `CloseSequence` message to shut down the sequence.</span></span>  
  
-   <span data-ttu-id="dacbe-156">B1202:可信賴傳訊來源會等到序列訊息的完整認可再傳送`CloseSequence`訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-156">B1202: The Reliable Messaging source waits for acknowledgement of the full range of sequence messages before sending the `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="dacbe-157">B1203:可信賴傳訊來源一律包含選用`LastMsgNumber`項目除非序列不包含訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-157">B1203: The Reliable Messaging source always includes the optional `LastMsgNumber` element unless the sequence does not contain messages.</span></span>  
  
-   <span data-ttu-id="dacbe-158">R1204:可信賴傳訊目的地必須藉由傳送啟始關閉`CloseSequence`訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-158">R1204: The Reliable Messaging destination must not initiate shutdown by sending a `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="dacbe-159">B1205:在收到`CloseSequence`訊息，WCF 可信賴傳訊來源會將序列視為不完整並傳送錯誤。</span><span class="sxs-lookup"><span data-stu-id="dacbe-159">B1205: Upon receiving a `CloseSequence` message, the WCF Reliable Messaging source considers the sequence incomplete and sends a fault.</span></span>  
  
 <span data-ttu-id="dacbe-160">`CloseSequence` 訊息的範例。</span><span class="sxs-lookup"><span data-stu-id="dacbe-160">An example of a `CloseSequence` message.</span></span>  
  
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
  
### <a name="sequence-termination"></a><span data-ttu-id="dacbe-161">終止序列</span><span class="sxs-lookup"><span data-stu-id="dacbe-161">Sequence Termination</span></span>  
 <span data-ttu-id="dacbe-162">WCF 主要是透過`TerminateSequence/TerminateSequenceResponse`交握完成後的`CloseSequence/CloseSequenceResponse`交握。</span><span class="sxs-lookup"><span data-stu-id="dacbe-162">WCF primarily uses the `TerminateSequence/TerminateSequenceResponse` handshake after completing the `CloseSequence/CloseSequenceResponse` handshake.</span></span> <span data-ttu-id="dacbe-163">WCF 可信賴傳訊目的地不會啟始終止和可信賴傳訊來源不支援可信賴傳訊目的地起始終止。</span><span class="sxs-lookup"><span data-stu-id="dacbe-163">The WCF Reliable Messaging destination does not initiate termination and the Reliable Messaging source does not support a Reliable Messaging destination-initiated termination.</span></span> <span data-ttu-id="dacbe-164">以下是適用的條件約束：</span><span class="sxs-lookup"><span data-stu-id="dacbe-164">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="dacbe-165">B1301:WCF 啟動器只會傳送`TerminateSequence`成功完成後的訊息`CloseSequence/CloseSequenceResponse`交握。</span><span class="sxs-lookup"><span data-stu-id="dacbe-165">B1301: The WCF Initiator only sends the `TerminateSequence` message after the successful completion of the `CloseSequence/CloseSequenceResponse` handshake.</span></span>  
  
-   <span data-ttu-id="dacbe-166">R1302:WCF 驗證`LastMsgNumber`所有項目是否一致`CloseSequence`和`TerminateSequence`針對特定序列的訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-166">R1302: WCF validates that the `LastMsgNumber` element is consistent across all `CloseSequence` and `TerminateSequence` messages for a given sequence.</span></span> <span data-ttu-id="dacbe-167">也就是說，`LastMsgNumber` 不是不存在於所有 `CloseSequence` 和 `TerminateSequence` 訊息上，就是存在於所有 `CloseSequence` 和 `TerminateSequence` 訊息上而且全部一樣。</span><span class="sxs-lookup"><span data-stu-id="dacbe-167">This means that `LastMsgNumber` is either not present on all `CloseSequence` and `TerminateSequence` messages, or it is present and identical on all `CloseSequence` and `TerminateSequence` messages.</span></span>  
  
-   <span data-ttu-id="dacbe-168">B1303:當接收`TerminateSequence`訊息之後`CloseSequence/CloseSequenceResponse`交握，以回應的可信賴傳訊目的地`TerminateSequenceResponse`訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-168">B1303: When receiving a `TerminateSequence` message after the `CloseSequence/CloseSequenceResponse` handshake, the Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="dacbe-169">由於可信賴傳訊來源在傳送 `TerminateSequence` 訊息之前已經獲得最後的認可，因此可信賴傳訊目的地毫無疑問地知道序列已結束並立即回收資源。</span><span class="sxs-lookup"><span data-stu-id="dacbe-169">Because the Reliable Messaging source has the final acknowledgement before sending the `TerminateSequence` message, the Reliable Messaging destination knows without doubt that the sequence ends, and reclaims resources immediately.</span></span>  
  
-   <span data-ttu-id="dacbe-170">B1304:當接收`TerminateSequence`訊息之前`CloseSequence/CloseSequenceResponse`交握，WCF 可信賴傳訊目的地會以回應`TerminateSequenceResponse`訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-170">B1304: When receiving a `TerminateSequence` message prior to the `CloseSequence/CloseSequenceResponse` handshake, the WCF Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="dacbe-171">如果可信賴傳訊目的地判斷序列中沒有任何不一致的項目，則可信賴傳訊目的地會等候應用程式目的地指定的時間一到再回收資源，以便讓用戶端有機會接收最後的認可。</span><span class="sxs-lookup"><span data-stu-id="dacbe-171">If the Reliable Messaging destination determines that there are no inconsistencies in the sequence, the Reliable Messaging destination waits for an application destination-specified time before reclaiming resources, to allow the client the chance to receive the final acknowledgement.</span></span> <span data-ttu-id="dacbe-172">否則，可信賴傳訊目的地會立即回收資源並引發 `Faulted` 事件以向應用程式目的地指出序列是在不確定的情況下結束。</span><span class="sxs-lookup"><span data-stu-id="dacbe-172">Otherwise, the Reliable Messaging destination reclaims resources immediately and indicates to the application destination that the sequence ends with doubt by raising the `Faulted` event.</span></span>  
  
 <span data-ttu-id="dacbe-173">`TerminateSequence` 訊息的範例。</span><span class="sxs-lookup"><span data-stu-id="dacbe-173">An example of a `TerminateSequence` message.</span></span>  
  
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
  
### <a name="sequences"></a><span data-ttu-id="dacbe-174">序列</span><span class="sxs-lookup"><span data-stu-id="dacbe-174">Sequences</span></span>  
 <span data-ttu-id="dacbe-175">下列清單列出適用於序列的條件約束：</span><span class="sxs-lookup"><span data-stu-id="dacbe-175">The following is a list of constraints that apply to sequences:</span></span>  
  
-   <span data-ttu-id="dacbe-176">B1401:WCF 會產生，並存取序號不高於`xs:long`的最大包含值，9223372036854775807。</span><span class="sxs-lookup"><span data-stu-id="dacbe-176">B1401:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>  
  
 <span data-ttu-id="dacbe-177">`Sequence` 標頭的範例。</span><span class="sxs-lookup"><span data-stu-id="dacbe-177">An example of a `Sequence` header.</span></span>  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a><span data-ttu-id="dacbe-178">要求認可</span><span class="sxs-lookup"><span data-stu-id="dacbe-178">Request Acknowledgement</span></span>  
 <span data-ttu-id="dacbe-179">WCF 會使用`AckRequested`標頭做為 keep-alive 機制。</span><span class="sxs-lookup"><span data-stu-id="dacbe-179">WCF uses the `AckRequested` header as a keep-alive mechanism.</span></span>  
  
 <span data-ttu-id="dacbe-180">`AckRequested` 標頭的範例。</span><span class="sxs-lookup"><span data-stu-id="dacbe-180">An example of an `AckRequested` header.</span></span>  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a><span data-ttu-id="dacbe-181">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="dacbe-181">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="dacbe-182">WCF 所提供的 Ws-reliable 訊息的序列認可使用"piggy-back 機操作 」 機制。</span><span class="sxs-lookup"><span data-stu-id="dacbe-182">WCF uses a "piggy-back" mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span> <span data-ttu-id="dacbe-183">以下是適用的條件約束：</span><span class="sxs-lookup"><span data-stu-id="dacbe-183">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="dacbe-184">R1601:當使用建立兩個反向序列`Offer`機制，`SequenceAcknowledgement`標頭可能包含在傳送到預定的收件者的任何應用程式訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-184">R1601: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span> <span data-ttu-id="dacbe-185">遠端端點必須能夠存取以 Piggyback 方式傳送的 `SequenceAcknowledgement` 標頭。</span><span class="sxs-lookup"><span data-stu-id="dacbe-185">The remote endpoint must be able to access a piggybacked `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="dacbe-186">B1602:WCF 不會產生`SequenceAcknowledgement`包含的標頭`Nack`項目。</span><span class="sxs-lookup"><span data-stu-id="dacbe-186">B1602: WCF does not generate `SequenceAcknowledgement` headers that contain `Nack` elements.</span></span> <span data-ttu-id="dacbe-187">WCF 驗證每個`Nack`項目包含序號，但是另一方面會忽略`Nack`元素和值。</span><span class="sxs-lookup"><span data-stu-id="dacbe-187">WCF validates that each `Nack` element contains a sequence number, but otherwise ignores the `Nack` element and value.</span></span>  
  
 <span data-ttu-id="dacbe-188">`SequenceAcknowledgement` 標頭的範例。</span><span class="sxs-lookup"><span data-stu-id="dacbe-188">An example of a `SequenceAcknowledgement` header.</span></span>  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="dacbe-189">WS-ReliableMessaging 錯誤</span><span class="sxs-lookup"><span data-stu-id="dacbe-189">WS-ReliableMessaging Faults</span></span>  
 <span data-ttu-id="dacbe-190">以下是適用於 WS-ReliableMessaging 錯誤 WCF 實作的條件約束的清單。</span><span class="sxs-lookup"><span data-stu-id="dacbe-190">The following is a list of constraints that apply to the WCF implementation of WS-ReliableMessaging faults.</span></span> <span data-ttu-id="dacbe-191">以下是適用的條件約束：</span><span class="sxs-lookup"><span data-stu-id="dacbe-191">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="dacbe-192">B1701:WCF 不會產生`MessageNumberRollover`錯誤。</span><span class="sxs-lookup"><span data-stu-id="dacbe-192">B1701: WCF does not generate `MessageNumberRollover` faults.</span></span>  
  
-   <span data-ttu-id="dacbe-193">B1702:在 SOAP 1.2 中，當服務端點到達其連線限制，而且無法處理新的連線，WCF 會產生巢狀`CreateSequenceRefused`錯誤子代碼， `netrm:ConnectionLimitReached`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="dacbe-193">B1702: Over SOAP 1.2, when the service endpoint reaches its connection limit and cannot process new connections, WCF generates a nested `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>  
  
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
  
### <a name="ws-addressing-faults"></a><span data-ttu-id="dacbe-194">WS-Addressing 錯誤</span><span class="sxs-lookup"><span data-stu-id="dacbe-194">WS-Addressing Faults</span></span>  
 <span data-ttu-id="dacbe-195">由於 WS-ReliableMessaging 是使用 Ws-addressing，WCF WS-ReliableMessaging 實作可能會產生並傳送 Ws-addressing 錯誤。</span><span class="sxs-lookup"><span data-stu-id="dacbe-195">Because WS-ReliableMessaging uses WS-Addressing, the WCF WS-ReliableMessaging implementation may generate and transmit WS-Addressing faults.</span></span> <span data-ttu-id="dacbe-196">此章節將涵蓋 WCF 明確地產生，並在 WS-ReliableMessaging 層傳送 Ws-addressing 錯誤：</span><span class="sxs-lookup"><span data-stu-id="dacbe-196">This section covers the WS-Addressing faults that WCF explicitly generates and transmits at the WS-ReliableMessaging layer:</span></span>  
  
-   <span data-ttu-id="dacbe-197">B1801:WCF 會產生並傳送`Message Addressing Header Required`當下列其中一項條件成立時，發生錯誤：</span><span class="sxs-lookup"><span data-stu-id="dacbe-197">B1801:WCF generates and transmits the `Message Addressing Header Required` fault when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="dacbe-198">`CreateSequence`、`CloseSequence` 或 `TerminateSequence` 訊息缺少 `MessageId` 標頭。</span><span class="sxs-lookup"><span data-stu-id="dacbe-198">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `MessageId` header.</span></span>  
  
    -   <span data-ttu-id="dacbe-199">`CreateSequence`、`CloseSequence` 或 `TerminateSequence` 訊息缺少 `ReplyTo` 標頭。</span><span class="sxs-lookup"><span data-stu-id="dacbe-199">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `ReplyTo` header.</span></span>  
  
    -   <span data-ttu-id="dacbe-200">`CreateSequenceResponse`、`CloseSequenceResponse` 或 `TerminateSequenceResponse` 訊息缺少 `RelatesTo` 標頭。</span><span class="sxs-lookup"><span data-stu-id="dacbe-200">A `CreateSequenceResponse`, `CloseSequenceResponse`, or `TerminateSequenceResponse` message is missing a `RelatesTo` header.</span></span>  
  
-   <span data-ttu-id="dacbe-201">B1802:WCF 會產生並傳送`Endpoint Unavailable`錯誤以指出沒有任何接聽的端點來處理序列中的定址標頭的檢查為基礎`CreateSequence`訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-201">B1802:WCF generates and transmits the `Endpoint Unavailable` fault to indicate there is no endpoint listening that can process the sequence based on examination of the addressing headers in the `CreateSequence` message.</span></span>  
  
## <a name="protocol-composition"></a><span data-ttu-id="dacbe-202">通訊協定組合</span><span class="sxs-lookup"><span data-stu-id="dacbe-202">Protocol Composition</span></span>  
  
### <a name="composition-with-ws-addressing"></a><span data-ttu-id="dacbe-203">與 WS-Addressing 組合</span><span class="sxs-lookup"><span data-stu-id="dacbe-203">Composition with WS-Addressing</span></span>  
 <span data-ttu-id="dacbe-204">WCF 支援兩個 Ws-addressing 版本：Ws-addressing 2004/08 [WS-ADDR] 和 W3C Ws-addressing 1.0 建議 [WS-ADDR-核心] 和 [WS-ADDR-SOAP]。</span><span class="sxs-lookup"><span data-stu-id="dacbe-204">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>  
  
 <span data-ttu-id="dacbe-205">儘管 WS-ReliableMessaging 規格只提到 WS-Addressing 2004/08，它並未限制要使用的 WS-Addressing 版本。</span><span class="sxs-lookup"><span data-stu-id="dacbe-205">While the WS-ReliableMessaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="dacbe-206">以下是適用於 WCF 的條件約束的清單：</span><span class="sxs-lookup"><span data-stu-id="dacbe-206">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="dacbe-207">R2101:Ws-addressing 2004/08 和 Ws-addressing 1.0 可搭配 Ws-reliable 訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-207">R2101: Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="dacbe-208">R2102:單一版本的 Ws-addressing 必須使用在整個指定的 WS-ReliableMessaging 序列或是一對使用相互關聯的反向序列`Offer`機制。</span><span class="sxs-lookup"><span data-stu-id="dacbe-208">R2102: A single version of WS-Addressing must be used throughout a given WS-ReliableMessaging sequence or a pair of converse sequences correlated by using the `Offer` mechanism.</span></span>  
  
### <a name="composition-with-soap"></a><span data-ttu-id="dacbe-209">與 SOAP 組合</span><span class="sxs-lookup"><span data-stu-id="dacbe-209">Composition with SOAP</span></span>  
 <span data-ttu-id="dacbe-210">WCF 支援 SOAP 1.1 和 SOAP 1.2 搭配 Ws-reliable 訊息一起使用。</span><span class="sxs-lookup"><span data-stu-id="dacbe-210">WCF supports the use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="dacbe-211">與 WS-Security 和 WS-SecureConversation 組合</span><span class="sxs-lookup"><span data-stu-id="dacbe-211">Composition with WS-Security and WS-SecureConversation</span></span>  
 <span data-ttu-id="dacbe-212">WCF 會提供 WS-ReliableMessaging 序列 (sequence) 的保護，透過安全傳輸 (HTTPS)、 與 Ws-security 組合且組合與 Ws-secure Conversation。</span><span class="sxs-lookup"><span data-stu-id="dacbe-212">WCF provides protection for WS-ReliableMessaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="dacbe-213">WS-ReliableMessaging 1.1 通訊協定、WS-Security 1.1 和 WS-Secure Conversation 1.3 通訊協定應該一併使用。</span><span class="sxs-lookup"><span data-stu-id="dacbe-213">The WS-ReliableMessaging 1.1 protocol, WS-Security 1.1 and WS-Secure Conversation 1.3 protocol should be used together.</span></span> <span data-ttu-id="dacbe-214">以下是適用於 WCF 的條件約束的清單：</span><span class="sxs-lookup"><span data-stu-id="dacbe-214">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="dacbe-215">R2301:若要保護的個別訊息完整性除了 WS-ReliableMessaging 序列的完整性與機密性，WCF 會要求必須使用 Ws-secure Conversation。</span><span class="sxs-lookup"><span data-stu-id="dacbe-215">R2301: To protect the integrity of a WS-ReliableMessaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>  
  
-   <span data-ttu-id="dacbe-216">R2302:AWS-在建立 WS-ReliableMessaging 序列之前，必須建立安全對話工作階段。</span><span class="sxs-lookup"><span data-stu-id="dacbe-216">R2302:AWS-Secure Conversation session must be established prior to establishing WS-ReliableMessaging sequence(s).</span></span>  
  
-   <span data-ttu-id="dacbe-217">R2303:如果 WS-ReliableMessaging 序列存留期超過 Ws-secure Conversation 工作階段的存留期，`SecurityContextToken`藉由使用 Ws-secure Conversation 必須更新使用對應的 Ws-secure Conversation 更新繫結。</span><span class="sxs-lookup"><span data-stu-id="dacbe-217">R2303: If the WS-ReliableMessaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>  
  
-   <span data-ttu-id="dacbe-218">B2304:WS-Ws-reliablemessaging 序列或是一對相互關聯的反向序列一律繫結至單一 Ws-secureconversation 工作階段。</span><span class="sxs-lookup"><span data-stu-id="dacbe-218">B2304:WS-ReliableMessaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>  
  
-   <span data-ttu-id="dacbe-219">R2305:WCF 回應需要組合之後便構成與 Ws-secure Conversation`CreateSequence`訊息包含`wsse:SecurityTokenReference`項目和`wsrm:UsesSequenceSTR`標頭。</span><span class="sxs-lookup"><span data-stu-id="dacbe-219">R2305: When composed with WS-Secure Conversation, the WCF responder requires that the `CreateSequence` message contain the `wsse:SecurityTokenReference` element and the `wsrm:UsesSequenceSTR` header.</span></span>  
  
 <span data-ttu-id="dacbe-220">`UsesSequenceSTR` 標頭的範例。</span><span class="sxs-lookup"><span data-stu-id="dacbe-220">An example of a `UsesSequenceSTR` header.</span></span>  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a><span data-ttu-id="dacbe-221">與 SSL/TLS 組合</span><span class="sxs-lookup"><span data-stu-id="dacbe-221">Composition with SSL/TLS sessions</span></span>  
 <span data-ttu-id="dacbe-222">WCF 不支援使用 SSL/TLS 工作階段的組合：</span><span class="sxs-lookup"><span data-stu-id="dacbe-222">WCF does not support composition with SSL/TLS sessions:</span></span>  
  
-   <span data-ttu-id="dacbe-223">B2401:WCF 不會產生`wsrm:UsesSequenceSSL`標頭。</span><span class="sxs-lookup"><span data-stu-id="dacbe-223">B2401: WCF does not generate the `wsrm:UsesSequenceSSL` header.</span></span>  
  
-   <span data-ttu-id="dacbe-224">R2402:可信賴傳訊啟動器必須傳送`CreateSequence`訊息，其`wsrm:UsesSequenceSSL`WCF 回應標頭。</span><span class="sxs-lookup"><span data-stu-id="dacbe-224">R2402: A Reliable Messaging Initiator must not send a `CreateSequence` message with a `wsrm:UsesSequenceSSL` header to a WCF Responder.</span></span>  
  
### <a name="composition-with-ws-policy"></a><span data-ttu-id="dacbe-225">與 WS-Policy 組合</span><span class="sxs-lookup"><span data-stu-id="dacbe-225">Composition with WS-Policy</span></span>  
 <span data-ttu-id="dacbe-226">WCF 支援 Ws-policy 的兩種的版本：Ws-policy 1.2 和 Ws-policy 1.5。</span><span class="sxs-lookup"><span data-stu-id="dacbe-226">WCF supports two versions of WS-Policy: WS-Policy 1.2 and WS-Policy 1.5.</span></span>  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a><span data-ttu-id="dacbe-227">WS-ReliableMessaging WS-Policy 判斷提示</span><span class="sxs-lookup"><span data-stu-id="dacbe-227">WS-ReliableMessaging WS-Policy Assertion</span></span>  
 <span data-ttu-id="dacbe-228">WCF 使用了 WS-ReliableMessaging Ws-policy 判斷提示`wsrm:RMAssertion`來描述端點的功能。</span><span class="sxs-lookup"><span data-stu-id="dacbe-228">WCF uses WS-ReliableMessaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="dacbe-229">以下是適用於 WCF 的條件約束的清單：</span><span class="sxs-lookup"><span data-stu-id="dacbe-229">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="dacbe-230">B3001:WCF 會附加`wsrmn:RMAssertion`Ws-policy 判斷提示至`wsdl:binding`項目。</span><span class="sxs-lookup"><span data-stu-id="dacbe-230">B3001: WCF attaches `wsrmn:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="dacbe-231">WCF 支援這兩個附件`wsdl:binding`和`wsdl:port`項目。</span><span class="sxs-lookup"><span data-stu-id="dacbe-231">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>  
  
-   <span data-ttu-id="dacbe-232">B3002:永遠不會產生 WCF`wsp:Optional`標記。</span><span class="sxs-lookup"><span data-stu-id="dacbe-232">B3002: WCF never generates the `wsp:Optional` tag.</span></span>  
  
-   <span data-ttu-id="dacbe-233">B3003:存取時`wsrmp:RMAssertion`Ws-policy 判斷提示，WCF 會忽略`wsp:Optional`標記，並將 WS-RM 原則視為強制性。</span><span class="sxs-lookup"><span data-stu-id="dacbe-233">B3003: When accessing the `wsrmp:RMAssertion` WS-Policy Assertion, WCF ignores the `wsp:Optional` tag and treats the WS-RM policy as mandatory.</span></span>  
  
-   <span data-ttu-id="dacbe-234">R3004:因為 WCF 無法組成與 SSL/TLS 工作階段，WCF 不接受指定的原則`wsrmp:SequenceTransportSecurity`。</span><span class="sxs-lookup"><span data-stu-id="dacbe-234">R3004: Because WCF does not compose with SSL/TLS sessions, WCF does not accept policy that specifies `wsrmp:SequenceTransportSecurity`.</span></span>  
  
-   <span data-ttu-id="dacbe-235">B3005:WCF 一律會產生`wsrmp:DeliveryAssurance`項目。</span><span class="sxs-lookup"><span data-stu-id="dacbe-235">B3005: WCF always generates the `wsrmp:DeliveryAssurance` element.</span></span>  
  
-   <span data-ttu-id="dacbe-236">B3006:WCF 一律指定`wsrmp:ExactlyOnce`傳遞保證。</span><span class="sxs-lookup"><span data-stu-id="dacbe-236">B3006: WCF always specifies the `wsrmp:ExactlyOnce` delivery assurance.</span></span>  
  
-   <span data-ttu-id="dacbe-237">B3007:WCF 會產生並讀取下列 WS-ReliableMessaging 判斷提示的屬性，並針對它們提供控制的 WCF`ReliableSessionBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="dacbe-237">B3007: WCF generates and reads the following properties of the WS-ReliableMessaging assertion and provides control over them on the WCF`ReliableSessionBindingElement`:</span></span>  
  
    -   `netrmp:InactivityTimeout`  
  
    -   `netrmp:AcknowledgementInterval`  
  
     <span data-ttu-id="dacbe-238">`RMAssertion` 的範例。</span><span class="sxs-lookup"><span data-stu-id="dacbe-238">An example of a `RMAssertion`.</span></span>  
  
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
  
## <a name="flow-control-ws-reliablemessaging-extension"></a><span data-ttu-id="dacbe-239">WS-ReliableMessaging 延伸的流量控制</span><span class="sxs-lookup"><span data-stu-id="dacbe-239">Flow Control WS-ReliableMessaging Extension</span></span>  
 <span data-ttu-id="dacbe-240">WCF 會使用 WS-ReliableMessaging 擴充性，提供選擇性的額外更緊密地控制序列訊息流量。</span><span class="sxs-lookup"><span data-stu-id="dacbe-240">WCF uses WS-ReliableMessaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>  
  
 <span data-ttu-id="dacbe-241">藉由設定已啟用流量控制<xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="dacbe-241">Flow control is enabled by setting the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="dacbe-242">以下是適用於 WCF 的條件約束的清單：</span><span class="sxs-lookup"><span data-stu-id="dacbe-242">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="dacbe-243">B4001:WCF 啟用信賴傳訊流量控制時，會產生`netrm:BufferRemaining`中的項目擴充性項目`SequenceAcknowledgement`標頭，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="dacbe-243">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="dacbe-244">B4002:即使信賴傳訊流量控制已啟用，WCF 不需要`netrm:BufferRemaining`中的項目`SequenceAcknowledgement`標頭。</span><span class="sxs-lookup"><span data-stu-id="dacbe-244">B4002: Even when Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element in the `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="dacbe-245">B4003:WCF 可靠傳訊目的地會使用`netrm:BufferRemaining`緩衝來指出多少新訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-245">B4003: WCF Reliable Messaging Destination uses `netrm:BufferRemaining` to indicate how many new messages it can buffer.</span></span>  
  
-   <span data-ttu-id="dacbe-246">已啟用 B4004:When 信賴傳訊流量控制，WCF 可靠傳訊來源會使用值`netrm:BufferRemaining`來調節訊息傳輸。</span><span class="sxs-lookup"><span data-stu-id="dacbe-246">B4004:When Reliable Messaging Flow Control is enabled, the WCF Reliable Messaging Source uses the value of `netrm:BufferRemaining` to throttle message transmission.</span></span>  
  
-   <span data-ttu-id="dacbe-247">B4005:WCF 會產生`netrm:BufferRemaining`整數值介於 0 到 4096 （含)，並讀取介於 0 的整數值與`xs:int`的`maxInclusive`值 214748364 （含)。</span><span class="sxs-lookup"><span data-stu-id="dacbe-247">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>  
  
## <a name="message-exchange-patterns"></a><span data-ttu-id="dacbe-248">訊息交換模式</span><span class="sxs-lookup"><span data-stu-id="dacbe-248">Message Exchange Patterns</span></span>  
 <span data-ttu-id="dacbe-249">當不同訊息交換模式使用 WS-ReliableMessaging 時，本節會說明 WCF 的行為。</span><span class="sxs-lookup"><span data-stu-id="dacbe-249">This section describes WCF's behavior when WS-ReliableMessaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="dacbe-250">在每個訊息交換模式中，會考慮下列兩種部署案例：</span><span class="sxs-lookup"><span data-stu-id="dacbe-250">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>  
  
-   <span data-ttu-id="dacbe-251">不可定址的啟動器：啟動器位於防火牆;回應程式將訊息傳送至起始端，只能在 HTTP 回應上。</span><span class="sxs-lookup"><span data-stu-id="dacbe-251">Non-Addressable Initiator: Initiator is behind a firewall; Responder can deliver messages to the Initiator only on HTTP responses.</span></span>  
  
-   <span data-ttu-id="dacbe-252">可定址的啟動器：啟動器和回應程式可傳送 HTTP 要求;換句話說，您可以建立兩個反向 HTTP 連線。</span><span class="sxs-lookup"><span data-stu-id="dacbe-252">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>  
  
### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="dacbe-253">單向、不可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="dacbe-253">One-way, Non-addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="dacbe-254">繫結</span><span class="sxs-lookup"><span data-stu-id="dacbe-254">Binding</span></span>  
 <span data-ttu-id="dacbe-255">WCF 會提供一個 HTTP 通道上使用一個序列的單向訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="dacbe-255">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="dacbe-256">WCF 會使用 HTTP 要求來傳送所有訊息從啟動器至回應程式並透過 HTTP 回應來都傳送所有訊息從回應者至啟動器。</span><span class="sxs-lookup"><span data-stu-id="dacbe-256">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="dacbe-257">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="dacbe-257">CreateSequence Exchange</span></span>  
 <span data-ttu-id="dacbe-258">WCF 啟動者傳送出去`CreateSequence`含訊息`Offer`HTTP 要求的項目，並預期`CreateSequenceResponse`HTTP 回應的訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-258">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="dacbe-259">WCF 回應程式會建立序列，並將傳送`CreateSequenceResponse`含訊息`Accept`HTTP 回應上的項目。</span><span class="sxs-lookup"><span data-stu-id="dacbe-259">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on the HTTP response.</span></span>  
  
#### <a name="sequenceacknowledgement"></a><span data-ttu-id="dacbe-260">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="dacbe-260">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="dacbe-261">WCF 啟動器處理以外的所有訊息的認可回覆`CreateSequence`訊息與錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-261">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="dacbe-262">WCF 回應程式一律會傳輸至所有序列的 HTTP 回應將獨立認可和`AckRequested`訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-262">The WCF Responder always transmits a stand-alone acknowledgement on the HTTP response to all sequence and `AckRequested` messages.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="dacbe-263">CloseSequence 交換</span><span class="sxs-lookup"><span data-stu-id="dacbe-263">CloseSequence Exchange</span></span>  
 <span data-ttu-id="dacbe-264">WCF 啟動者傳送出去`CloseSequence`HTTP 要求訊息，並預期`CreateSequenceResponse`HTTP 回應的訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-264">The WCF Initiator transmits a `CloseSequence` message on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="dacbe-265">WCF 回應傳輸`CloseSequenceResponse`HTTP 回應的訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-265">The WCF Responder transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="dacbe-266">TerminateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="dacbe-266">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="dacbe-267">WCF 啟動者傳送出去`TerminateSequence`HTTP 要求訊息，並預期`TerminateSequenceResponse`HTTP 回應的訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-267">The WCF Initiator transmits a `TerminateSequence` message on an HTTP request and expects the `TerminateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="dacbe-268">WCF 回應傳輸`TerminateSequenceResponse`HTTP 回應的訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-268">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="one-way-addressable-initiator"></a><span data-ttu-id="dacbe-269">單向、可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="dacbe-269">One Way, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="dacbe-270">繫結</span><span class="sxs-lookup"><span data-stu-id="dacbe-270">Binding</span></span>  
 <span data-ttu-id="dacbe-271">WCF 提供單向的訊息交換模式使用一個序列的放在一個傳入與一個傳出 HTTP 通道。</span><span class="sxs-lookup"><span data-stu-id="dacbe-271">WCF provides a one-way message exchange pattern using one sequence over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="dacbe-272">WCF 會使用 HTTP 要求來傳送所有訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-272">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="dacbe-273">所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="dacbe-273">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="dacbe-274">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="dacbe-274">CreateSequence Exchange</span></span>  
 <span data-ttu-id="dacbe-275">WCF 啟動者傳送出去`CreateSequence`含訊息`Offer`HTTP 要求的項目。</span><span class="sxs-lookup"><span data-stu-id="dacbe-275">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request.</span></span> <span data-ttu-id="dacbe-276">WCF 回應程式會建立序列，並將傳送`CreateSequenceResponse`含訊息`Accept`HTTP 要求的項目。</span><span class="sxs-lookup"><span data-stu-id="dacbe-276">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on an HTTP request.</span></span>  
  
### <a name="duplex-addressable-initiator"></a><span data-ttu-id="dacbe-277">雙工、可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="dacbe-277">Duplex, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="dacbe-278">繫結</span><span class="sxs-lookup"><span data-stu-id="dacbe-278">Binding</span></span>  
 <span data-ttu-id="dacbe-279">WCF 會提供完全非同步的雙向訊息交換模式使用兩個序列透過在一個傳入與一個傳出 HTTP 通道。</span><span class="sxs-lookup"><span data-stu-id="dacbe-279">WCF provides a fully-asynchronous, two-way message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="dacbe-280">在有限的情況下，此訊息交換模式可與 `Request/Reply`、`Addressable` 啟動器訊息交換模式混合使用。</span><span class="sxs-lookup"><span data-stu-id="dacbe-280">This message exchange pattern can be mixed with the `Request/Reply`, `Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="dacbe-281">WCF 會使用 HTTP 要求來傳送所有訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-281">WCF uses HTTP requests to transmit all messages.</span></span> <span data-ttu-id="dacbe-282">所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="dacbe-282">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="dacbe-283">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="dacbe-283">CreateSequence Exchange</span></span>  
 <span data-ttu-id="dacbe-284">WCF 啟動者傳送出去`CreateSequence`訊息，其`Offer`HTTP 要求的項目。</span><span class="sxs-lookup"><span data-stu-id="dacbe-284">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="dacbe-285">WCF 回應程式會確保`CreateSequence`已經`Offer`項目，然後建立序列，並傳輸`CreateSequenceResponse`訊息，其`Accept`項目。</span><span class="sxs-lookup"><span data-stu-id="dacbe-285">The WCF Responder ensures that the `CreateSequence` has an `Offer` element, then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="sequence-lifetime"></a><span data-ttu-id="dacbe-286">序列存留期</span><span class="sxs-lookup"><span data-stu-id="dacbe-286">Sequence Lifetime</span></span>  
 <span data-ttu-id="dacbe-287">WCF 會將兩個序列視為一個全雙工工作階段。</span><span class="sxs-lookup"><span data-stu-id="dacbe-287">WCF treats the two sequences as one fully-duplex session.</span></span>  
  
 <span data-ttu-id="dacbe-288">在產生可挑剔某個序列的錯誤，WCF 會預期遠端端點將同時挑剔兩個序列。</span><span class="sxs-lookup"><span data-stu-id="dacbe-288">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="dacbe-289">在讀取可挑剔某個序列的錯誤，WCF 會挑剔兩個序列。</span><span class="sxs-lookup"><span data-stu-id="dacbe-289">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>  
  
 <span data-ttu-id="dacbe-290">WCF 可以關閉其傳出序列並繼續處理其傳入序列的訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-290">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="dacbe-291">相反地，WCF 可以處理傳入序列的關閉，並繼續傳送其傳出序列的訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-291">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a><span data-ttu-id="dacbe-292">要求-回覆和單向、不可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="dacbe-292">Request-Reply and One-Way, Non-Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="dacbe-293">繫結</span><span class="sxs-lookup"><span data-stu-id="dacbe-293">Binding</span></span>  
 <span data-ttu-id="dacbe-294">WCF 提供單向和要求-回覆訊息交換模式使用兩個序列透過在一個 HTTP 通道。</span><span class="sxs-lookup"><span data-stu-id="dacbe-294">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="dacbe-295">WCF 會使用 HTTP 要求來傳送所有訊息從啟動器至回應程式並透過 HTTP 回應來都傳送所有訊息從回應者至啟動器。</span><span class="sxs-lookup"><span data-stu-id="dacbe-295">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="dacbe-296">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="dacbe-296">CreateSequence Exchange</span></span>  
 <span data-ttu-id="dacbe-297">WCF 啟動者傳送出去`CreateSequence`訊息，其`Offer`HTTP 要求的項目，並預期`CreateSequenceResponse`HTTP 回應的訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-297">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="dacbe-298">WCF 回應程式會建立序列，並將傳送`CreateSequenceResponse`訊息，其`Accept`HTTP 回應上的項目。</span><span class="sxs-lookup"><span data-stu-id="dacbe-298">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element on the HTTP response.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="dacbe-299">單向訊息</span><span class="sxs-lookup"><span data-stu-id="dacbe-299">One-way Message</span></span>  
 <span data-ttu-id="dacbe-300">若要成功完成單向訊息交換，WCF 啟動器會傳送要求序列訊息的 HTTP 要求並接收獨立`SequenceAcknowledgement`HTTP 回應的訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-300">To complete a one-way message exchange successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="dacbe-301">`SequenceAcknowledgement` 必須認可傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-301">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>  
  
 <span data-ttu-id="dacbe-302">WCF 回應可能以回覆要求認可、 錯誤或是內含空本文與 HTTP 202 狀態碼的回應。</span><span class="sxs-lookup"><span data-stu-id="dacbe-302">The WCF Responder may reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="two-way-messages"></a><span data-ttu-id="dacbe-303">雙向訊息</span><span class="sxs-lookup"><span data-stu-id="dacbe-303">Two Way Messages</span></span>  
 <span data-ttu-id="dacbe-304">若要成功完成雙向訊息交換通訊協定，WCF 啟動者傳送要求序列訊息的 HTTP 要求和接收 HTTP 回應的回覆序列訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-304">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="dacbe-305">回應中必須包含認可傳輸之要求序列訊息的 `SequenceAcknowledgement`。</span><span class="sxs-lookup"><span data-stu-id="dacbe-305">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>  
  
 <span data-ttu-id="dacbe-306">WCF 回應可能以回覆要求應用程式回覆、 錯誤或是內含空本文與 HTTP 202 狀態碼的回應。</span><span class="sxs-lookup"><span data-stu-id="dacbe-306">The WCF Responder may reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>  
  
 <span data-ttu-id="dacbe-307">由於單向訊息與應用程式回覆時機的緣故，要求序列訊息的序號與回應訊息的序號彼此並未互相關聯。</span><span class="sxs-lookup"><span data-stu-id="dacbe-307">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>  
  
#### <a name="retrying-replies"></a><span data-ttu-id="dacbe-308">重試回覆</span><span class="sxs-lookup"><span data-stu-id="dacbe-308">Retrying Replies</span></span>  
 <span data-ttu-id="dacbe-309">WCF 需仰賴雙向訊息交換通訊協定相互關聯的 HTTP 要求-回覆相互關聯。</span><span class="sxs-lookup"><span data-stu-id="dacbe-309">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="dacbe-310">因為這個緣故，WCF 啟動器不會停止在認可要求序列訊息時，重試要求序列訊息，但而當 HTTP 回應內含`SequenceAcknowledgement`，應用程式回覆或錯誤。</span><span class="sxs-lookup"><span data-stu-id="dacbe-310">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries a `SequenceAcknowledgement`, application reply, or fault.</span></span> <span data-ttu-id="dacbe-311">WCF 回應重試回覆相互關聯之要求的 HTTP 回應的回覆。</span><span class="sxs-lookup"><span data-stu-id="dacbe-311">The WCF Responder retries replies on the HTTP response of the request to which the reply is correlated.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="dacbe-312">CloseSequence 交換</span><span class="sxs-lookup"><span data-stu-id="dacbe-312">CloseSequence Exchange</span></span>  
 <span data-ttu-id="dacbe-313">接收之後所有回覆序列訊息與認可所有單向要求序列訊息時，WCF 啟動者傳送出去`CloseSequence`HTTP 要求將要求序列訊息，並預期`CloseSequenceResponse`HTTP 回應。</span><span class="sxs-lookup"><span data-stu-id="dacbe-313">After receiving all reply sequence messages and acknowledgements for all one way request sequence messages, the WCF Initiator transmits a `CloseSequence` message for the request sequence on an HTTP request and expects the `CloseSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="dacbe-314">隱含地關閉要求序列會一併關閉回覆序列。</span><span class="sxs-lookup"><span data-stu-id="dacbe-314">Closing the request sequence implicitly closes the reply sequence.</span></span> <span data-ttu-id="dacbe-315">這表示 WCF 啟動器包含回覆序列的最終`SequenceAcknowledgement`上`CloseSequence`訊息，而且回覆序列沒有`CloseSequence`exchange。</span><span class="sxs-lookup"><span data-stu-id="dacbe-315">This means the WCF Initiator includes the reply sequence’s Final `SequenceAcknowledgement` on the `CloseSequence` message and the reply sequence does not have a `CloseSequence` exchange.</span></span>  
  
 <span data-ttu-id="dacbe-316">WCF 回應程式可確保所有回覆認可，並將傳送`CloseSequenceResponse`HTTP 回應的訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-316">The WCF Responder ensures all replies are acknowledged and transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="dacbe-317">TerminateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="dacbe-317">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="dacbe-318">在收到後`CloseSequenceResponse`訊息，WCF 起始端傳輸`TerminateSequence`HTTP 要求將要求序列訊息，並預期`TerminateSequenceResponse`HTTP 回應。</span><span class="sxs-lookup"><span data-stu-id="dacbe-318">After receiving the `CloseSequenceResponse` message, the WCF Initiator transmits a `TerminateSequence` message for the request sequence on an HTTP request and expects the `TerminateSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="dacbe-319">就像 `CloseSequence` 交換一樣，終止要求序列會隱含地終止回覆序列。</span><span class="sxs-lookup"><span data-stu-id="dacbe-319">Like the `CloseSequence` exchange, terminating the request sequence implicitly terminates the reply sequence.</span></span> <span data-ttu-id="dacbe-320">這表示 WCF 啟動器包含回覆序列的最終`SequenceAcknowledgement`上`TerminateSequence`訊息，而且回覆序列沒有`TerminateSequence`exchange。</span><span class="sxs-lookup"><span data-stu-id="dacbe-320">This means the WCF Initiator includes the reply sequence’s final `SequenceAcknowledgement` on the `TerminateSequence` message and the reply sequence does not have a `TerminateSequence` exchange.</span></span>  
  
 <span data-ttu-id="dacbe-321">WCF 回應傳輸`TerminateSequenceResponse`HTTP 回應的訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-321">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="dacbe-322">要求/回覆、可定址啟動器</span><span class="sxs-lookup"><span data-stu-id="dacbe-322">Request/Reply, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="dacbe-323">繫結</span><span class="sxs-lookup"><span data-stu-id="dacbe-323">Binding</span></span>  
 <span data-ttu-id="dacbe-324">WCF 會提供要求-回覆訊息交換模式使用兩個序列透過在一個傳入與一個傳出 HTTP 通道。</span><span class="sxs-lookup"><span data-stu-id="dacbe-324">WCF provides a request-reply message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="dacbe-325">在有限的情況下，此訊息交換模式可與 `Duplex, Addressable` 啟動器訊息交換模式混合使用。</span><span class="sxs-lookup"><span data-stu-id="dacbe-325">This message exchange pattern can be mixed with the `Duplex, Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="dacbe-326">WCF 會使用 HTTP 要求來傳送所有訊息。</span><span class="sxs-lookup"><span data-stu-id="dacbe-326">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="dacbe-327">所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="dacbe-327">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="dacbe-328">CreateSequence 交換</span><span class="sxs-lookup"><span data-stu-id="dacbe-328">CreateSequence Exchange</span></span>  
 <span data-ttu-id="dacbe-329">WCF 啟動者傳送出去`CreateSequence`訊息，其`Offer`HTTP 要求的項目。</span><span class="sxs-lookup"><span data-stu-id="dacbe-329">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="dacbe-330">WCF 回應程式會確保`CreateSequence`已經`Offer`項目然後建立序列，並傳輸`CreateSequenceResponse`訊息，其`Accept`項目。</span><span class="sxs-lookup"><span data-stu-id="dacbe-330">The WCF Responder ensures that the `CreateSequence` has an `Offer` element then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="requestreply-correlation"></a><span data-ttu-id="dacbe-331">要求/回覆相互關聯</span><span class="sxs-lookup"><span data-stu-id="dacbe-331">Request/Reply Correlation</span></span>  
 <span data-ttu-id="dacbe-332">下列會套用到所有相互關聯的要求及回覆：</span><span class="sxs-lookup"><span data-stu-id="dacbe-332">The following applies to all correlated requests and replies:</span></span>  
  
-   <span data-ttu-id="dacbe-333">WCF 可確保所有的應用程式要求訊息都帶有`ReplyTo`端點參考和`MessageId`。</span><span class="sxs-lookup"><span data-stu-id="dacbe-333">WCF ensures all application request messages bear a `ReplyTo` endpoint reference and a `MessageId`.</span></span>  
  
-   <span data-ttu-id="dacbe-334">WCF 會將本機端點參照套用為每個應用程式要求訊息`ReplyTo`。</span><span class="sxs-lookup"><span data-stu-id="dacbe-334">WCF applies the local endpoint reference as each application request message’s `ReplyTo`.</span></span> <span data-ttu-id="dacbe-335">啟動器的本機端點參照是 `CreateSequence` 訊息的 `ReplyTo`，而回應程式的本機端點參照則是 `CreateSequence` 訊息的 `To`。</span><span class="sxs-lookup"><span data-stu-id="dacbe-335">The local endpoint reference is the `CreateSequence` message’s `ReplyTo` for the Initiator and the `CreateSequence` message’s `To` for the Responder.</span></span>  
  
-   <span data-ttu-id="dacbe-336">WCF 可讓您確保傳入的要求訊息都帶有`MessageId`和`ReplyTo`。</span><span class="sxs-lookup"><span data-stu-id="dacbe-336">WCF ensures that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span>  
  
-   <span data-ttu-id="dacbe-337">WCF 可確保`ReplyTo`稍早定義的所有應用程式要求訊息的端點參照 URI 符合本機端點參照。</span><span class="sxs-lookup"><span data-stu-id="dacbe-337">WCF ensures the `ReplyTo` endpoint reference’s URI of all application request messages match the local endpoint reference as defined earlier.</span></span>  
  
-   <span data-ttu-id="dacbe-338">WCF 可讓您確保所有回覆都帶有正確`RelatesTo`並`To`遵循的標頭`wsa`要求/回覆相互關聯規則。</span><span class="sxs-lookup"><span data-stu-id="dacbe-338">WCF ensures that all replies bear the correct `RelatesTo` and `To` headers following `wsa` request/reply correlation rules.</span></span>

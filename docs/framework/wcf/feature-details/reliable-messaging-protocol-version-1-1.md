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
# <a name="reliable-messaging-protocol-version-11"></a>Reliable Messaging Protocol 1.1 版
本主題涵蓋了 WS-ReliableMessaging February 2007 (1.1 版) 通訊協定的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 實作詳細資料，這個通訊協定是使用 HTTP 傳輸來進行交互操作時所需的通訊協定。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 遵循本主題所述 WS-ReliableMessaging 規格的條件約束及說明。 請注意開始實作 Ws-reliablemessaging 1.1 版通訊協定[!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]。  
  
 WS-ReliableMessaging February 2007 通訊協定可透過 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 在 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> 中實作。  
  
 為了方便起見，本主題將使用下列角色：  
  
-   啟動器：啟動 WS-Reliable 訊息序列建立作業的用戶端。  
  
-   回應程式：接收啟動器要求的服務。  
  
 本文件會使用下表的前置詞和命名空間。  
  
|前置詞|命名空間|  
|-|-|  
|wsrm|http://docs.oasis-open.org/ws-rx/wsrm/200702|  
|netrm|http://schemas.microsoft.com/ws/2006/05/rm|  
|s|http://www.w3.org/2003/05/soap-envelope|  
|wsa|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|wsse|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
|wsrmp|http://docs.oasis-open.org/ws-rx/wsrmp/200702|  
|netrmp|http://schemas.microsoft.com/ws-rx/wsrmp/200702|  
|wsp|(WS-Policy 1.2 或 WS-Policy 1.5)|  
  
## <a name="messaging"></a>傳訊  
  
### <a name="sequence-creation"></a>建立序列  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會實作 `CreateSequence` 和 `CreateSequenceResponse` 訊息以建立可信賴傳訊序列。 以下是適用的條件約束：  
  
-   B1101：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器使用的端點參照與 `CreateSequence` 訊息的 `ReplyTo`、`AcksTo` 和 `Offer/Endpoint` 使用的端點參照一樣。  
  
-   R1102：`AcksTo` 訊息中的 `ReplyTo`、`Offer/Endpoint` 和 `CreateSequence` 端點參照必須具有包含相同字串表示的位址值以符合八位元規格。  
  
    -   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式在建立序列之前，會先驗證 `AcksTo`、`ReplyTo` 和 `Endpoint` 端點參照的 URI 部分是否相同。  
  
-   R1103：`AcksTo` 訊息中的 `ReplyTo`、`Offer/Endpoint` 和 `CreateSequence` 端點參照應該具有相同的參照參數集合。  
  
    -   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不會強制執行，但會假定 `AcksTo` 上的 `ReplyTo`、`Offer/Endpoint` 和 `CreateSequence` 端點參照之參照參數都是一樣，並且使用來自 `ReplyTo` 端點參照的參照參數，以認可並與序列訊息對話。  
  
-   B1104：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器不會在 `Expires` 訊息中產生選用的 `Offer/Expires` 或 `CreateSequence` 項目。  
  
-   B1105：在存取 `CreateSequence` 訊息時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會使用 `Expires` 項目中的 `CreateSequence` 值做為 `Expires` 項目中的 `CreateSequenceResponse` 值。 否則，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式將讀取並忽略 `Expires` 和 `Offer/Expires` 值。  
  
-   B1106：在存取 `CreateSequenceResponse` 訊息時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會讀取選用的 `Expires` 值但不會加以使用。  
  
-   B1107：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器和回應程式一律在 `IncompleteSequenceBehavior` 和 `CreateSequence/Offer` 項目中產生選用的 `CreateSequenceResponse` 項目。  
  
-   B1108：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 只會使用 `DiscardFollowingFirstGap` 項目中的 `NoDiscard` 和 `IncompleteSequenceBehavior` 值。  
  
    -   WS-ReliableMessaging 會使用 `Offer` 機制來建立兩個反向關聯序列以形成工作階段。  
  
-   B1109：如果 `CreateSequence` 包含 `Offer` 項目，單向 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會透過不含 `CreateSequenceResponse` 項目的 `Accept` 來回應以拒絕提供的序列。  
  
-   B1110：如果可信賴傳訊回應程式拒絕了提供的序列，則 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會挑出新建立序列的錯誤。  
  
-   B1111：如果 `CreateSequence` 不包含 `Offer` 項目，雙向 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會透過 `CreateSequenceRefused` 錯誤來回應以拒絕提供的序列。  
  
-   R1112：當兩個反向序列都是透過 `Offer` 機制建立時，`[address]` 端點參照之 `CreateSequenceResponse/Accept/AcksTo` 屬性的每個位元組必須完全符合 `CreateSequence` 訊息之目的 URI 的每個位元組。  
  
-   R1113：當兩個反向序列都是透過 `Offer` 機制建立時，從啟動器流向回應程式之雙邊序列上的所有訊息必須傳送至相同的端點參照。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 使用 WS-ReliableMessaging 在啟動器與回應程式之間建立可靠工作階段。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-ReliableMessaging 實作會針對單向、要求-回覆與全雙工訊息模式提供可靠工作階段。 `Offer` 和 `CreateSequence` 上的 WS-ReliableMessaging `CreateSequenceResponse` 機制可讓您建立兩個相互關聯的反向序列，並提供適用於所有訊息端點的工作階段通訊協定。 由於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會針對此類工作階段提供安全性保證，包含工作階段完整性的端對端保護，因此可以實際地確保訊息會抵達預定的相同目的地。 這麼做也可以針對應用程式訊息進行 "piggy-backing" 的序列認可作業。 因此，條件約束 R1102、 R1112 和 R1113 適用於[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]。  
  
 `CreateSequence` 訊息的範例。  
  
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
  
 `CreateSequenceResponse` 訊息的範例。  
  
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
  
### <a name="closing-a-sequence"></a>關閉序列  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會使用 `CloseSequence` 和 `CloseSequenceResponse` 訊息支援由來源啟始的可信賴傳訊關閉作業。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可信賴傳訊目的地不會啟始關閉作業，而且 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可信賴傳訊來源不支援從目的地啟始的可信賴傳訊關閉作業。 以下是適用的條件約束：  
  
-   B1201：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可信賴傳訊來源一律傳送 `CloseSequence` 訊息來關閉序列。  
  
-   B1202：可信賴傳訊來源會在傳送 `CloseSequence` 訊息之前，等候整個序列訊息的認可。  
  
-   B1203：可信賴傳訊來源一律包含選用的 `LastMsgNumber` 項目 (除非序列不包含訊息)。  
  
-   R1204：可信賴傳訊目的地不可以藉由傳送 `CloseSequence` 訊息來啟始關閉作業。  
  
-   B1205：在收到 `CloseSequence` 訊息時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可信賴傳訊來源會將序列視為不完整並傳送錯誤。  
  
 `CloseSequence` 訊息的範例。  
  
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
  
### <a name="sequence-termination"></a>終止序列  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 在完成了 `TerminateSequence/TerminateSequenceResponse` 交握之後，主要使用 `CloseSequence/CloseSequenceResponse` 交握。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可信賴傳訊目的地不會啟始終止作業，而且可信賴傳訊來源不支援從目的地啟始的可信賴傳訊終止作業。 以下是適用的條件約束：  
  
-   B1301：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器只會在成功完成 `TerminateSequence` 交握之後，才傳送 `CloseSequence/CloseSequenceResponse` 訊息。  
  
-   R1302：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會針對特定序列，驗證所有 `LastMsgNumber` 和 `CloseSequence` 訊息上的 `TerminateSequence` 項目是否一致。 也就是說，`LastMsgNumber` 不是不存在於所有 `CloseSequence` 和 `TerminateSequence` 訊息上，就是存在於所有 `CloseSequence` 和 `TerminateSequence` 訊息上而且全部一樣。  
  
-   B1303：在 `TerminateSequence` 交握之後收到 `CloseSequence/CloseSequenceResponse` 訊息時，可信賴傳訊目的地會以 `TerminateSequenceResponse` 訊息來回應。 由於可信賴傳訊來源在傳送 `TerminateSequence` 訊息之前已經獲得最後的認可，因此可信賴傳訊目的地毫無疑問地知道序列已結束並立即回收資源。  
  
-   B1304：在 `TerminateSequence` 交握之前收到 `CloseSequence/CloseSequenceResponse` 訊息時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可信賴傳訊目的地會以 `TerminateSequenceResponse` 訊息來回應。 如果可信賴傳訊目的地判斷序列中沒有任何不一致的項目，則可信賴傳訊目的地會等候應用程式目的地指定的時間一到再回收資源，以便讓用戶端有機會接收最後的認可。 否則，可信賴傳訊目的地會立即回收資源並引發 `Faulted` 事件以向應用程式目的地指出序列是在不確定的情況下結束。  
  
 `TerminateSequence` 訊息的範例。  
  
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
  
### <a name="sequences"></a>序列  
 下列清單列出適用於序列的條件約束：  
  
-   B1401:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]會產生並存取序號大於`xs:long`的最大包含值，9223372036854775807。  
  
 `Sequence` 標頭的範例。  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a>要求認可  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會使用 `AckRequested` 標頭做為 Keep-Alive 機制。  
  
 `AckRequested` 標頭的範例。  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會針對 WS-Reliable 訊息所提供的序列認可使用 "piggy-back" 機制。 以下是適用的條件約束：  
  
-   R1601： 當兩個反向序列會建立使用`Offer`機制，`SequenceAcknowledgement`標頭可能包含在傳送給預定收件者的任何應用程式訊息。 遠端端點必須能夠存取以 Piggyback 方式傳送的 `SequenceAcknowledgement` 標頭。  
  
-   B1602：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不會產生包含 `SequenceAcknowledgement` 元素的 `Nack` 標頭。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會驗證每個 `Nack` 元素是否都包含序號，但是另一方面會忽略 `Nack` 元素與值。  
  
 `SequenceAcknowledgement` 標頭的範例。  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a>WS-ReliableMessaging 錯誤  
 下列清單列出適用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 之 WS-ReliableMessaging 錯誤實作的條件約束： 以下是適用的條件約束：  
  
-   B1701:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]不會產生`MessageNumberRollover`錯誤。  
  
-   B1702：在 SOAP 1.2 中，當服務端點到達其連線限制，而且無法處理新的連線時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 就會產生巢狀 `CreateSequenceRefused` 錯誤子代碼 `netrm:ConnectionLimitReached`，如下列範例所示。  
  
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
  
### <a name="ws-addressing-faults"></a>WS-Addressing 錯誤  
 由於 WS-ReliableMessaging 是使用 WS-Addressing，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-ReliableMessaging 實作可能會產生並傳送 WS-Addressing 錯誤。 本節涵蓋 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 所明確產生並在 WS-ReliableMessaging 層加以傳送的 WS-Addressing 錯誤：  
  
-   B1801:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]會產生並傳輸`Message Addressing Header Required`當下列其中一項條件成立時，發生錯誤：  
  
    -   `CreateSequence`、`CloseSequence` 或 `TerminateSequence` 訊息缺少 `MessageId` 標頭。  
  
    -   `CreateSequence`、`CloseSequence` 或 `TerminateSequence` 訊息缺少 `ReplyTo` 標頭。  
  
    -   `CreateSequenceResponse`、`CloseSequenceResponse` 或 `TerminateSequenceResponse` 訊息缺少 `RelatesTo` 標頭。  
  
-   B1802:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]會產生並傳輸`Endpoint Unavailable`錯誤，表示沒有任何接聽的端點可以根據檢查結果中的定位標頭的順序進行處理`CreateSequence`訊息。  
  
## <a name="protocol-composition"></a>通訊協定組合  
  
### <a name="composition-with-ws-addressing"></a>與 WS-Addressing 組合  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 支援兩種版本的 WS-Addressing：WS-Addressing 2004/08 [WS-ADDR] 和 W3C WS-Addressing 1.0 建議 [WS-ADDR-CORE] 和 [WS-ADDR-SOAP]。  
  
 儘管 WS-ReliableMessaging 規格只提到 WS-Addressing 2004/08，它並未限制要使用的 WS-Addressing 版本。 下列清單列出適用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的條件約束：  
  
-   R2101：WS-Addressing 2004/08 和 WS-Addressing 1.0 皆可搭配 WS-Reliable 訊息一起使用。  
  
-   R2102：單一版本的 WS-Addressing 必須透過 `Offer` 機制，用在整個特定的 WS-ReliableMessaging 序列或是一對相關聯的反向序列上。  
  
### <a name="composition-with-soap"></a>與 SOAP 組合  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 同時支援 SOAP 1.1 和 SOAP 1.2 搭配 WS-Reliable 訊息一起使用。  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a>與 WS-Security 和 WS-SecureConversation 組合  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 透過安全傳輸 (HTTPS)、與 WS-Security 組合，以及與 WS-Secure Conversation 組合，為 WS-ReliableMessaging 序列提供保護。 WS-ReliableMessaging 1.1 通訊協定、WS-Security 1.1 和 WS-Secure Conversation 1.3 通訊協定應該一併使用。 下列清單列出適用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的條件約束：  
  
-   R2301：為了在個別訊息的完整性與機密性之外保護 WS-ReliableMessaging 序列的完整性，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 要求必須使用 WS-Secure Conversation。  
  
-   R2302:AWS-必須在建立了 Ws-reliablemessaging 序列前建立安全對話工作階段。  
  
-   R2303：如果 WS-ReliableMessaging 序列的存留期超過 WS-Secure Conversation 工作階段的存留期，則使用 WS-Secure Conversation 建立的 `SecurityContextToken` 必須透過對應的 WS-Secure Conversation 更新繫結來加以更新。  
  
-   B2304:WS-Ws-reliablemessaging 序列或是一對的相互關聯的反向順序永遠會繫結至單一的 Ws-secureconversation 工作階段。  
  
-   R2305：一旦與 WS-Secure Conversation 組合，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式就會要求 `CreateSequence` 訊息必須包含 `wsse:SecurityTokenReference` 項目和 `wsrm:UsesSequenceSTR` 標頭。  
  
 `UsesSequenceSTR` 標頭的範例。  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a>與 SSL/TLS 組合  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不支援與 SSL/TLS 工作階段的組合：  
  
-   B2401：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不會產生 `wsrm:UsesSequenceSSL` 標頭。  
  
-   R2402：可信賴傳訊啟動器不可以將帶有 `CreateSequence` 標頭的 `wsrm:UsesSequenceSSL` 訊息傳送到 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式中。  
  
### <a name="composition-with-ws-policy"></a>與 WS-Policy 組合  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 支援兩種版本的 WS-Policy：WS-Policy 1.2 和 WS-Policy 1.5。  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a>WS-ReliableMessaging WS-Policy 判斷提示  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 使用 WS-ReliableMessaging WS-Policy 判斷提示 `wsrm:RMAssertion` 來描述各項端點功能。 下列清單列出適用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的條件約束：  
  
-   B3001：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會將 `wsrmn:RMAssertion` WS-Policy 判斷提示附加至 `wsdl:binding` 元素。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 同時支援附加至 `wsdl:binding` 和 `wsdl:port` 元素。  
  
-   B3002：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 永遠不會產生 `wsp:Optional` 標記。  
  
-   B3003：存取 `wsrmp:RMAssertion` WS-Policy 判斷提示時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會忽略 `wsp:Optional` 標記並將 WS-RM 原則視為強制執行原則。  
  
-   R3004：由於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 無法與 SSL/TLS 工作階段組合，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不會接受用來指定 `wsrmp:SequenceTransportSecurity` 的原則。  
  
-   B3005：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 一律產生 `wsrmp:DeliveryAssurance` 項目。  
  
-   B3006：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 一律指定 `wsrmp:ExactlyOnce` 傳遞保證。  
  
-   B3007：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會產生並讀取下列 WS-ReliableMessaging 判斷提示屬性，並透過 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]`ReliableSessionBindingElement` 針對這些屬性提供控制權：  
  
    -   `netrmp:InactivityTimeout`  
  
    -   `netrmp:AcknowledgementInterval`  
  
     `RMAssertion` 的範例。  
  
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
  
## <a name="flow-control-ws-reliablemessaging-extension"></a>WS-ReliableMessaging 延伸的流量控制  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會透過 WS-ReliableMessaging 擴充性，針對序列訊息流量提供其他更嚴格的選擇性控制。  
  
 藉由設定已啟用流量控制`ReliableSessionBindingElement`的`FlowControlEnabled``boolean`屬性`true`。 下列清單列出適用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的條件約束：  
  
-   B4001：一旦啟用了可信賴傳訊流量控制，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會在 `netrm:BufferRemaining` 標頭的項目擴充性中產生 `SequenceAcknowledgement` 項目，如下列範例所示。  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B4002：即使啟用了可信賴傳訊流量控制，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 也不需要 `netrm:BufferRemaining` 標頭中的 `SequenceAcknowledgement` 項目。  
  
-   B4003：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可信賴傳訊目的地使用 `netrm:BufferRemaining` 來指出能夠緩衝處理的新訊息數目。  
  
-   已啟用 B4004:When 可信賴傳訊流量控制，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]可信賴傳訊來源會使用值`netrm:BufferRemaining`節流訊息傳輸。  
  
-   B4005：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會產生介於 0 到 4096 (含) 之間的 `netrm:BufferRemaining` 整數值，並讀取介於 0 和 `xs:int` 的 `maxInclusive` 值 214748364 (含) 之間的整數值。  
  
## <a name="message-exchange-patterns"></a>訊息交換模式  
 本節將說明當不同訊息交換模式使用 WS-ReliableMessaging 時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的行為。 在每個訊息交換模式中，會考慮下列兩種部署案例：  
  
-   不可定址的啟動器：啟動器位於防火牆後方，回應程式只能透過 HTTP 回應將訊息傳送至啟動器。  
  
-   可定址的啟動器：可將 HTTP 要求同時傳送給啟動器與回應程式，亦即可建立兩個反向 HTTP 連線。  
  
### <a name="one-way-non-addressable-initiator"></a>單向、不可定址啟動器  
  
#### <a name="binding"></a>繫結  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 透過在一個 HTTP 通道上使用一個序列的方式，提供單向的訊息交換模式。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會使用 HTTP 要求將所有訊息從啟動器傳送至回應程式，並透過 HTTP 回應將所有訊息從回應程式傳送至啟動器。  
  
#### <a name="createsequence-exchange"></a>CreateSequence 交換  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會透過 HTTP 要求將不包含 `CreateSequence` 項目的 `Offer` 訊息傳送出去，並預期透過 HTTP 回應接收 `CreateSequenceResponse` 訊息。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會建立序列，並透過 HTTP 回應將不包含 `CreateSequenceResponse` 項目的 `Accept` 訊息傳送出去。  
  
#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會處理所有訊息回覆的認可，除了 `CreateSequence` 訊息與錯誤訊息以外。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式一律透過 HTTP 回應將獨立認可傳送至所有序列和 `AckRequested` 訊息。  
  
#### <a name="closesequence-exchange"></a>CloseSequence 交換  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會透過 HTTP 要求將 `CloseSequence` 訊息傳送出去，並預期透過 HTTP 回應接收 `CreateSequenceResponse` 訊息。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會透過 HTTP 回應將 `CloseSequenceResponse` 訊息傳送出去。  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence 交換  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會透過 HTTP 要求將 `TerminateSequence` 訊息傳送出去，並預期透過 HTTP 回應接收 `TerminateSequenceResponse` 訊息。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會透過 HTTP 回應將 `TerminateSequenceResponse` 訊息傳送出去。  
  
### <a name="one-way-addressable-initiator"></a>單向、可定址啟動器  
  
#### <a name="binding"></a>繫結  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 透過在一個傳入與一個傳出 HTTP 通道上使用一個序列的方式，提供單向的訊息交換模式。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會使用 HTTP 要求來傳送所有訊息。 所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。  
  
#### <a name="createsequence-exchange"></a>CreateSequence 交換  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會透過 HTTP 要求將不包含 `CreateSequence` 項目的 `Offer` 訊息傳送出去。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會建立序列，並透過 HTTP 要求將不包含 `CreateSequenceResponse` 項目的 `Accept` 訊息傳送出去。  
  
### <a name="duplex-addressable-initiator"></a>雙工、可定址啟動器  
  
#### <a name="binding"></a>繫結  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 透過在一個傳入與一個傳出 HTTP 通道上使用兩個序列的方式，提供完全非同步、雙向的訊息交換模式。 在有限的情況下，此訊息交換模式可與 `Request/Reply`、`Addressable` 啟動器訊息交換模式混合使用。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會使用 HTTP 要求來傳送所有訊息。 所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。  
  
#### <a name="createsequence-exchange"></a>CreateSequence 交換  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會透過 HTTP 要求將包含 `CreateSequence` 項目的 `Offer` 訊息傳送出去。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會確保 `CreateSequence` 包含 `Offer` 項目，然後建立序列並將包含 `CreateSequenceResponse` 項目的 `Accept` 訊息傳送出去。  
  
#### <a name="sequence-lifetime"></a>序列存留期  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會將兩個序列視為一個全雙工工作階段。  
  
 在產生可挑剔某個序列的錯誤時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 預期遠端端點將同時挑剔兩個序列。 在讀取可挑剔某個序列的錯誤時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 將同時挑剔兩個序列。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可關閉本身的傳出序列並繼續處理其傳入序列中的訊息。 反之，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可以處理傳入序列的關閉作業並繼續傳送其傳出序列中的訊息。  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a>要求-回覆和單向、不可定址啟動器  
  
#### <a name="binding"></a>繫結  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 透過在一個 HTTP 通道上使用兩個序列的方式，提供單向、要求-回覆的訊息交換模式。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會使用 HTTP 要求將所有訊息從啟動器傳送至回應程式，並透過 HTTP 回應將所有訊息從回應程式傳送至啟動器。  
  
#### <a name="createsequence-exchange"></a>CreateSequence 交換  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會透過 HTTP 要求將包含 `CreateSequence` 項目的 `Offer` 訊息傳送出去，並預期透過 HTTP 回應接收 `CreateSequenceResponse` 訊息。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會建立序列，並透過 HTTP 回應將包含 `CreateSequenceResponse` 項目的 `Accept` 訊息傳送出去。  
  
#### <a name="one-way-message"></a>單向訊息  
 為了成功完成單向訊息交換，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會在 HTTP 要求上傳送要求序列訊息，並在 HTTP 回應上接收獨立的 `SequenceAcknowledgement` 訊息。 `SequenceAcknowledgement` 必須認可傳送的訊息。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式可透過認可、錯誤或是內含空本文與 HTTP 202 狀態碼的回應來回覆要求。  
  
#### <a name="two-way-messages"></a>雙向訊息  
 為了成功完成雙向訊息交換通訊協定，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會透過 HTTP 要求傳送要求序列訊息，並透過 HTTP 回應接收回覆序列訊息。 回應中必須包含認可傳輸之要求序列訊息的 `SequenceAcknowledgement`。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式可透過應用程式回覆、錯誤或是內含空本文與 HTTP 202 狀態碼的回應來回覆要求。  
  
 由於單向訊息與應用程式回覆時機的緣故，要求序列訊息的序號與回應訊息的序號彼此並未互相關聯。  
  
#### <a name="retrying-replies"></a>重試回覆  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 仰賴 HTTP 要求-回覆相互關聯來執行雙向訊息交換通訊協定的相互關聯作業。 由於這個緣故，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器不會在認可要求序列訊息時停止重試要求序列訊息，而會在 HTTP 回應內含 `SequenceAcknowledgement`、應用程式回覆，或是錯誤時，才停止重試要求序列訊息。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會在與回覆相互關聯之要求的 HTTP 回應上重試回覆。  
  
#### <a name="closesequence-exchange"></a>CloseSequence 交換  
 在收到所有單向要求序列訊息的所有回覆序列訊息與認可時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會透過 HTTP 要求傳送要求序列的 `CloseSequence` 訊息，並預期透過 HTTP 回應收到 `CloseSequenceResponse`。  
  
 隱含地關閉要求序列會一併關閉回覆序列。 也就是說，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會在 `SequenceAcknowledgement` 訊息中包含回覆序列的最終 `CloseSequence`，而且回覆序列不會有 `CloseSequence` 交換。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會確保所有回覆都已認可，並透過 HTTP 回應來傳送 `CloseSequenceResponse` 訊息。  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence 交換  
 在收到 `CloseSequenceResponse` 訊息之後，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會透過 HTTP 要求將要求序列的 `TerminateSequence` 訊息傳送出去，並預期透過 HTTP 回應收到 `TerminateSequenceResponse`。  
  
 就像 `CloseSequence` 交換一樣，終止要求序列會隱含地終止回覆序列。 也就是說，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會在 `SequenceAcknowledgement` 訊息中包含回覆序列的最終 `TerminateSequence`，而且回覆序列不會有 `TerminateSequence` 交換。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會透過 HTTP 回應將 `TerminateSequenceResponse` 訊息傳送出去。  
  
### <a name="requestreply-addressable-initiator"></a>要求/回覆、可定址啟動器  
  
#### <a name="binding"></a>繫結  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 透過在一個傳入與一個傳出 HTTP 通道上使用兩個序列的方式，提供要求-回覆訊息交換模式。 在有限的情況下，此訊息交換模式可與 `Duplex, Addressable` 啟動器訊息交換模式混合使用。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會使用 HTTP 要求來傳送所有訊息。 所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。  
  
#### <a name="createsequence-exchange"></a>CreateSequence 交換  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會透過 HTTP 要求將包含 `CreateSequence` 項目的 `Offer` 訊息傳送出去。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會確保 `CreateSequence` 包含 `Offer` 項目，然後建立序列並將包含 `CreateSequenceResponse` 項目的 `Accept` 訊息傳送出去。  
  
#### <a name="requestreply-correlation"></a>要求/回覆相互關聯  
 下列會套用到所有相互關聯的要求及回覆：  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可確保所有應用程式要求訊息都帶有 `ReplyTo` 端點參照和 `MessageId`。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會將本機端點參照當成每個應用程式要求訊息的 `ReplyTo` 來套用。 啟動器的本機端點參照是 `CreateSequence` 訊息的 `ReplyTo`，而回應程式的本機端點參照則是 `CreateSequence` 訊息的 `To`。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可確保所有傳入的要求訊息都帶有 `MessageId` 和 `ReplyTo`。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可確保所有應用程式要求訊息的 `ReplyTo` 端點參照 URI 都符合如先前定義的本機端點參照。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可確保所有回覆都帶有正確且遵循 `RelatesTo` 要求/回覆相互關聯規則的 `To` 和 `wsa` 標頭。

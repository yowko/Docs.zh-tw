---
title: Reliable Messaging Protocol 1.1 版
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: 8ff02bc6953ec1e5030dd0b592a352b7e23ab0d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="reliable-messaging-protocol-version-11"></a>Reliable Messaging Protocol 1.1 版
本主題涵蓋 Windows Communication Foundation (WCF) 實作詳細資料的 WS-SECURITY 與 Ws-reliablemessaging February 2007 （1.1 版） 通訊協定所需使用 HTTP 傳輸的互通性。 WCF 會遵循的條件約束及說明本主題所述 Ws-reliablemessaging 規格。 請注意開始實作 Ws-reliablemessaging 1.1 版通訊協定[!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]。  
  
 Ws-reliablemessaging February 2007 通訊協定的實作中的 WCF <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>。  
  
 為了方便起見，本主題將使用下列角色：  
  
-   啟動器：啟動 WS-Reliable 訊息序列建立作業的用戶端。  
  
-   回應程式：接收啟動器要求的服務。  
  
 本文件會使用下表的前置詞和命名空間。  
  
|前置詞|命名空間|  
|-|-|  
|wsrm|http://docs.oasis-open.org/ws-rx/wsrm/200702|  
|netrm|http://schemas.microsoft.com/ws/2006/05/rm|  
|秒|http://www.w3.org/2003/05/soap-envelope|  
|wsa|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|wsse|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
|wsrmp|http://docs.oasis-open.org/ws-rx/wsrmp/200702|  
|netrmp|http://schemas.microsoft.com/ws-rx/wsrmp/200702|  
|wsp|(WS-Policy 1.2 或 WS-Policy 1.5)|  
  
## <a name="messaging"></a>訊息  
  
### <a name="sequence-creation"></a>建立序列  
 WCF 實作`CreateSequence`和`CreateSequenceResponse`訊息以建立可信賴傳訊序列。 以下是適用的條件約束：  
  
-   B1101: WCF 啟動者會使用相同的端點參照一樣`CreateSequence`訊息的`ReplyTo`，`AcksTo`和`Offer/Endpoint`。  
  
-   R1102：`AcksTo` 訊息中的 `ReplyTo`、`Offer/Endpoint` 和 `CreateSequence` 端點參照必須具有包含相同字串表示的位址值以符合八位元規格。  
  
    -   WCF 回應程式會驗證的 URI 部分`AcksTo`，`ReplyTo`和`Endpoint`建立序列之前，端點參考完全相同。  
  
-   R1103：`AcksTo` 訊息中的 `ReplyTo`、`Offer/Endpoint` 和 `CreateSequence` 端點參照應該具有相同的參照參數集合。  
  
    -   WCF 不會強制執行，但會採用該參考參數`AcksTo`，`ReplyTo`和`Offer/Endpoint`端點參照`CreateSequence`都相同，而且使用參考參數，從`ReplyTo`的端點參考認可並與序列訊息對話。  
  
-   B1104: WCF 啟動器不會產生選擇性`Expires`或`Offer/Expires`中的項目`CreateSequence`訊息。  
  
-   B1105： 存取時`CreateSequence`訊息，WCF 回應程式則使用`Expires`值`CreateSequence`項目做為`Expires`值`CreateSequenceResponse`項目。 否則，WCF 回應程式將讀取並忽略`Expires`和`Offer/Expires`值。  
  
-   B1106： 存取時`CreateSequenceResponse`訊息，WCF 啟動器會讀取選用`Expires`值但不是會使用它。  
  
-   B1107: WCF 啟動器和回應程式一律產生選用`IncompleteSequenceBehavior`中的項目`CreateSequence/Offer`和`CreateSequenceResponse`項目。  
  
-   B1108: WCF 只會使用`DiscardFollowingFirstGap`和`NoDiscard`值`IncompleteSequenceBehavior`項目。  
  
    -   WS-ReliableMessaging 會使用 `Offer` 機制來建立兩個反向關聯序列以形成工作階段。  
  
-   B1109： 如果`CreateSequence`包含`Offer`項目，單向 WCF 回應程式拒絕提供的序列來回應以`CreateSequenceResponse`沒有`Accept`項目。  
  
-   B1110： 如果可信賴傳訊回應程式拒絕提供的序列，WCF 啟動者錯誤中新建立的序列。  
  
-   B1111： 如果`CreateSequence`不包含`Offer`項目，雙向 WCF 回應程式拒絕提供的序列來回應以`CreateSequenceRefused`錯誤。  
  
-   R1112：當兩個反向序列都是透過 `Offer` 機制建立時，`[address]` 端點參照之 `CreateSequenceResponse/Accept/AcksTo` 屬性的每個位元組必須完全符合 `CreateSequence` 訊息之目的 URI 的每個位元組。  
  
-   R1113：當兩個反向序列都是透過 `Offer` 機制建立時，從啟動器流向回應程式之雙邊序列上的所有訊息必須傳送至相同的端點參照。  
  
 WCF 會建立啟動器和回應程式之間的可靠工作階段使用 Ws-reliablemessaging。 WCF WS-SECURITY 與 Ws-reliablemessaging 實作會提供可靠工作階段的單向、 要求-回覆與全雙工訊息模式。 `Offer` 和 `CreateSequence` 上的 WS-ReliableMessaging `CreateSequenceResponse` 機制可讓您建立兩個相互關聯的反向序列，並提供適用於所有訊息端點的工作階段通訊協定。 WCF 有提供安全性保證，這類工作階段包含的工作階段完整性的端對端保護，因為它可以實際地確保適用於相同的合作對象的訊息都到達相同的目的地。 這麼做也可以針對應用程式訊息進行 "piggy-backing" 的序列認可作業。 因此，條件約束 R1102、 R1112 和 R1113 適用於 WCF。  
  
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
 WCF 使用`CloseSequence`和`CloseSequenceResponse`可信賴傳訊來源起始關機的訊息。 WCF 可信賴傳訊目的地不會啟始關閉，WCF 可信賴傳訊來源不支援可信賴傳訊目的地啟始關閉。 以下是適用的條件約束：  
  
-   B1201: WCF 可信賴傳訊來源一律傳送`CloseSequence`關閉順序訊息。  
  
-   B1202：可信賴傳訊來源會在傳送 `CloseSequence` 訊息之前，等候整個序列訊息的認可。  
  
-   B1203：可信賴傳訊來源一律包含選用的 `LastMsgNumber` 項目 (除非序列不包含訊息)。  
  
-   R1204：可信賴傳訊目的地不可以藉由傳送 `CloseSequence` 訊息來啟始關閉作業。  
  
-   B1205： 在收到`CloseSequence`訊息，WCF 可信賴傳訊來源會將序列視為不完整並傳送錯誤。  
  
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
 主要是使用 WCF`TerminateSequence/TerminateSequenceResponse`交握之後完成`CloseSequence/CloseSequenceResponse`交握。 WCF 可信賴傳訊目的地不會啟始終止和可信賴傳訊來源不支援可信賴傳訊目的地起始終止。 以下是適用的條件約束：  
  
-   B1301: WCF 啟動者只傳送`TerminateSequence`成功完成後的訊息`CloseSequence/CloseSequenceResponse`交握。  
  
-   R1302: WCF 驗證`LastMsgNumber`所有項目是否一致`CloseSequence`和`TerminateSequence`指定項目序列的訊息。 也就是說，`LastMsgNumber` 不是不存在於所有 `CloseSequence` 和 `TerminateSequence` 訊息上，就是存在於所有 `CloseSequence` 和 `TerminateSequence` 訊息上而且全部一樣。  
  
-   B1303：在 `TerminateSequence` 交握之後收到 `CloseSequence/CloseSequenceResponse` 訊息時，可信賴傳訊目的地會以 `TerminateSequenceResponse` 訊息來回應。 由於可信賴傳訊來源在傳送 `TerminateSequence` 訊息之前已經獲得最後的認可，因此可信賴傳訊目的地毫無疑問地知道序列已結束並立即回收資源。  
  
-   B1304： 在接收時`TerminateSequence`訊息之前`CloseSequence/CloseSequenceResponse`信號交換期間，WCF 可信賴傳訊目的地會以回應`TerminateSequenceResponse`訊息。 如果可信賴傳訊目的地判斷序列中沒有任何不一致的項目，則可信賴傳訊目的地會等候應用程式目的地指定的時間一到再回收資源，以便讓用戶端有機會接收最後的認可。 否則，可信賴傳訊目的地會立即回收資源並引發 `Faulted` 事件以向應用程式目的地指出序列是在不確定的情況下結束。  
  
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
  
-   B1401:WCF 會產生並存取序號大於`xs:long`的最大包含值，9223372036854775807。  
  
 `Sequence` 標頭的範例。  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a>要求認可  
 WCF 使用`AckRequested`標頭做為 keep-alive 機制。  
  
 `AckRequested` 標頭的範例。  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 WCF Ws-reliable 訊息所提供的序列認可使用的"piggy-back"機制。 以下是適用的條件約束：  
  
-   R1601： 當兩個反向序列會建立使用`Offer`機制，`SequenceAcknowledgement`標頭可能包含在傳送給預定收件者的任何應用程式訊息。 遠端端點必須能夠存取以 Piggyback 方式傳送的 `SequenceAcknowledgement` 標頭。  
  
-   B1602: WCF 不會產生`SequenceAcknowledgement`包含的標頭`Nack`項目。 WCF 會驗證每個`Nack`項目包含序號，但是另一方面會忽略`Nack`元素和值。  
  
 `SequenceAcknowledgement` 標頭的範例。  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a>WS-ReliableMessaging 錯誤  
 以下是適用於 WCF 實作的 WS-SECURITY 與 Ws-reliablemessaging 錯誤的條件約束的清單。 以下是適用的條件約束：  
  
-   B1701: WCF 不會產生`MessageNumberRollover`錯誤。  
  
-   B1702： 在 SOAP 1.2 中，當服務端點到達其連線限制，且無法處理新的連接，WCF 會產生巢狀`CreateSequenceRefused`錯誤子代碼`netrm:ConnectionLimitReached`，如下列範例所示。  
  
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
 由於 Ws-reliablemessaging 會使用 Ws-addressing，WCF WS-SECURITY 與 Ws-reliablemessaging 實作可能會產生並傳送 Ws-addressing 錯誤。 本章節涵蓋 WCF 明確產生並傳輸在 Ws-reliablemessaging 層 Ws-addressing 錯誤：  
  
-   B1801:WCF 會產生並傳輸`Message Addressing Header Required`當下列其中一項條件成立時，發生錯誤：  
  
    -   `CreateSequence`、`CloseSequence` 或 `TerminateSequence` 訊息缺少 `MessageId` 標頭。  
  
    -   `CreateSequence`、`CloseSequence` 或 `TerminateSequence` 訊息缺少 `ReplyTo` 標頭。  
  
    -   `CreateSequenceResponse`、`CloseSequenceResponse` 或 `TerminateSequenceResponse` 訊息缺少 `RelatesTo` 標頭。  
  
-   B1802:WCF 會產生並傳輸`Endpoint Unavailable`錯誤，表示沒有任何接聽的端點可以根據檢查結果中的定位標頭的順序進行處理`CreateSequence`訊息。  
  
## <a name="protocol-composition"></a>通訊協定組合  
  
### <a name="composition-with-ws-addressing"></a>與 WS-Addressing 組合  
 WCF 支援兩個版本的 Ws-addressing: Ws-addressing 2004/08 [WS-ADDR] 和 W3C Ws-addressing 1.0 建議 [WS-位址-核心] 和 [WS-位址-SOAP]。  
  
 儘管 WS-ReliableMessaging 規格只提到 WS-Addressing 2004/08，它並未限制要使用的 WS-Addressing 版本。 以下是適用於 WCF 的條件約束的清單：  
  
-   R2101：WS-Addressing 2004/08 和 WS-Addressing 1.0 皆可搭配 WS-Reliable 訊息一起使用。  
  
-   R2102：單一版本的 WS-Addressing 必須透過 `Offer` 機制，用在整個特定的 WS-ReliableMessaging 序列或是一對相關聯的反向序列上。  
  
### <a name="composition-with-soap"></a>與 SOAP 組合  
 WCF 支援 SOAP 1.1 和 SOAP 1.2 搭配 Ws-reliable 訊息一起使用。  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a>與 WS-Security 和 WS-SecureConversation 組合  
 WCF 會提供透過安全傳輸 (HTTPS)、 與 Ws-security 組合且組合 Ws-secure Conversation 與 WS-SECURITY 與 Ws-reliablemessaging 序列的保護。 WS-ReliableMessaging 1.1 通訊協定、WS-Security 1.1 和 WS-Secure Conversation 1.3 通訊協定應該一併使用。 以下是適用於 WCF 的條件約束的清單：  
  
-   R2301： 若要保護的個別訊息完整性除了 WS-SECURITY 與 Ws-reliablemessaging 序列的完整性與機密性，WCF 所要求，必須使用 Ws-secure Conversation。  
  
-   R2302:AWS-必須在建立了 Ws-reliablemessaging 序列前建立安全對話工作階段。  
  
-   R2303：如果 WS-ReliableMessaging 序列的存留期超過 WS-Secure Conversation 工作階段的存留期，則使用 WS-Secure Conversation 建立的 `SecurityContextToken` 必須透過對應的 WS-Secure Conversation 更新繫結來加以更新。  
  
-   B2304:WS-Ws-reliablemessaging 序列或是一對的相互關聯的反向順序永遠會繫結至單一的 Ws-secureconversation 工作階段。  
  
-   R2305： 與 Ws-secure Conversation 組合，當 WCF 回應要求`CreateSequence`訊息包含`wsse:SecurityTokenReference`項目和`wsrm:UsesSequenceSTR`標頭。  
  
 `UsesSequenceSTR` 標頭的範例。  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a>與 SSL/TLS 組合  
 WCF 不支援與 SSL/TLS 工作階段組合：  
  
-   B2401: WCF 不會產生`wsrm:UsesSequenceSSL`標頭。  
  
-   R2402： 可信賴傳訊啟動器必須傳送`CreateSequence`訊息`wsrm:UsesSequenceSSL`WCF 回應標頭。  
  
### <a name="composition-with-ws-policy"></a>與 WS-Policy 組合  
 WCF 支援兩個版本的 Ws-policy: Ws-policy 1.2 和 Ws-policy 1.5。  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a>WS-ReliableMessaging WS-Policy 判斷提示  
 WCF 使用 Ws-reliablemessaging Ws-policy 判斷提示`wsrm:RMAssertion`來描述端點功能。 以下是適用於 WCF 的條件約束的清單：  
  
-   B3001: WCF 附加`wsrmn:RMAssertion`Ws-policy 判斷提示來`wsdl:binding`項目。 WCF 同時支援附加至`wsdl:binding`和`wsdl:port`項目。  
  
-   B3002: WCF 永遠不會產生`wsp:Optional`標記。  
  
-   B3003： 存取時`wsrmp:RMAssertion`Ws-policy 判斷提示，WCF 會忽略`wsp:Optional`標記並將 WS-RM 原則視為強制性。  
  
-   R3004: WCF 無法組成與 SSL/TLS 工作階段，因為 WCF 不接受指定的原則`wsrmp:SequenceTransportSecurity`。  
  
-   B3005: WCF 一律產生`wsrmp:DeliveryAssurance`項目。  
  
-   B3006: WCF 一律指定`wsrmp:ExactlyOnce`傳遞保證。  
  
-   B3007: WCF 會產生並讀取下列 Ws-reliablemessaging 判斷提示的屬性並針對它們提供控制的 WCF`ReliableSessionBindingElement`:  
  
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
 WCF 會使用 WS-SECURITY 與 Ws-reliablemessaging 擴充性提供選擇性額外更加嚴格控制序列訊息流量。  
  
 藉由設定已啟用流量控制`ReliableSessionBindingElement`的`FlowControlEnabled``boolean`屬性`true`。 以下是適用於 WCF 的條件約束的清單：  
  
-   B4001： 啟用可信賴傳訊流量控制時，WCF 會產生`netrm:BufferRemaining`中的項目擴充性項目`SequenceAcknowledgement`標頭，如下列範例所示。  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B4002： 即使啟用了可信賴傳訊流量控制，WCF 不要求`netrm:BufferRemaining`中的項目`SequenceAcknowledgement`標頭。  
  
-   B4003: WCF 可信賴傳訊目的地會使用`netrm:BufferRemaining`表示多少新訊息可以緩衝。  
  
-   B4004:When 可信賴傳訊流量控制時，WCF 可信賴傳訊來源會使用的值`netrm:BufferRemaining`節流訊息傳輸。  
  
-   B4005: WCF 會產生`netrm:BufferRemaining`整數值介於 0 到 4096 （含)，並讀取介於 0 的整數值和`xs:int`的`maxInclusive`值 214748364 （含)。  
  
## <a name="message-exchange-patterns"></a>訊息交換模式  
 當不同訊息交換模式使用 Ws-reliablemessaging 時，本節會說明 WCF 的行為。 在每個訊息交換模式中，會考慮下列兩種部署案例：  
  
-   不可定址的啟動器：啟動器位於防火牆後方，回應程式只能透過 HTTP 回應將訊息傳送至啟動器。  
  
-   可定址的啟動器：可將 HTTP 要求同時傳送給啟動器與回應程式，亦即可建立兩個反向 HTTP 連線。  
  
### <a name="one-way-non-addressable-initiator"></a>單向、不可定址啟動器  
  
#### <a name="binding"></a>繫結  
 WCF 提供透過一個 HTTP 通道上使用一個序列的單向訊息交換模式。 WCF 會使用 HTTP 要求來傳送所有訊息從啟動器至回應並透過 HTTP 回應來都傳送所有訊息從回應者至啟動器。  
  
#### <a name="createsequence-exchange"></a>CreateSequence 交換  
 WCF 啟動者傳送出去`CreateSequence`訊息沒有`Offer`HTTP 要求的項目，並且預期會`CreateSequenceResponse`HTTP 回應的訊息。 WCF 回應程式會建立序列，並將傳送`CreateSequenceResponse`訊息沒有`Accept`HTTP 回應上的項目。  
  
#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 WCF 啟動器會處理回覆訊息的認可所有除了`CreateSequence`訊息與錯誤訊息。 WCF 回應程式一律會傳輸至所有序列的 HTTP 回應將獨立認可和`AckRequested`訊息。  
  
#### <a name="closesequence-exchange"></a>CloseSequence 交換  
 WCF 啟動者傳送出去`CloseSequence`HTTP 要求訊息，並且預期會`CreateSequenceResponse`HTTP 回應的訊息。 WCF 回應程式會透過`CloseSequenceResponse`HTTP 回應的訊息。  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence 交換  
 WCF 啟動者傳送出去`TerminateSequence`HTTP 要求訊息，並且預期會`TerminateSequenceResponse`HTTP 回應的訊息。 WCF 回應程式會透過`TerminateSequenceResponse`HTTP 回應的訊息。  
  
### <a name="one-way-addressable-initiator"></a>單向、可定址啟動器  
  
#### <a name="binding"></a>繫結  
 WCF，提供單向訊息交換模式使用一個序列的其中一個傳入與一個傳出 HTTP 通道。 WCF 會使用 HTTP 要求來傳送所有訊息。 所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。  
  
#### <a name="createsequence-exchange"></a>CreateSequence 交換  
 WCF 啟動者傳送出去`CreateSequence`訊息沒有`Offer`HTTP 要求的項目。 WCF 回應程式會建立序列，並將傳送`CreateSequenceResponse`訊息沒有`Accept`HTTP 要求的項目。  
  
### <a name="duplex-addressable-initiator"></a>雙工、可定址啟動器  
  
#### <a name="binding"></a>繫結  
 WCF 提供完全非同步、 雙向訊息交換模式使用兩個序列在一個傳入與一個傳出 HTTP 通道。 在有限的情況下，此訊息交換模式可與 `Request/Reply`、`Addressable` 啟動器訊息交換模式混合使用。 WCF 會使用 HTTP 要求來傳送所有訊息。 所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。  
  
#### <a name="createsequence-exchange"></a>CreateSequence 交換  
 WCF 啟動者傳送出去`CreateSequence`訊息`Offer`HTTP 要求的項目。 WCF 回應程式會確保`CreateSequence`具有`Offer`項目，然後建立序列，並會傳輸`CreateSequenceResponse`訊息`Accept`項目。  
  
#### <a name="sequence-lifetime"></a>序列存留期  
 WCF 會將兩個序列視為一個全雙工工作階段。  
  
 在產生可挑剔某個序列的錯誤，WCF 會預期遠端端點將同時挑剔兩個序列。 在讀取可挑剔某個序列的錯誤，WCF 會挑剔兩個序列。  
  
 WCF 可以關閉其傳出序列並繼續處理其傳入序列的訊息。 相反地，WCF 可以處理傳入序列的關閉作業並繼續傳送其傳出序列的訊息。  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a>要求-回覆和單向、不可定址啟動器  
  
#### <a name="binding"></a>繫結  
 WCF 提供單向和要求-回覆訊息交換模式使用兩個序列超過一個 HTTP 通道。 WCF 會使用 HTTP 要求來傳送所有訊息從啟動器至回應並透過 HTTP 回應來都傳送所有訊息從回應者至啟動器。  
  
#### <a name="createsequence-exchange"></a>CreateSequence 交換  
 WCF 啟動者傳送出去`CreateSequence`訊息`Offer`HTTP 要求的項目，並且預期會`CreateSequenceResponse`HTTP 回應的訊息。 WCF 回應程式會建立序列，並將傳送`CreateSequenceResponse`訊息`Accept`HTTP 回應上的項目。  
  
#### <a name="one-way-message"></a>單向訊息  
 若要成功完成單向訊息交換，WCF 啟動器會傳送要求序列訊息的 HTTP 要求並接收獨立`SequenceAcknowledgement`HTTP 回應的訊息。 `SequenceAcknowledgement` 必須認可傳送的訊息。  
  
 WCF 回應可能回覆的認可、 錯誤或是內含空本文與 HTTP 202 狀態碼的回應要求。  
  
#### <a name="two-way-messages"></a>雙向訊息  
 若要成功完成雙向訊息交換通訊協定，WCF 啟動者傳送要求序列訊息的 HTTP 要求和接收 HTTP 回應上的回覆序列訊息。 回應中必須包含認可傳輸之要求序列訊息的 `SequenceAcknowledgement`。  
  
 WCF 回應可能回應至要求的應用程式回覆、 錯誤或是內含空本文與 HTTP 202 狀態碼的回應。  
  
 由於單向訊息與應用程式回覆時機的緣故，要求序列訊息的序號與回應訊息的序號彼此並未互相關聯。  
  
#### <a name="retrying-replies"></a>重試回覆  
 WCF 仰賴 HTTP 要求-回覆相互關聯來執行雙向訊息交換通訊協定相互關聯。 因為這個緣故，WCF 啟動器不會停止在認可要求序列訊息時，重試要求序列訊息，但而是當 HTTP 回應執行`SequenceAcknowledgement`，應用程式回覆或錯誤。 WCF 回應重試回覆相互關聯之要求的 HTTP 回應上的回覆。  
  
#### <a name="closesequence-exchange"></a>CloseSequence 交換  
 收到之後所有回覆序列訊息與認可所有單向要求序列訊息時，WCF 啟動者傳送出去`CloseSequence`HTTP 要求將要求序列訊息，並且預期會`CloseSequenceResponse`HTTP 回應。  
  
 隱含地關閉要求序列會一併關閉回覆序列。 這表示 WCF 啟動器包含回覆序列的最終`SequenceAcknowledgement`上`CloseSequence`訊息，而且回覆序列沒有`CloseSequence`exchange。  
  
 WCF 回應可確保所有回覆都已認可，並將傳送`CloseSequenceResponse`HTTP 回應的訊息。  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence 交換  
 在收到後`CloseSequenceResponse`傳送出去的訊息，WCF 啟動器`TerminateSequence`HTTP 要求將要求序列訊息，並且預期會`TerminateSequenceResponse`HTTP 回應。  
  
 就像 `CloseSequence` 交換一樣，終止要求序列會隱含地終止回覆序列。 這表示 WCF 啟動器包含回覆序列的最終`SequenceAcknowledgement`上`TerminateSequence`訊息，而且回覆序列沒有`TerminateSequence`exchange。  
  
 WCF 回應程式會透過`TerminateSequenceResponse`HTTP 回應的訊息。  
  
### <a name="requestreply-addressable-initiator"></a>要求/回覆、可定址啟動器  
  
#### <a name="binding"></a>繫結  
 WCF 提供要求-回覆訊息交換模式使用兩個序列在一個傳入與一個傳出 HTTP 通道。 在有限的情況下，此訊息交換模式可與 `Duplex, Addressable` 啟動器訊息交換模式混合使用。 WCF 會使用 HTTP 要求來傳送所有訊息。 所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。  
  
#### <a name="createsequence-exchange"></a>CreateSequence 交換  
 WCF 啟動者傳送出去`CreateSequence`訊息`Offer`HTTP 要求的項目。 WCF 回應程式會確保`CreateSequence`具有`Offer`項目然後建立序列，並會傳輸`CreateSequenceResponse`訊息`Accept`項目。  
  
#### <a name="requestreply-correlation"></a>要求/回覆相互關聯  
 下列會套用到所有相互關聯的要求及回覆：  
  
-   WCF 可確保所有應用程式要求訊息都帶有`ReplyTo`端點參考和`MessageId`。  
  
-   WCF 適用於每個應用程式要求訊息的本機端點參照`ReplyTo`。 啟動器的本機端點參照是 `CreateSequence` 訊息的 `ReplyTo`，而回應程式的本機端點參照則是 `CreateSequence` 訊息的 `To`。  
  
-   WCF 可確保傳入的要求訊息都帶有`MessageId`和`ReplyTo`。  
  
-   WCF 可確保`ReplyTo`先前定義的所有應用程式要求訊息的端點參照 URI 符合本機端點參照。  
  
-   WCF 可確保所有回覆都帶有正確`RelatesTo`和`To`下列標頭`wsa`要求/回覆相互關聯的規則。

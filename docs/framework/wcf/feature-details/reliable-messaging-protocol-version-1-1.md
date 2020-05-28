---
title: Reliable Messaging Protocol 1.1 版
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: ad0a77842c10965749eab4e76bb123938e07e9d5
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144717"
---
# <a name="reliable-messaging-protocol-version-11"></a>Reliable Messaging Protocol 1.1 版

本主題涵蓋使用 HTTP 傳輸進行交互操作所需之 WS-RELIABLEMESSAGING 2007 （1.1 版）通訊協定的 Windows Communication Foundation （WCF）執行詳細資料。 WCF 遵循 WS-RELIABLEMESSAGING 規格與本主題所述的條件約束和說明。 請注意，ws-reliablemessaging 1.1 通訊協定是從 .NET Framework 3.5 開始實行。

Ws-reliablemessaging 2 月2007通訊協定是在 WCF 中由所執行 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> 。

為了方便起見，本主題將使用下列角色：

- 啟動器：啟動 WS-Reliable 訊息序列建立作業的用戶端。

- 回應程式：接收啟動器要求的服務。

 本文件會使用下表的前置詞和命名空間。

|前置詞|命名空間|
|-|-|
|wsrm|`http://docs.oasis-open.org/ws-rx/wsrm/200702`|
|netrm|`http://schemas.microsoft.com/ws/2006/05/rm`|
|s|`http://www.w3.org/2003/05/soap-envelope`|
|wsa|`http://schemas.xmlsoap.org/ws/2005/08/addressing`|
|wsse|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd`|
|wsrmp|`http://docs.oasis-open.org/ws-rx/wsrmp/200702`|
|netrmp|`http://schemas.microsoft.com/ws-rx/wsrmp/200702`|
|wsp|(WS-Policy 1.2 或 WS-Policy 1.5)|

## <a name="messaging"></a>Messaging (傳訊)

### <a name="sequence-creation"></a>建立序列

WCF 會 `CreateSequence` `CreateSequenceResponse` 執行和訊息，以建立可靠的訊息順序。 以下是適用的條件約束：

- B1101： WCF 啟動器會使用與 `CreateSequence` 訊息的、和相同的端點 `ReplyTo` 參考 `AcksTo` `Offer/Endpoint` 。

- R1102：`AcksTo` 訊息中的 `ReplyTo`、`Offer/Endpoint` 和 `CreateSequence` 端點參照必須具有包含相同字串表示的位址值以符合八位元規格。

  - WCF 回應程式 `AcksTo` 會在建立序列之前，確認、 `ReplyTo` 和端點參考的 URI 部分 `Endpoint` 都相同。

- R1103：`AcksTo` 訊息中的 `ReplyTo`、`Offer/Endpoint` 和 `CreateSequence` 端點參照應該具有相同的參照參數集合。

  - WCF 不會強制執行，但會假設上的、和端點參考的參考參數 `AcksTo` `ReplyTo` `Offer/Endpoint` `CreateSequence` 完全相同，並且使用來自 `ReplyTo` 端點參考的參考參數來取得通知和反向序列訊息。

- B1104： WCF 啟動器不會 `Expires` `Offer/Expires` 在訊息中產生選擇性或元素 `CreateSequence` 。

- B1105：存取訊息時 `CreateSequence` ，WCF 回應者會使用專案 `Expires` 中的值 `CreateSequence` 做為 `Expires` 元素中的值 `CreateSequenceResponse` 。 否則，WCF 回應程式會讀取並忽略 `Expires` 和 `Offer/Expires` 值。

- B1106：存取訊息時 `CreateSequenceResponse` ，WCF 啟動器會讀取選擇性值， `Expires` 但不會使用它。

- B1107： WCF 啟動器和回應程式一律會 `IncompleteSequenceBehavior` 在和專案中產生選擇性元素 `CreateSequence/Offer` `CreateSequenceResponse` 。

- B1108： WCF 只會使用 `DiscardFollowingFirstGap` `NoDiscard` 元素中的和值 `IncompleteSequenceBehavior` 。

  - WS-ReliableMessaging 會使用 `Offer` 機制來建立兩個反向關聯序列以形成工作階段。

- B1109：如果 `CreateSequence` 包含專案 `Offer` ，則 WCF 回應程式會透過以不含專案的來回應，來拒絕所提供的序列 `CreateSequenceResponse` `Accept` 。

- B1110：如果可靠的訊息回應程式拒絕所提供的順序，WCF 啟動器會將新建立的序列錯誤。

- B1111：如果不 `CreateSequence` 包含 `Offer` 元素，雙向 WCF 回應程式會藉由回應錯誤來拒絕提供的序列 `CreateSequenceRefused` 。

- R1112：當兩個反向序列都是透過 `Offer` 機制建立時，`[address]` 端點參照之 `CreateSequenceResponse/Accept/AcksTo` 屬性的每個位元組必須完全符合 `CreateSequence` 訊息之目的 URI 的每個位元組。

- R1113：當兩個反向序列都是透過 `Offer` 機制建立時，從啟動器流向回應程式之雙邊序列上的所有訊息必須傳送至相同的端點參照。

WCF 使用 WS-RELIABLEMESSAGING 在啟動器和回應程式之間建立可靠的會話。 WCF ws-reliablemessaging 實行會針對單向、要求-回復與全雙工訊息模式提供可靠的會話。 `Offer` 和 `CreateSequence` 上的 WS-ReliableMessaging `CreateSequenceResponse` 機制可讓您建立兩個相互關聯的反向序列，並提供適用於所有訊息端點的工作階段通訊協定。 因為 WCF 會針對這類會話提供安全性保證，包括會話完整性的端對端保護，所以確保適用于同一方的訊息會到達相同的目的地。 這麼做也可以針對應用程式訊息進行 "piggy-backing" 的序列認可作業。 因此，條件約束 R1102、R1112 和 R1113 適用于 WCF。

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

WCF 會使用 `CloseSequence` 和 `CloseSequenceResponse` 訊息來進行可靠的訊息來源起始的關機。 WCF 可靠訊息目的地不會起始關機，而且 WCF 可靠的訊息來源不支援可靠的訊息目的地起始的關閉。 以下是適用的條件約束：

- B1201： WCF 可靠的訊息來源一律會傳送一 `CloseSequence` 則訊息，以關閉順序。

- B1202：可信賴傳訊來源會在傳送 `CloseSequence` 訊息之前，等候整個序列訊息的認可。

- B1203：可信賴傳訊來源一律包含選用的 `LastMsgNumber` 項目 (除非序列不包含訊息)。

- R1204：可信賴傳訊目的地不可以藉由傳送 `CloseSequence` 訊息來啟始關閉作業。

- B1205：接收訊息時 `CloseSequence` ，WCF 可靠訊息來源會將序列視為不完整，並傳送錯誤。

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
```

範例 `CloseSequenceResponse` 訊息：

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

### <a name="sequence-termination"></a>終止序列

WCF 在 `TerminateSequence/TerminateSequenceResponse` 完成交握之後，主要會使用交握 `CloseSequence/CloseSequenceResponse` 。 WCF 可靠訊息目的地不會起始終止，而且可靠的訊息來源不支援可靠的訊息目的地起始的終止。 以下是適用的條件約束：

- B1301： WCF 啟動器只會在 `TerminateSequence` 成功完成交握之後傳送訊息 `CloseSequence/CloseSequenceResponse` 。

- R1302： WCF 會驗證專案在 `LastMsgNumber` 指定序列的所有和訊息中都是一致的 `CloseSequence` `TerminateSequence` 。 也就是說，`LastMsgNumber` 不是不存在於所有 `CloseSequence` 和 `TerminateSequence` 訊息上，就是存在於所有 `CloseSequence` 和 `TerminateSequence` 訊息上而且全部一樣。

- B1303：在 `TerminateSequence` 交握之後收到 `CloseSequence/CloseSequenceResponse` 訊息時，可信賴傳訊目的地會以 `TerminateSequenceResponse` 訊息來回應。 由於可信賴傳訊來源在傳送 `TerminateSequence` 訊息之前已經獲得最後的認可，因此可信賴傳訊目的地毫無疑問地知道序列已結束並立即回收資源。

- B1304：在 `TerminateSequence` 交握之前收到訊息時 `CloseSequence/CloseSequenceResponse` ，WCF 可靠的訊息目的地會以訊息來回應 `TerminateSequenceResponse` 。 如果可信賴傳訊目的地判斷序列中沒有任何不一致的項目，則可信賴傳訊目的地會等候應用程式目的地指定的時間一到再回收資源，以便讓用戶端有機會接收最後的認可。 否則，可信賴傳訊目的地會立即回收資源並引發 `Faulted` 事件以向應用程式目的地指出序列是在不確定的情況下結束。

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
```

範例 `TerminateSequenceResponse` 訊息：

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

### <a name="sequences"></a>序列

下列清單列出適用於序列的條件約束：

- B1401： WCF 會產生並存取不超過 `xs:long` 最大內含值9223372036854775807的序號。

`Sequence` 標頭的範例。

```xml
<wsrm:Sequence s:mustUnderstand="1">
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:MessageNumber>1</wsrm:MessageNumber>
</wsrm:Sequence>
```

### <a name="request-acknowledgement"></a>要求認可

WCF 會使用 `AckRequested` 標頭做為 keep-alive 機制。

`AckRequested` 標頭的範例。

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement

WCF 會針對 WS-TRUST 訊息中提供的順序通知使用「piggy-back 後」機制。 以下是適用的條件約束：

- R1601：當使用此機制來建立兩個反向序列時 `Offer` ， `SequenceAcknowledgement` 標頭可能會包含在傳送給預定收件者的任何應用程式訊息中。 遠端端點必須能夠存取以 Piggyback 方式傳送的 `SequenceAcknowledgement` 標頭。

- B1602： WCF 不會產生 `SequenceAcknowledgement` 包含元素的標頭 `Nack` 。 WCF 會驗證每個 `Nack` 元素都包含序號，否則會忽略 `Nack` 元素和值。

 `SequenceAcknowledgement` 標頭的範例。

```xml
<wsrm:SequenceAcknowledgement>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>
</wsrm:SequenceAcknowledgement>
```

### <a name="ws-reliablemessaging-faults"></a>WS-ReliableMessaging 錯誤

以下是適用于 WS-RELIABLEMESSAGING 錯誤之 WCF 執行條件約束的清單。 以下是適用的條件約束：

- B1701： WCF 不會產生 `MessageNumberRollover` 錯誤。

- B1702： Over SOAP 1.2，當服務端點達到其連線限制，而且無法處理新的連接時，WCF 會產生一個嵌套 `CreateSequenceRefused` 錯誤子代碼， `netrm:ConnectionLimitReached` 如下列範例所示。

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

因為 ws-reliablemessaging 使用 WS-ADDRESSING，所以 WCF ws-reliablemessaging 執行可能會產生並傳輸 WS-ADDRESSING 錯誤。 本節涵蓋 WCF 在 ws-reliablemessaging 層明確產生和傳輸的 WS-ADDRESSING 錯誤：

- B1801： `Message Addressing Header Required` 當下列其中一項為真時，WCF 會產生並傳輸錯誤：

  - `CreateSequence`、`CloseSequence` 或 `TerminateSequence` 訊息缺少 `MessageId` 標頭。

  - `CreateSequence`、`CloseSequence` 或 `TerminateSequence` 訊息缺少 `ReplyTo` 標頭。

  - `CreateSequenceResponse`、`CloseSequenceResponse` 或 `TerminateSequenceResponse` 訊息缺少 `RelatesTo` 標頭。

- B1802： WCF 會產生並傳輸 `Endpoint Unavailable` 錯誤，指出沒有任何接聽的端點可以根據訊息中的定址標頭檢查來處理序列 `CreateSequence` 。

## <a name="protocol-composition"></a>通訊協定組合

### <a name="composition-with-ws-addressing"></a>與 WS-Addressing 組合

WCF 支援兩種 WS-ADDRESSING 版本： WS-ADDRESSING 2004/08 [WS-ATOMICTRANSACTION] 和 W3C WS-ADDRESSING 1.0 建議 [WS-ADDRESSING-CORE] 和 [WS-ATOMICTRANSACTION-SOAP]。

儘管 WS-ReliableMessaging 規格只提到 WS-Addressing 2004/08，它並未限制要使用的 WS-Addressing 版本。 以下是適用于 WCF 的條件約束清單：

- R2101：WS-Addressing 2004/08 和 WS-Addressing 1.0 皆可搭配 WS-Reliable 訊息一起使用。

- R2102：單一版本的 WS-Addressing 必須透過 `Offer` 機制，用在整個特定的 WS-ReliableMessaging 序列或是一對相關聯的反向序列上。

### <a name="composition-with-soap"></a>與 SOAP 組合

WCF 支援搭配使用 SOAP 1.1 和 SOAP 1.2 與 WS-可靠的訊息。

### <a name="composition-with-ws-security-and-ws-secureconversation"></a>與 WS-Security 和 WS-SecureConversation 組合

WCF 藉由使用安全傳輸（HTTPS）、以 WS-MANAGEMENT 撰寫，以及與 WS-安全交談組合，來提供 WS-RELIABLEMESSAGING 序列的保護。 WS-ReliableMessaging 1.1 通訊協定、WS-Security 1.1 和 WS-Secure Conversation 1.3 通訊協定應該一併使用。 以下是適用于 WCF 的條件約束清單：

- R2301：若要保護 ws-reliablemessaging 序列的完整性，以及個別訊息的完整性和機密性，WCF 需要使用 WS-安全交談。

- R2302：在建立 WS-ReliableMessaging 序列之前，必須先建立 WS-Secure Conversation 工作階段。

- R2303：如果 WS-ReliableMessaging 序列的存留期超過 WS-Secure Conversation 工作階段的存留期，則使用 WS-Secure Conversation 建立的 `SecurityContextToken` 必須透過對應的 WS-Secure Conversation 更新繫結來加以更新。

- B2304：WS-ReliableMessaging 序列或是一對相互關聯的反向序列一律繫結至單一 WS-SecureConversation 工作階段。

- R2305：以 WS-安全對話撰寫時，WCF 回應者會要求 `CreateSequence` 訊息必須包含 `wsse:SecurityTokenReference` 元素和 `wsrm:UsesSequenceSTR` 標頭。

 `UsesSequenceSTR` 標頭的範例。

```xml
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>
```

### <a name="composition-with-ssltls-sessions"></a>與 SSL/TLS 組合

WCF 不支援使用 SSL/TLS 會話撰寫：

- B2401： WCF 不會產生 `wsrm:UsesSequenceSSL` 標頭。

- R2402：可靠的訊息啟動器不能傳送 `CreateSequence` 具有 `wsrm:UsesSequenceSSL` 標頭的訊息給 WCF 回應程式。

### <a name="composition-with-ws-policy"></a>與 WS-Policy 組合

WCF 支援兩種版本的 WS 原則： WS-Policy 1.2 和 WS-Policy 1.5。

## <a name="ws-reliablemessaging-ws-policy-assertion"></a>WS-ReliableMessaging WS-Policy 判斷提示

WCF 使用 WS-RELIABLEMESSAGING WS-原則判斷提示 `wsrm:RMAssertion` 來描述端點功能。 以下是適用于 WCF 的條件約束清單：

- B3001： WCF 會 `wsrmn:RMAssertion` 將 WS-原則判斷提示附加至 `wsdl:binding` 元素。 WCF 同時支援 `wsdl:binding` 和元素的附件 `wsdl:port` 。

- B3002： WCF 永遠不會產生 `wsp:Optional` 標記。

- B3003：存取 `wsrmp:RMAssertion` WS-Policy 判斷提示時，WCF 會忽略 `wsp:Optional` 標記並將 ws-rm 原則視為強制。

- R3004：因為 WCF 不是以 SSL/TLS 會話撰寫，所以 WCF 不接受指定的原則 `wsrmp:SequenceTransportSecurity` 。

- B3005： WCF 一律會產生 `wsrmp:DeliveryAssurance` 元素。

- B3006： WCF 一律會指定 `wsrmp:ExactlyOnce` 傳遞保證。

- B3007： WCF 會產生並讀取 WS-RELIABLEMESSAGING 判斷提示的下列屬性，並在 WCF 上提供控制 `ReliableSessionBindingElement` ：

  - `netrmp:InactivityTimeout`

  - `netrmp:AcknowledgementInterval`

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

WCF 使用 WS-RELIABLEMESSAGING 擴充性，對序列訊息流程提供選擇性的額外更緊密的控制。

藉由將屬性設定為，即可啟用流量控制 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> `true` 。 以下是適用于 WCF 的條件約束清單：

- B4001 一旦：當可靠的訊息流量控制啟用時，WCF 會 `netrm:BufferRemaining` 在標頭的專案擴充性中產生元素 `SequenceAcknowledgement` ，如下列範例所示。

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="1" Lower="1"/>
    <netrm:BufferRemaining>8</netrm:BufferRemaining>
  </wsrm:SequenceAcknowledgement>
  ```

- B4002：即使啟用可靠的訊息流程式控制制，WCF 也不需要 `netrm:BufferRemaining` 標頭中的元素 `SequenceAcknowledgement` 。

- B4003： WCF 可靠的訊息目的地 `netrm:BufferRemaining` 會使用來指出它可以緩衝處理的新訊息數目。

- B4004：當可靠的訊息流量控制啟用時，WCF 可靠的訊息來源會使用的值 `netrm:BufferRemaining` 來節流訊息傳輸。

- B4005： WCF 會產生 `netrm:BufferRemaining` 介於0到4096（含）之間的整數值，並讀取介於0和 `xs:int` 的 `maxInclusive` 值214748364（含）之間的整數值。

## <a name="message-exchange-patterns"></a>訊息交換模式

本節說明在不同的訊息交換模式使用 WS-RELIABLEMESSAGING 時，WCF 的行為。 在每個訊息交換模式中，會考慮下列兩種部署案例：

- 不可定址的啟動器：啟動器位於防火牆後方，回應程式只能透過 HTTP 回應將訊息傳送至啟動器。

- 可定址的啟動器：可將 HTTP 要求同時傳送給啟動器與回應程式，亦即可建立兩個反向 HTTP 連線。

### <a name="one-way-non-addressable-initiator"></a>單向、不可定址啟動器

#### <a name="binding"></a>繫結

WCF 會在一個 HTTP 通道上使用一個序列來提供單向的訊息交換模式。 WCF 使用 HTTP 要求將所有訊息從啟動器傳送至回應程式，而 HTTP 回應則將所有訊息從回應傳送至啟動器。

#### <a name="createsequence-exchange"></a>CreateSequence 交換

WCF 啟動器會透過 `CreateSequence` HTTP 要求來傳送沒有元素的訊息 `Offer` ，並預期 `CreateSequenceResponse` HTTP 回應上的訊息。 WCF 回應程式會建立序列，並在 `CreateSequenceResponse` `Accept` HTTP 回應上傳送沒有元素的訊息。

#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement

除了訊息和錯誤訊息以外，WCF 啟動器會處理所有訊息回復的 `CreateSequence` 通知。 WCF 回應者一律會將 HTTP 回應上的獨立認可傳送至所有序列和 `AckRequested` 訊息。

#### <a name="closesequence-exchange"></a>CloseSequence 交換

WCF 啟動器會 `CloseSequence` 在 HTTP 要求上傳輸訊息，並預期 `CreateSequenceResponse` HTTP 回應上的訊息。 WCF 回應程式會將 `CloseSequenceResponse` 訊息傳送至 HTTP 回應。

#### <a name="terminatesequence-exchange"></a>TerminateSequence 交換

WCF 啟動器會 `TerminateSequence` 在 HTTP 要求上傳輸訊息，並預期 `TerminateSequenceResponse` HTTP 回應上的訊息。 WCF 回應程式會將 `TerminateSequenceResponse` 訊息傳送至 HTTP 回應。

### <a name="one-way-addressable-initiator"></a>單向、可定址啟動器

#### <a name="binding"></a>繫結

WCF 會在一個輸入和一個傳出 HTTP 通道上使用一個序列來提供單向訊息交換模式。 WCF 會使用 HTTP 要求來傳送所有訊息。 所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。

#### <a name="createsequence-exchange"></a>CreateSequence 交換

WCF 啟動器會透過 `CreateSequence` HTTP 要求來傳送沒有元素的訊息 `Offer` 。 WCF 回應程式會建立序列，並 `CreateSequenceResponse` `Accept` 在 HTTP 要求上傳送不含任何元素的訊息。

### <a name="duplex-addressable-initiator"></a>雙工、可定址啟動器

#### <a name="binding"></a>繫結

WCF 會在一個輸入和一個傳出 HTTP 通道上使用兩個序列，以提供完全非同步、雙向的訊息交換模式。 在有限的情況下，此訊息交換模式可與 `Request/Reply`、`Addressable` 啟動器訊息交換模式混合使用。 WCF 會使用 HTTP 要求來傳送所有訊息。 所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。

#### <a name="createsequence-exchange"></a>CreateSequence 交換

WCF 啟動器會 `CreateSequence` 使用 HTTP 要求上的專案來傳輸訊息 `Offer` 。 WCF 回應程式可確保 `CreateSequence` 具有 `Offer` 元素，然後建立序列並使用專案來傳輸 `CreateSequenceResponse` 訊息 `Accept` 。

#### <a name="sequence-lifetime"></a>序列存留期

WCF 會將這兩個序列視為一個全雙工會話。

在產生錯誤一個序列的錯誤時，WCF 會預期遠端端點會同時容錯這兩個序列。 當讀取錯誤發生一系列的錯誤時，WCF 會同時錯誤這兩個序列。

WCF 可以關閉其輸出序列，並繼續處理其輸入序列的訊息。 相反地，WCF 可以處理輸入序列的關閉，並繼續以輸出序列來傳送訊息。

### <a name="request-reply-and-one-way-non-addressable-initiator"></a>要求-回覆和單向、不可定址啟動器

#### <a name="binding"></a>繫結

WCF 透過在一個 HTTP 通道上使用兩個序列的方式，提供單向和要求-回復訊息交換模式。 WCF 使用 HTTP 要求將所有訊息從啟動器傳送至回應程式，而 HTTP 回應則將所有訊息從回應傳送至啟動器。

#### <a name="createsequence-exchange"></a>CreateSequence 交換

WCF 啟動器會 `CreateSequence` 使用 HTTP 要求上的專案來傳輸訊息 `Offer` ，並預期 `CreateSequenceResponse` HTTP 回應上的訊息。 WCF 回應程式會建立序列，並透過 `CreateSequenceResponse` HTTP 回應的元素來傳輸訊息 `Accept` 。

#### <a name="one-way-message"></a>單向訊息

為了成功完成單向訊息交換，WCF 啟動器會在 HTTP 要求上傳輸要求序列訊息，並 `SequenceAcknowledgement` 在 HTTP 回應上接收獨立的訊息。 `SequenceAcknowledgement` 必須認可傳送的訊息。

WCF 回應者可以使用通知、錯誤或具有空白本文和 HTTP 202 狀態碼的回應來回複要求。

#### <a name="two-way-messages"></a>雙向訊息

為了成功完成雙向訊息交換通訊協定，WCF 啟動器會在 HTTP 要求上傳輸要求序列訊息，並在 HTTP 回應上接收回複序列訊息。 回應中必須包含認可傳輸之要求序列訊息的 `SequenceAcknowledgement`。

WCF 回應者可以透過應用程式回復、錯誤或具有空白本文的回應，以及 HTTP 202 狀態碼來回複要求。

由於單向訊息與應用程式回覆時機的緣故，要求序列訊息的序號與回應訊息的序號彼此並未互相關聯。

#### <a name="retrying-replies"></a>重試回覆

WCF 依賴雙向訊息交換通訊協定相互關聯的 HTTP 要求-回復相互關聯。 因此，在認可要求序列訊息時，WCF 啟動器不會停止重試要求序列訊息，而是當 HTTP 回應攜帶 `SequenceAcknowledgement` 、應用程式回復或錯誤時， WCF 回應程式會在與回復相互關聯之要求的 HTTP 回應上重試回復。

#### <a name="closesequence-exchange"></a>CloseSequence 交換

收到所有單向要求順序訊息的所有回復順序訊息和通知之後，WCF 啟動器會針對 `CloseSequence` HTTP 要求傳送要求序列的訊息，並在 `CloseSequenceResponse` HTTP 回應上要求。

隱含地關閉要求序列會一併關閉回覆序列。 這表示 WCF 啟動器會在訊息上包含回復序列的最終 `SequenceAcknowledgement` `CloseSequence` ，而且回復順序沒有 `CloseSequence` 交換。

WCF 回應程式可確保所有回復都已認可，並將訊息傳送至 `CloseSequenceResponse` HTTP 回應。

#### <a name="terminatesequence-exchange"></a>TerminateSequence 交換

接收訊息之後 `CloseSequenceResponse` ，WCF 啟動器會針對 `TerminateSequence` HTTP 要求傳送要求序列的訊息，並在 `TerminateSequenceResponse` HTTP 回應上要求。

就像 `CloseSequence` 交換一樣，終止要求序列會隱含地終止回覆序列。 這表示 WCF 啟動器會在訊息上包含回復序列的最終 `SequenceAcknowledgement` `TerminateSequence` ，而且回復順序沒有 `TerminateSequence` 交換。

WCF 回應程式會將 `TerminateSequenceResponse` 訊息傳送至 HTTP 回應。

### <a name="requestreply-addressable-initiator"></a>要求/回覆、可定址啟動器

#### <a name="binding"></a>繫結

WCF 會在一個輸入和一個傳出 HTTP 通道上使用兩個序列，以提供要求-回復訊息交換模式。 在有限的情況下，此訊息交換模式可與 `Duplex, Addressable` 啟動器訊息交換模式混合使用。 WCF 會使用 HTTP 要求來傳送所有訊息。 所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。

#### <a name="createsequence-exchange"></a>CreateSequence 交換

WCF 啟動器會 `CreateSequence` 使用 HTTP 要求上的專案來傳輸訊息 `Offer` 。 WCF 回應程式可確保 `CreateSequence` 具有元素， `Offer` 然後建立序列並使用專案來傳輸 `CreateSequenceResponse` 訊息 `Accept` 。

#### <a name="requestreply-correlation"></a>要求/回覆相互關聯

下列會套用到所有相互關聯的要求及回覆：

- WCF 可確保所有應用程式要求訊息都有 `ReplyTo` 端點參考和 `MessageId` 。

- WCF 會將本機端點參考套用為每個應用程式要求訊息的 `ReplyTo` 。 啟動器的本機端點參照是 `CreateSequence` 訊息的 `ReplyTo`，而回應程式的本機端點參照則是 `CreateSequence` 訊息的 `To`。

- WCF 可確保傳入的要求訊息會擲出 `MessageId` 和 `ReplyTo` 。

- WCF 可確保 `ReplyTo` 所有應用程式要求訊息的端點參考 URI 符合先前所定義的本機端點參考。

- WCF 可確保所有回復都是 `RelatesTo` `To` 遵循 `wsa` 要求/回復相互關聯規則的正確和標頭。

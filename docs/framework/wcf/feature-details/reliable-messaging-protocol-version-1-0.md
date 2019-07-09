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
# <a name="reliable-messaging-protocol-version-10"></a>Reliable Messaging Protocol 1.0 版

本主題涵蓋 Windows Communication Foundation (WCF) 實作細節 Ws-reliable messaging February 2005 （1.0 版） 通訊協定所需的互通性，使用 HTTP 傳輸。 WCF 會遵循本主題所說明的相關限制與說明 Ws-reliable 訊息規格。 請注意 WinFX 從開始實作 WS-ReliableMessaging 1.0 版通訊協定。

Ws-reliable Messaging February 2005 通訊協定的實作中的 WCF <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>。

為了方便起見，本主題將使用下列角色：

- 啟動器：啟動 WS-Reliable 訊息序列建立作業的用戶端

- 回應程式：接收啟動器要求的服務

本文件會使用下表的前置詞和命名空間。

|前置詞|命名空間|
|------------|---------------|
|wsrm|http://schemas.xmlsoap.org/ws/2005/02/rm|
|netrm|http://schemas.microsoft.com/ws/2006/05/rm|
|秒|http://www.w3.org/2003/05/soap-envelope|
|wsa|http://schemas.xmlsoap.org/ws/2005/08/addressing|
|wsse|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|

## <a name="messaging"></a>訊息

### <a name="sequence-establishment-messages"></a>序列建立訊息

WCF 實作`CreateSequence`和`CreateSequenceResponse`訊息以建立可靠的訊息序列。 以下是適用的條件約束：

- B1101:WCF 啟動器不會產生選用的 Expires 項目，在`CreateSequence`訊息或情況時`CreateSequence`訊息包含`Offer`項目、 選擇性`Expires`中的項目`Offer`項目。

- B1102:存取時`CreateSequence`訊息，WCF`Responder`傳送和接收兩者`Expires`如果它們存在，但不會使用其值的項目。

WS-Reliable 訊息會使用 `Offer` 機制來建立兩個反向關聯序列以形成工作階段。

- R1103:如果`CreateSequence`包含`Offer`項目，可靠的傳訊回應程式必須接收序列並以回應`CreateSequenceResponse`包含`wsrm:Accept`項目，形成兩個相互關聯的反向序列，或拒絕`CreateSequence`要求。

- R1104：流經反向序列的 `SequenceAcknowledgement` 和應用程式訊息必須傳送到 `ReplyTo` 的 `CreateSequence` 端點參考。

- R1105：`AcksTo` 中的 `ReplyTo` 和 `CreateSequence` 端點參考必須具有位址值以符合八位元規格。

  WCF 回應程式會驗證的 URI 部分`AcksTo`和`ReplyTo`Epr 建立序列之前完全相同。

- R1106：`AcksTo` 訊息中的 `ReplyTo` 和 `CreateSequence` 端點參照應該具有相同的參照參數集合。

  WCF 不會強制執行，但假設的之 [reference parameters]`AcksTo`並`ReplyTo`上`CreateSequence`相同，並使用 [參考 parameters] 從`ReplyTo`認可並與序列訊息的端點參考。

- R1107:建立兩個反向序列的使用時`Offer`機制`SequenceAcknowledgement`流經反向序列的應用程式訊息必須傳送至`ReplyTo`端點參考`CreateSequence`。

- R1108:當兩個反向序列都透過 Offer 機制，來建立`[address]`的屬性`wsrm:AcksTo`端點參考子項目`wsrm:Accept`項目`CreateSequenceResponse`必須符合的位元組規格目的地URI`CreateSequence`.

- R1109:建立兩個反向序列的使用時`Offer`機制、 起始端和回應訊息的通知所傳送的訊息必須傳送至相同的端點參考。

  WCF 會使用 Ws-reliable 訊息建立啟動器和回應程式之間的可靠工作階段。 WCF 的 Ws-reliable 訊息實作會提供可靠的工作階段的單向、 要求-回覆與全雙工訊息模式。 Ws-reliable 訊息`Offer`上的機制`CreateSequence` / `CreateSequenceResponse`可讓您建立兩個相互關聯的反向序列，並提供工作階段通訊協定，可適用於所有訊息端點。 WCF 會提供包含的工作階段完整性的端對端保護這類的工作階段的安全性保證，因此它會實際地確保相同的合作對象的訊息會抵達相同的目的地。 這麼做也可以針對應用程式訊息進行 Piggy-Backing 的序列認可作業。 因此，R1104、 R1105 和 R1108 的條件約束套用至 WCF。

`CreateSequence` 訊息的範例。

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

 `CreateSequenceResponse` 訊息的範例。

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

### <a name="sequence"></a>序列

下列清單列出適用於序列的條件約束：

- B1201:WCF 會產生，並存取序號不高於`xs:long`的最大包含值，9223372036854775807。

- B1202:WCF 一律會產生主體空白的最後一個訊息，並將動作 URI 的`http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`。

- B1203:WCF 接收與傳遞的訊息序列標頭，其中包含`LastMessage`項目只要動作 URI 不是`http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`。

序列標頭的範例。

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

### <a name="ackrequested-header"></a>AckRequested 標頭

WCF 會使用`AckRequested`標頭做為 keep-alive 機制。 WCF 不會產生選擇性`MessageNumber`項目。 收到的訊息`AckRequested`包含的標頭`MessageNumber`元素，WCF 會忽略`MessageNumber`元素的值，如下列範例所示。

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement-header"></a>SequenceAcknowledgement 標頭

WCF 所提供的 Ws-reliable 訊息的序列認可使用 piggy-back 機制。

- R1401:當使用建立兩個反向序列`Offer`機制，`SequenceAcknowledgement`標頭可能包含在傳送到預定的收件者的任何應用程式訊息。

- B1402:當 WCF 必須先產生認可之前收到任何序列訊息 (例如，若要滿足`AckRequested`訊息)，WCF 會產生`SequenceAcknowledgement`包含範圍 0-0，如下列範例所示的標頭。

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="0" Lower="0"/>
  </wsrm:SequenceAcknowledgement>
  ```

- B1403:WCF 不會產生`SequenceAcknowledgement`包含的標頭`Nack`項目，但支援`Nack`項目。

### <a name="ws-reliablemessaging-faults"></a>WS-ReliableMessaging 錯誤

以下是適用於 Ws-reliable 訊息錯誤 WCF 實作的條件約束的清單：

- B1501:WCF 不會產生`MessageNumberRollover`錯誤。

- B1502:WCF 端點可能會產生`CreateSequenceRefused`錯誤，如規格所述。

- B1503:When 服務端點到達其連線限制，而且無法處理新的連線時，WCF 會產生額外`CreateSequenceRefused`錯誤子代碼， `netrm:ConnectionLimitReached`，如下列範例所示。

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

### <a name="ws-addressing-faults"></a>WS-Addressing 錯誤

由於 Ws-reliable 訊息會使用 Ws-addressing，WCF Ws-reliable 訊息實作可能會產生 Ws-addressing 錯誤。 本節涵蓋了 Ws-reliable 訊息層明確產生 WCF Ws-addressing 錯誤：

- 當下列其中一項條件成立時，B1601:WCF 就會產生錯誤訊息定址標頭需要：

  - 訊息缺少 `Sequence` 標頭和 `Action` 標頭。

  - `CreateSequence` 訊息缺少 `MessageId` 標頭。

  - `CreateSequence` 訊息缺少 `ReplyTo` 標頭。

- B1602:WCF 產生時遺失訊息不支援動作的錯誤`Sequence`標頭，且`Action`不是可辨識的 Ws-reliable 訊息規格中的標頭。

- B1603:WCF 產生端點無法使用，表示端點不會處理順序根據檢查錯誤`CreateSequence`訊息之定址標頭。

## <a name="protocol-composition"></a>通訊協定組合

### <a name="composition-with-ws-addressing"></a>與 WS-Addressing 組合

WCF 支援兩個 Ws-addressing 版本：Ws-addressing 2004/08 [WS-ADDR] 和 W3C Ws-addressing 1.0 建議 [WS-ADDR-核心] 和 [WS-ADDR-SOAP]。

儘管 WS-Reliable 訊息規格只提到 WS-Addressing 2004/08，它並未限制要使用的 WS-Addressing 版本。 以下是適用於 WCF 的條件約束的清單：

- R2101： 這兩個 Ws-addressing 2004/08 和 Ws-addressing 1.0 可搭配 Ws-reliable 訊息。

- 在整個特定的 Ws-reliable 訊息序列或是一對使用相互關聯的反向序列，就必須使用 ws-addressing 的 R2102:A 單一版本`wsrm:Offer`機制。

### <a name="composition-with-soap"></a>與 SOAP 組合

WCF 支援 SOAP 1.1 和 SOAP 1.2 搭配 Ws-reliable 訊息一起使用。

### <a name="composition-with-ws-security-and-ws-secureconversation"></a>與 WS-Security 和 WS-SecureConversation 組合

WCF 會提供保護 Ws-reliable 訊息序列 (sequence)，透過安全傳輸 (HTTPS)、 與 Ws-security 組合且組合與 Ws-secure Conversation。 以下是適用於 WCF 的條件約束的清單：

- R2301： 若要保護的個別訊息完整性除了 Ws-reliable 訊息序列的完整性與機密性，WCF 要求，必須使用 Ws-secure Conversation。

- R2302:AWS-在建立 Ws-reliable 訊息序列之前，必須建立安全對話工作階段。

- R2303:如果 Ws-reliable 訊息序列存留期超過 Ws-secure Conversation 工作階段的存留期，`SecurityContextToken`藉由使用 Ws-secure Conversation 必須更新使用對應的 Ws-secure Conversation 更新繫結。

- B2304:WS-可靠的訊息序列或是一對相互關聯的反向序列一律繫結至單一 Ws-secureconversation 工作階段。

  WCF 來源會產生`wsse:SecurityTokenReference`的項目擴充性區段中的項目`CreateSequence`訊息。

- 與 Ws-secure Conversation，R2305:When`CreateSequence`訊息必須包含`wsse:SecurityTokenReference`項目。

## <a name="ws-reliable-messaging-ws-policy-assertion"></a>WS-Reliable 訊息 WS-Policy 判斷提示

WCF 會使用 Ws-reliable 訊息 Ws-policy 判斷提示`wsrm:RMAssertion`來描述端點的功能。 以下是適用於 WCF 的條件約束的清單：

- B3001:WCF 會附加`wsrm:RMAssertion`Ws-policy 判斷提示至`wsdl:binding`項目。 WCF 支援這兩個附件`wsdl:binding`和`wsdl:port`項目。

- B3002:WCF 支援下列選用的 Ws-reliable 訊息判斷提示屬性，並針對它們提供控制的 WCF`ReliableMessagingBindingElement`:

  - `wsrm:InactivityTimeout`

  - `wsrm:AcknowledgementInterval`

  下列為範例。

  ```xml
  <wsrm:RMAssertion>
    <wsrm:InactivityTimeout Milliseconds="600000" />
    <wsrm:AcknowledgementInterval Milliseconds="200" />
  </wsrm:RMAssertion>
  ```

## <a name="flow-control-ws-reliable-messaging-extension"></a>WS-Reliable 訊息延伸的流量控制

WCF 會使用 Ws-reliable 訊息擴充性，提供選擇性的額外更緊密地控制序列訊息流量。

藉由設定已啟用流量控制<xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType>屬性設`true`。 以下是適用於 WCF 的條件約束的清單：

- B4001:WCF 啟用信賴傳訊流量控制時，會產生`netrm:BufferRemaining`中的項目擴充性項目`SequenceAcknowledgement`標頭。

- B4002:啟用信賴傳訊流量控制時，WCF 不需要`netrm:BufferRemaining`項目會出現在`SequenceAcknowledgement`標頭，如下列範例所示。

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

- B4003:WCF 會使用`netrm:BufferRemaining`指出多少新訊息的可靠的傳訊目的地可以緩衝。

- B4004: WCF 可靠傳訊服務節流處理的可信賴傳訊目的地應用程式無法快速接收訊息時，傳輸的訊息數目。 可信賴傳訊目的地會緩衝處理訊息，並讓項目值降為 0。

- B4005:WCF 會產生`netrm:BufferRemaining`整數值介於 0 到 4096 （含)，並讀取介於 0 的整數值與`xs:int`的`maxInclusive`值 214748364 （含)。

## <a name="message-exchange-patterns"></a>訊息交換模式

不同的訊息交換模式使用 Ws-reliable 訊息時，本節會說明 WCF 的行為。 在每個訊息交換模式中，會考慮下列兩種部署案例：

- 不可定址的啟動器：啟動器位於防火牆;回應程式將訊息傳送至啟動器只在 HTTP 回應。

- 可定址的啟動器：啟動器和回應程式可傳送 HTTP 要求;換句話說，您可以建立兩個反向 HTTP 連線。

### <a name="one-way-non-addressable-initiator"></a>單向、不可定址啟動器

#### <a name="binding"></a>繫結

WCF 會提供一個 HTTP 通道上使用一個序列的單向訊息交換模式。 WCF 會使用 HTTP 要求來傳送所有訊息從 RMS 至 RMD，並在 HTTP 回應來都傳送所有訊息從 rmd 傳送至 RMS。

#### <a name="createsequence-exchange"></a>CreateSequence 交換

WCF 啟動器會產生`CreateSequence`不含提議的訊息。 WCF 回應程式會確保`CreateSequence`建立序列之前不含提議。 WCF 回應回覆`CreateSequence`要求與`CreateSequenceResponse`訊息。

#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement

WCF 啟動器處理以外的所有訊息的認可回覆`CreateSequence`訊息與錯誤訊息。 WCF 回應程式一律產生獨立認可，以回應這兩個序列和`AckRequested`訊息。

#### <a name="terminatesequence-message"></a>TerminateSequence 訊息

WCF 會將`TerminateSequence`視為單向作業，代表 HTTP 回應具有空白主體與 HTTP 202 狀態碼。

### <a name="one-way-addressable-initiator"></a>單向、可定址啟動器

#### <a name="binding"></a>繫結

WCF 會提供使用一個序列，透過在一個傳入與一個傳出 Http 通道的單向訊息交換模式。 WCF 會使用 HTTP 要求來傳送所有訊息。 所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。

#### <a name="createsequence-exchange"></a>CreateSequence 交換

WCF 啟動器會產生`CreateSequence`不含提議的訊息。 WCF 回應程式會確保`CreateSequence`建立序列之前不含提議。 WCF 回應傳輸`CreateSequenceResponse`HTTP 要求訊息而獲得解決`ReplyTo`端點參考。

### <a name="duplex-addressable-initiator"></a>雙工、可定址啟動器

#### <a name="binding"></a>繫結

WCF 提供完全非同步的雙向訊息交換模式使用一個傳入與一個傳出 HTTP 通道上的兩個序列。 WCF 會使用 HTTP 要求來傳送所有訊息。 所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。

#### <a name="createsequence-exchange"></a>CreateSequence 交換

WCF 啟動器會產生`CreateSequence`供應項目訊息。 WCF 回應程式會確保`CreateSequence`供應項目中建立序列之前。 WCF 傳送`CreateSequenceResponse`HTTP 要求傳送給`CreateSequence`的`ReplyTo`端點參考。

#### <a name="sequence-lifetime"></a>序列存留期

WCF 會將兩個序列視為一個全雙工工作階段。

在產生可挑剔某個序列的錯誤，WCF 會預期遠端端點將同時挑剔兩個序列。 在讀取可挑剔某個序列的錯誤，WCF 會挑剔兩個序列。

WCF 可以關閉其傳出序列並繼續處理其傳入序列的訊息。 相反地，WCF 可以處理傳入序列的關閉，並繼續傳送其傳出序列的訊息。

### <a name="request-reply-non-addressable-initiator"></a>要求-回覆、不可定址啟動器

#### <a name="binding"></a>繫結

WCF 提供單向和要求-回覆訊息交換模式使用兩個序列透過在一個 HTTP 通道。 WCF 會使用 HTTP 要求來傳送要求序列訊息，並透過 HTTP 回應來傳送回覆序列的訊息。

#### <a name="createsequence-exchange"></a>CreateSequence 交換

WCF 啟動器會產生`CreateSequence`供應項目訊息。 WCF 回應程式會確保`CreateSequence`供應項目中建立序列之前。 WCF 回應回覆`CreateSequence`要求與`CreateSequenceResponse`訊息。

#### <a name="one-way-message"></a>單向訊息

若要成功完成單向訊息交換通訊協定，WCF 啟動器會傳送要求序列訊息的 HTTP 要求並接收獨立`SequenceAcknowledgement`HTTP 回應的訊息。 `SequenceAcknowledgement` 必須認可傳送的訊息。

WCF 回應來回覆要求，並認可、 錯誤或是內含空本文與 HTTP 202 狀態碼的回應。

#### <a name="two-way-messages"></a>雙向訊息

若要成功完成雙向訊息交換通訊協定，WCF 啟動者傳送要求序列訊息的 HTTP 要求和接收 HTTP 回應的回覆序列訊息。 回應中必須包含認可傳輸之要求序列訊息的 `SequenceAcknowledgement`。

WCF 回應來回覆要求應用程式回覆、 錯誤或是內含空本文與 HTTP 202 狀態碼的回應。

由於單向訊息與應用程式回覆時機的緣故，要求序列訊息的序號與回應訊息的序號彼此並未互相關聯。

#### <a name="retrying-replies"></a>重試回覆

WCF 需仰賴雙向訊息交換通訊協定相互關聯的 HTTP 要求-回覆相互關聯。 因為這個緣故，WCF 啟動器不會停止重試要求序列訊息，當在認可要求序列訊息，但在 HTTP 回應內含認可、 使用者訊息，或是錯誤時，而不是。 WCF 回應重試回覆相互關聯之要求的 HTTP 要求階段上的回覆。

#### <a name="lastmessage-exchange"></a>LastMessage 交換

WCF 啟動器會產生，並傳送 HTTP 要求階段上的空白主體最後一個訊息。 WCF 需要回應，但會忽略實際的回應訊息。 WCF 回應程式會回覆要求序列的主體空白的最後一則訊息回覆序列的主體空白的最後一個訊息。

如果 WCF 回應者收到的最後一則訊息中的動作 URI 不是`http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`，WCF 則會以最後一則訊息回覆。 在雙向訊息交換通訊協定的情況中，最後一則訊息包含應用程式訊息；在單向訊息交換通訊協定的情況中，最後一則訊息包含空白主體。

WCF 回應程式不需要回覆序列的主體空白的最後一則訊息的通知。

#### <a name="terminatesequence-exchange"></a>TerminateSequence 交換

一旦所有要求都收到有效回覆，WCF 啟動器會產生，並傳送要求序列的`TerminateSequence`HTTP 要求階段上的訊息。 WCF 需要回應，但會忽略實際的回應訊息。 回覆要求序列的 WCF 回應`TerminateSequence`透過回覆序列訊息`TerminateSequence`訊息。

在正常的關機序列中，兩個 `TerminateSequence` 訊息會同時包含完整範圍的 `SequenceAcknowledgement`。

### <a name="requestreply-addressable-initiator"></a>要求/回覆、可定址啟動器

#### <a name="binding"></a>繫結

WCF 會提供使用兩個序列，透過在一個傳入與一個傳出 HTTP 通道要求-回覆訊息交換模式。 WCF 會使用 HTTP 要求來傳送所有訊息。 所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。

#### <a name="createsequence-exchange"></a>CreateSequence 交換

WCF 啟動器會產生`CreateSequence`供應項目訊息。 WCF 回應程式會確保`CreateSequence`供應項目中建立序列之前。 WCF 傳送`CreateSequenceResponse`HTTP 要求傳送給`CreateSequence`的`ReplyTo`端點參考。

#### <a name="requestreply-correlation"></a>要求/回覆相互關聯

WCF 啟動者可確保所有的應用程式要求訊息都帶有`MessageId`和`ReplyTo`端點參考。 適用於 WCF 啟動器`CreateSequence`訊息的`ReplyTo`上每個應用程式要求訊息的端點參考。 WCF 回應程式會要求傳入的要求訊息都帶有`MessageId`和`ReplyTo`。 WCF 回應程式會確保兩個端點參照 URI `CreateSequence` ，而且所有的應用程式要求訊息完全相同。

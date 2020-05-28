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
# <a name="reliable-messaging-protocol-version-10"></a>Reliable Messaging Protocol 1.0 版

本主題涵蓋使用 HTTP 傳輸進行交互操作所需的 WS-TRUST 訊息2月2005（版本1.0）通訊協定 Windows Communication Foundation （WCF）的執行詳細資料。 WCF 遵循 WS-TRUST 訊息規格與本主題所述的條件約束和說明。 請注意，ws-reliablemessaging 版本1.0 通訊協定是從 WinFX 開始實行。

WS-可靠訊息2月2005通訊協定是在 WCF 中由所執行 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> 。

為了方便起見，本主題將使用下列角色：

- 啟動器：啟動 WS-Reliable 訊息序列建立作業的用戶端

- 回應程式：接收啟動器要求的服務

本文件會使用下表的前置詞和命名空間。

|前置詞|命名空間|
|------------|---------------|
|wsrm|`http://schemas.xmlsoap.org/ws/2005/02/rm`|
|netrm|`http://schemas.microsoft.com/ws/2006/05/rm`|
|s|`http://www.w3.org/2003/05/soap-envelope`|
|wsa|`http://schemas.xmlsoap.org/ws/2005/08/addressing|
|wsse|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd`|

## <a name="messaging"></a>Messaging (傳訊)

### <a name="sequence-establishment-messages"></a>序列建立訊息

WCF 會執行 `CreateSequence` 和 `CreateSequenceResponse` 訊息，以建立可靠的訊息順序。 以下是適用的條件約束：

- B1101： WCF 啟動器不會在訊息中產生選擇性的 Expires 元素， `CreateSequence` 或在訊息包含專案的情況下，在專案 `CreateSequence` `Offer` 中使用選擇性的 `Expires` 元素 `Offer` 。

- B1102：存取訊息時 `CreateSequence` ，WCF 會傳送 `Responder` 和接收兩個 `Expires` 元素（如果有的話），但不會使用它們的值。

WS-Reliable 訊息會使用 `Offer` 機制來建立兩個反向關聯序列以形成工作階段。

- R1103：如果 `CreateSequence` 包含 `Offer` 項目，則可信賴傳訊回應程式必須接收序列並以包含 `CreateSequenceResponse` 項目的 `wsrm:Accept` 來回應，以形成兩個相互關聯的反向序列，或是拒絕 `CreateSequence` 要求。

- R1104：流經反向序列的 `SequenceAcknowledgement` 和應用程式訊息必須傳送到 `ReplyTo` 的 `CreateSequence` 端點參考。

- R1105：`AcksTo` 中的 `ReplyTo` 和 `CreateSequence` 端點參考必須具有位址值以符合八位元規格。

  WCF 回應程式 `AcksTo` 會在建立序列之前，確認和 EPRs 的 URI 部分 `ReplyTo` 是否相同。

- R1106：`AcksTo` 訊息中的 `ReplyTo` 和 `CreateSequence` 端點參照應該具有相同的參照參數集合。

  WCF 不會強制執行，但會假設和 on 的 [參考參數] `AcksTo` `ReplyTo` `CreateSequence` 相同，並使用來自端點參考的 [參考參數] `ReplyTo` 來取得通知和反向順序訊息。

- R1107：當兩個反向序列都是透過 `Offer` 機制建立時，流經反向序列的 `SequenceAcknowledgement` 和應用程式訊息必須傳送至 `ReplyTo` 的 `CreateSequence` 端點參考。

- R1108：當兩個反向序列都透過 Offer 機制建立時，`[address]` 端點參考子項目 (屬於 `wsrm:AcksTo` 的 `wsrm:Accept` 項目) 的 `CreateSequenceResponse` 屬性必須符合 `CreateSequence` 的目的地 URI 的位元組規格。

- R1109：當兩個反向序列都是透過 `Offer` 機制建立時，從啟動器傳送的訊息以及透過回應程式對訊息的認可，必須傳送至相同的端點參考。

  WCF 使用 WS-TRUST 訊息，在啟動器和回應程式之間建立可靠的會話。 WCF 的 WS-TRUST 訊息執行可為單向、要求-回復與全雙工訊息模式提供可靠的會話。 上的 WS-可靠訊息 `Offer` 機制 `CreateSequence` / `CreateSequenceResponse` 可讓您建立兩個相互關聯的反向序列，並提供適用于所有訊息端點的會話通訊協定。 因為 WCF 會針對這類會話提供安全性保證，包括會話完整性的端對端保護，所以確保適用于同一方的訊息會抵達相同的目的地。 這麼做也可以針對應用程式訊息進行 Piggy-Backing 的序列認可作業。 因此，條件約束 R1104、R1105 和 R1108 適用于 WCF。

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

### <a name="sequence"></a>順序

下列清單列出適用於序列的條件約束：

- B1201： WCF 會產生並存取不超過 `xs:long` 最大內含值9223372036854775807的序號。

- B1202： WCF 一律會產生具有動作 URI 的空白主體最後訊息 `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` 。

- B1203： `LastMessage` 只要動作 URI 不是，WCF 就會接收並傳遞包含專案之 Sequence 標頭的訊息 `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` 。

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

WCF 會使用 `AckRequested` 標頭做為 keep-alive 機制。 WCF 不會產生選擇性的 `MessageNumber` 元素。 接收包含專案的 `AckRequested` 標頭訊息時 `MessageNumber` ，WCF 會忽略 `MessageNumber` 元素的值，如下列範例所示。

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement-header"></a>SequenceAcknowledgement 標頭

WCF 會針對 WS-TRUST 訊息中提供的順序通知使用 piggy-back 回溯機制。

- R1401：當兩個反向序列透過 `Offer` 機制建立時，`SequenceAcknowledgement` 標頭可以包含在任何傳送至目的收件者的應用程式訊息中。

- B1402：當 WCF 必須在接收任何序列訊息（例如，為了滿足訊息）之前產生認可時 `AckRequested` ，wcf `SequenceAcknowledgement` 會產生包含範圍0-0 的標頭，如下列範例所示。

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="0" Lower="0"/>
  </wsrm:SequenceAcknowledgement>
  ```

- B1403： WCF 不會產生 `SequenceAcknowledgement` 包含 `Nack` 元素但支援元素的標頭 `Nack` 。

### <a name="ws-reliablemessaging-faults"></a>WS-ReliableMessaging 錯誤

以下是適用于 WS-TRUST 訊息錯誤之 WCF 實作為條件約束的清單：

- B1501： WCF 不會產生 `MessageNumberRollover` 錯誤。

- B1502： WCF 端點可能會產生 `CreateSequenceRefused` 錯誤，如規格中所述。

- B1503：當服務端點達到其連線限制，而且無法處理新的連線時，WCF 會產生額外的 `CreateSequenceRefused` 錯誤子代碼， `netrm:ConnectionLimitReached` 如下列範例所示。

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

因為 WS-TRUST 訊息使用 WS-ADDRESSING，所以 WCF WS-TRUST 訊息執行可能會產生 WS-ADDRESSING 錯誤。 本節涵蓋 WCF 在 WS-TRUST 訊息層上明確產生的 WS-ADDRESSING 錯誤：

- B1601：當下列其中一項為真時，WCF 會產生所需的錯誤訊息定址標頭：

  - 訊息缺少 `Sequence` 標頭和 `Action` 標頭。

  - `CreateSequence` 訊息缺少 `MessageId` 標頭。

  - `CreateSequence` 訊息缺少 `ReplyTo` 標頭。

- B1602： WCF 會在回復遺失標頭的訊息時產生不支援的錯誤動作 `Sequence` ，而且具有 `Action` 不能在 ws-trust 訊息規格中辨識的標頭。

- B1603： WCF 會產生無法使用的錯誤端點，以指出端點不會根據 `CreateSequence` 訊息的定址標頭檢查來處理序列。

## <a name="protocol-composition"></a>通訊協定組合

### <a name="composition-with-ws-addressing"></a>與 WS-Addressing 組合

WCF 支援兩種 WS-ADDRESSING 版本： WS-ADDRESSING 2004/08 [WS-ATOMICTRANSACTION] 和 W3C WS-ADDRESSING 1.0 建議 [WS-ADDRESSING-CORE] 和 [WS-ATOMICTRANSACTION-SOAP]。

儘管 WS-Reliable 訊息規格只提到 WS-Addressing 2004/08，它並未限制要使用的 WS-Addressing 版本。 以下是適用于 WCF 的條件約束清單：

- R2101：WS-Addressing 2004/08 和 WS-Addressing 1.0 皆可搭配 WS-Reliable 訊息一起使用。

- R2102：必須在指定的 WS-TRUST 訊息序列或一對使用機制相互關聯的反向序列中使用 WS-ADDRESSING 的單一版本 `wsrm:Offer` 。

### <a name="composition-with-soap"></a>與 SOAP 組合

WCF 支援搭配使用 SOAP 1.1 和 SOAP 1.2 與 WS-可靠的訊息。

### <a name="composition-with-ws-security-and-ws-secureconversation"></a>與 WS-Security 和 WS-SecureConversation 組合

WCF 藉由使用安全傳輸（HTTPS）、以 WS-MANAGEMENT 撰寫，以及與 WS-安全交談組合，為 WS-TRUST 訊息序列提供保護。 以下是適用于 WCF 的條件約束清單：

- R2301：除了個別訊息的完整性和機密性以外，若要保護 WS-TRUST 訊息順序的完整性，WCF 會要求必須使用 WS-安全交談。

- R2302：在建立 WS-Reliable 訊息序列之前，必須先建立 WS-Secure Conversation 工作階段。

- R2303：如果 WS-Reliable 訊息序列的存留期超過 WS-Secure Conversation 工作階段的存留期，則使用 WS-Secure Conversation 建立的 `SecurityContextToken` 必須透過對應的 WS-Secure Conversation 更新繫結來加以更新。

- B2304：WS-Reliable 訊息序列或是一對相互關聯的反向序列一律繫結至單一 WS-SecureConversation 工作階段。

  WCF 來源會 `wsse:SecurityTokenReference` 在訊息的元素擴充性區段中產生元素 `CreateSequence` 。

- R2305：以 WS-安全對話撰寫時， `CreateSequence` 訊息必須包含 `wsse:SecurityTokenReference` 元素。

## <a name="ws-reliable-messaging-ws-policy-assertion"></a>WS-Reliable 訊息 WS-Policy 判斷提示

WCF 使用 WS-可靠的訊息 WS-原則判斷提示 `wsrm:RMAssertion` 來描述端點功能。 以下是適用于 WCF 的條件約束清單：

- B3001： WCF 會 `wsrm:RMAssertion` 將 WS-原則判斷提示附加至 `wsdl:binding` 元素。 WCF 同時支援 `wsdl:binding` 和元素的附件 `wsdl:port` 。

- B3002： WCF 支援 WS-可靠訊息判斷提示的下列選擇性屬性，並可在 WCF 上進行控制 `ReliableMessagingBindingElement` ：

  - `wsrm:InactivityTimeout`

  - `wsrm:AcknowledgementInterval`

  以下是一個範例。

  ```xml
  <wsrm:RMAssertion>
    <wsrm:InactivityTimeout Milliseconds="600000" />
    <wsrm:AcknowledgementInterval Milliseconds="200" />
  </wsrm:RMAssertion>
  ```

## <a name="flow-control-ws-reliable-messaging-extension"></a>WS-Reliable 訊息延伸的流量控制

WCF 使用 WS-TRUST 訊息擴充性來提供選擇性額外的更緊密控制序列訊息流程。

藉由將屬性設定為，即可啟用流量控制 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> `true` 。 以下是適用于 WCF 的條件約束清單：

- B4001 一旦：啟用可靠的訊息流程式控制制時，WCF 會在標頭的專案擴充性 `netrm:BufferRemaining` 中產生元素 `SequenceAcknowledgement` 。

- B4002：啟用可靠的訊息流程式控制制時，WCF 不需要 `netrm:BufferRemaining` 在標頭中出現元素 `SequenceAcknowledgement` ，如下列範例所示。

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

- B4003： WCF `netrm:BufferRemaining` 會使用來指出可靠訊息目的地可以緩衝處理的新訊息數目。

- B4004： WCF 可靠的訊息處理服務會在可靠的訊息目的地應用程式無法快速接收訊息時，限制傳輸的訊息數目。 可信賴傳訊目的地會緩衝處理訊息，並讓項目值降為 0。

- B4005： WCF 會產生 `netrm:BufferRemaining` 介於0到4096（含）之間的整數值，並讀取介於0和 `xs:int` 的 `maxInclusive` 值214748364（含）之間的整數值。

## <a name="message-exchange-patterns"></a>訊息交換模式

本節說明當您針對不同的訊息交換模式使用 WS-TRUST 訊息時，WCF 的行為。 在每個訊息交換模式中，會考慮下列兩種部署案例：

- 不可定址的啟動器：啟動器位於防火牆後方，回應程式只能透過 HTTP 回應將訊息傳送至啟動器。

- 可定址的啟動器：可將 HTTP 要求同時傳送給啟動器與回應程式，亦即可建立兩個反向 HTTP 連線。

### <a name="one-way-non-addressable-initiator"></a>單向、不可定址啟動器

#### <a name="binding"></a>繫結

WCF 會在一個 HTTP 通道上使用一個序列來提供單向的訊息交換模式。 WCF 會使用 HTTP 要求，將所有訊息從 RMS 傳送至 RMD 和 HTTP 回應，以將所有訊息從 RMD 傳送至 RMS。

#### <a name="createsequence-exchange"></a>CreateSequence 交換

WCF 啟動器會產生 `CreateSequence` 不含供應專案的訊息。 WCF 回應程式會在 `CreateSequence` 建立序列之前，確保沒有任何供應專案。 WCF 回應程式會 `CreateSequence` 使用訊息來回複要求 `CreateSequenceResponse` 。

#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement

除了訊息和錯誤訊息以外，WCF 啟動器會處理所有訊息回復的 `CreateSequence` 通知。 WCF 回應者一律會在對序列和訊息的回應中產生獨立的認可 `AckRequested` 。

#### <a name="terminatesequence-message"></a>TerminateSequence 訊息

WCF 會將視為 `TerminateSequence` 單向作業，這表示 HTTP 回應具有空白主體和 HTTP 202 狀態碼。

### <a name="one-way-addressable-initiator"></a>單向、可定址啟動器

#### <a name="binding"></a>繫結

WCF 會在傳入和傳出 Http 通道上使用一個序列來提供單向訊息交換模式。 WCF 會使用 HTTP 要求來傳送所有訊息。 所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。

#### <a name="createsequence-exchange"></a>CreateSequence 交換

WCF 啟動器會產生 `CreateSequence` 不含供應專案的訊息。 WCF 回應程式會在 `CreateSequence` 建立序列之前，確保沒有任何供應專案。 WCF 回應 `CreateSequenceResponse` 程式會在以端點參考定址的 HTTP 要求上傳輸訊息 `ReplyTo` 。

### <a name="duplex-addressable-initiator"></a>雙工、可定址啟動器

#### <a name="binding"></a>繫結

WCF 會在輸入和輸出 HTTP 通道上使用兩個序列，以提供完全非同步雙向訊息交換模式。 WCF 會使用 HTTP 要求來傳送所有訊息。 所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。

#### <a name="createsequence-exchange"></a>CreateSequence 交換

WCF 啟動器會產生 `CreateSequence` 包含供應專案的訊息。 WCF 回應程式會在 `CreateSequence` 建立序列之前，確保具有供應專案。 WCF 會將 `CreateSequenceResponse` HTTP 要求的傳送至已定址 `CreateSequence` 的 `ReplyTo` 端點參考。

#### <a name="sequence-lifetime"></a>序列存留期

WCF 會將這兩個序列視為一個全雙工會話。

在產生錯誤一個序列的錯誤時，WCF 會預期遠端端點會同時容錯這兩個序列。 當讀取錯誤發生一系列的錯誤時，WCF 會同時錯誤這兩個序列。

WCF 可以關閉其輸出序列，並繼續處理其輸入序列的訊息。 相反地，WCF 可以處理輸入序列的關閉，並繼續以輸出序列來傳送訊息。

### <a name="request-reply-non-addressable-initiator"></a>要求-回覆、不可定址啟動器

#### <a name="binding"></a>繫結

WCF 透過在一個 HTTP 通道上使用兩個序列的方式，提供單向和要求-回復訊息交換模式。 WCF 會使用 HTTP 要求來傳送要求序列的訊息，並使用 HTTP 回應來傳送回復序列的訊息。

#### <a name="createsequence-exchange"></a>CreateSequence 交換

WCF 啟動器會產生 `CreateSequence` 包含供應專案的訊息。 WCF 回應程式會在 `CreateSequence` 建立序列之前，確保具有供應專案。 WCF 回應程式會 `CreateSequence` 使用訊息來回複要求 `CreateSequenceResponse` 。

#### <a name="one-way-message"></a>單向訊息

為了成功完成單向訊息交換通訊協定，WCF 啟動器會在 HTTP 要求上傳輸要求序列訊息，並 `SequenceAcknowledgement` 在 HTTP 回應上接收獨立的訊息。 `SequenceAcknowledgement` 必須認可傳送的訊息。

WCF 回應者可以使用通知、錯誤或具有空白本文和 HTTP 202 狀態碼的回應來回複要求。

#### <a name="two-way-messages"></a>雙向訊息

為了成功完成雙向訊息交換通訊協定，WCF 啟動器會在 HTTP 要求上傳輸要求序列訊息，並在 HTTP 回應上接收回複序列訊息。 回應中必須包含認可傳輸之要求序列訊息的 `SequenceAcknowledgement`。

WCF 回應者可以透過應用程式回復、錯誤或具有空白本文的回應，以及 HTTP 202 狀態碼來回複要求。

由於單向訊息與應用程式回覆時機的緣故，要求序列訊息的序號與回應訊息的序號彼此並未互相關聯。

#### <a name="retrying-replies"></a>重試回覆

WCF 依賴雙向訊息交換通訊協定相互關聯的 HTTP 要求-回復相互關聯。 因此，在認可要求序列訊息時，WCF 啟動器不會停止重試要求序列訊息，而是在 HTTP 回應攜帶通知、使用者訊息或錯誤時發生。 WCF 回應程式會在與回復相互關聯之要求的 HTTP 要求階段上，重試回復。

#### <a name="lastmessage-exchange"></a>LastMessage 交換

WCF 啟動器會在 HTTP 要求階段上產生並傳送空的主體最後一則訊息。 WCF 需要回應，但會忽略實際的回應訊息。 WCF 回應程式會以回復序列的主體最後一則訊息來回複要求序列的空白主體最後一則訊息。

如果 WCF 回應程式收到動作 URI 不是的最後一則訊息 `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` ，則 WCF 會回復最後一則訊息。 在雙向訊息交換通訊協定的情況中，最後一則訊息包含應用程式訊息；在單向訊息交換通訊協定的情況中，最後一則訊息包含空白主體。

WCF 回應程式不需要對回復序列的空白主體最後一個訊息進行認可。

#### <a name="terminatesequence-exchange"></a>TerminateSequence 交換

當所有要求都收到有效回復時，WCF 啟動器會在 HTTP 要求階段上產生並傳送要求序列的 `TerminateSequence` 訊息。 WCF 需要回應，但會忽略實際的回應訊息。 WCF 回應程式會 `TerminateSequence` 使用回復序列的訊息來回複要求序列的訊息 `TerminateSequence` 。

在正常的關機序列中，兩個 `TerminateSequence` 訊息會同時包含完整範圍的 `SequenceAcknowledgement`。

### <a name="requestreply-addressable-initiator"></a>要求/回覆、可定址啟動器

#### <a name="binding"></a>繫結

WCF 會在輸入和輸出 HTTP 通道上使用兩個序列，以提供要求-回復訊息交換模式。 WCF 會使用 HTTP 要求來傳送所有訊息。 所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。

#### <a name="createsequence-exchange"></a>CreateSequence 交換

WCF 啟動器會產生 `CreateSequence` 包含供應專案的訊息。 WCF 回應程式會在 `CreateSequence` 建立序列之前，確保具有供應專案。 WCF 會將 `CreateSequenceResponse` HTTP 要求的傳送至已定址 `CreateSequence` 的 `ReplyTo` 端點參考。

#### <a name="requestreply-correlation"></a>要求/回覆相互關聯

WCF 啟動器可確保所有應用程式要求訊息都具有 `MessageId` 和 `ReplyTo` 端點參考。 WCF 啟動器會 `CreateSequence` `ReplyTo` 在每個應用程式要求訊息上套用訊息的端點參考。 WCF 回應程式要求傳入的要求訊息必須具有 `MessageId` 和 `ReplyTo` 。 WCF 回應者可確保 `CreateSequence` 和所有應用程式要求訊息的端點參考 URI 都相同。

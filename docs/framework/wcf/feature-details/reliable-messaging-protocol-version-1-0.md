---
title: "Reliable Messaging Protocol 1.0 版"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d204600682ec8acbc229240c4e1bc859d8ea4d21
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="reliable-messaging-protocol-version-10"></a>Reliable Messaging Protocol 1.0 版
本主題涵蓋了 WS-Reliable Messaging February 2005 (1.0 版) 通訊協定的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 實作詳細資料，這個通訊協定是使用 HTTP 傳輸來進行交互操作時所需的通訊協定。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 遵循本主題所述 WS-Reliable Messaging 規格的條件約束及說明。 請注意，[!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] 中開始實作 WS-ReliableMessaging 1.0 版通訊協定。  
  
 WS-Reliable Messaging February 2005 通訊協定可透過 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 在 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> 中實作。  
  
 為了方便起見，本主題將使用下列角色：  
  
-   啟動器：啟動 WS-Reliable 訊息序列建立作業的用戶端  
  
-   回應程式：接收啟動器要求的服務  
  
 本文件會使用下表的前置詞和命名空間。  
  
|前置詞|命名空間|  
|------------|---------------|  
|wsrm|http://schemas.xmlsoap.org/ws/2005/02/rm|  
|netrm|http://schemas.microsoft.com/ws/2006/05/rm|  
|s|http://www.w3.org/2003/05/soap-envelope|  
|wsa|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|wsse|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
  
## <a name="messaging"></a>傳訊  
  
### <a name="sequence-establishment-messages"></a>序列建立訊息  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會實作 `CreateSequence` 和 `CreateSequenceResponse` 訊息以建立可靠訊息序列。 以下是適用的條件約束：  
  
-   B1101：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器不會在 `CreateSequence` 訊息中產生選用的 Expires 項目，或當 `CreateSequence` 訊息包含 `Offer` 項目時，在 `Expires` 項目中產生選用的 `Offer` 項目。  
  
-   B1102：在存取 `CreateSequence` 訊息時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]`Responder` 會同時傳送與接收 `Expires` 項目 (如果兩者都存在的話)，但是不會使用它們的值。  
  
 WS-Reliable 訊息會使用 `Offer` 機制來建立兩個反向關聯序列以形成工作階段。  
  
-   R1103：如果 `CreateSequence` 包含 `Offer` 項目，則可信賴傳訊回應程式必須接收序列並以包含 `CreateSequenceResponse` 項目的 `wsrm:Accept` 來回應，以形成兩個相互關聯的反向序列，或是拒絕 `CreateSequence` 要求。  
  
-   R1104：流經反向序列的 `SequenceAcknowledgement` 和應用程式訊息必須傳送到 `ReplyTo` 的 `CreateSequence` 端點參考。  
  
-   R1105：`AcksTo` 中的 `ReplyTo` 和 `CreateSequence` 端點參考必須具有位址值以符合八位元規格。  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會在建立序列之前，先驗證 `AcksTo`、`ReplyTo` EPR 的 URI 部分是否相同。  
  
-   R1106：`AcksTo` 訊息中的 `ReplyTo` 和 `CreateSequence` 端點參照應該具有相同的參照參數集合。  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不會強制執行，但會假定 `AcksTo` 上的 `ReplyTo` 和 `CreateSequence` 之 [reference parameters] 都是一樣，並且使用來自 `ReplyTo` 端點參照的 [reference parameters]，以認可並與序列訊息對話。  
  
-   R1107：當兩個反向序列都是透過 `Offer` 機制建立時，流經反向序列的 `SequenceAcknowledgement` 和應用程式訊息必須傳送至 `ReplyTo` 的 `CreateSequence` 端點參考。  
  
-   R1108：當兩個反向序列都透過 Offer 機制建立時，`[address]` 端點參考子項目 (屬於 `wsrm:AcksTo` 的 `wsrm:Accept` 項目) 的 `CreateSequenceResponse` 屬性必須符合 `CreateSequence` 的目的地 URI 的位元組規格。  
  
-   R1109：當兩個反向序列都是透過 `Offer` 機制建立時，從啟動器傳送的訊息以及透過回應程式對訊息的認可，必須傳送至相同的端點參考。  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 使用 WS-Reliable 訊息在啟動器與回應程式之間建立可靠工作階段。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的 WS-Reliable 訊息實作會針對單向、要求-回覆與全雙工訊息模式提供可靠工作階段。 Ws-reliable 訊息`Offer`上的機制`CreateSequence` / `CreateSequenceResponse`可讓您建立兩個相互關聯的反向序列，並提供工作階段通訊協定，可適用於所有訊息端點。 由於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會針對此類工作階段提供安全性保證，包含工作階段完整性的端對端保護，因此可以實際地確保訊息會抵達預定的相同目的地。 這麼做也可以針對應用程式訊息進行 Piggy-Backing 的序列認可作業。 因此，R1104、R1105，和 R1108 的約束條件適用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]。  
  
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
  
-   B1201:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]會產生並存取序號大於`xs:long`的最大包含值，9223372036854775807。  
  
-   B1202:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]一律會產生空白主體最後一個訊息，與 http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage 的動作 URI。  
  
-   B1203：只要動作 URI 不是 http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會透過序列標頭 (其中包含 `LastMessage` 項目) 來接收與傳遞訊息。  
  
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
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會使用 `AckRequested` 標頭做為 Keep-Alive 機制。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不會產生選用的 `MessageNumber` 元素。 在收到使用 `AckRequested` 標頭 (內含 `MessageNumber` 項目) 的訊息時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會忽略 `MessageNumber` 的項目值，如下列範例所示。  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement-header"></a>SequenceAcknowledgement 標頭  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會針對 WS-Reliable 訊息所提供的序列認可使用 Piggy-Back 機制。  
  
-   R1401：當兩個反向序列透過 `Offer` 機制建立時，`SequenceAcknowledgement` 標頭可以包含在任何傳送至目的收件者的應用程式訊息中。  
  
-   B1402：當 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 在收到任何序列訊息之前必須先產生認可時 (例如，為了滿足 `AckRequested` 訊息)，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會產生包含範圍 0-0 的 `SequenceAcknowledgement` 標頭，如下列範例所示。  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="0" Lower="0"/>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B1403：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不會產生包含 `SequenceAcknowledgement` 項目的 `Nack` 標頭，但是支援 `Nack` 項目。  
  
### <a name="ws-reliablemessaging-faults"></a>WS-ReliableMessaging 錯誤  
 下列清單列出適用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 之 WS-Reliable 訊息錯誤實作的條件約束：  
  
-   B1501：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不會產生 `MessageNumberRollover` 錯誤。  
  
-   B1502:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]端點可能會產生`CreateSequenceRefused`規格中所述的錯誤。  
  
-   B1503:When 服務端點到達其連線限制，且無法處理新的連接，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]會產生額外`CreateSequenceRefused`錯誤子代碼`netrm:ConnectionLimitReached`，如下列範例所示。  
  
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
 由於 WS-Reliable 訊息是使用 WS-Addressing，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-Reliable 訊息實作可能會產生並傳送 WS-Addressing 錯誤。 本節涵蓋 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 在 WS-Reliable 訊息層明確產生的 WS-Addressing 錯誤：  
  
-   B1601:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]當下列其中一項條件成立時，會產生錯誤訊息定址標頭需要：  
  
    -   訊息缺少 `Sequence` 標頭和 `Action` 標頭。  
  
    -   `CreateSequence` 訊息缺少 `MessageId` 標頭。  
  
    -   `CreateSequence` 訊息缺少 `ReplyTo` 標頭。  
  
-   B1602:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]會產生錯誤動作不支援時遺失訊息`Sequence`標頭，且`Action`不是可辨識的 Ws-reliable 訊息規格中的標頭。  
  
-   B1603:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]會產生錯誤端點無法使用，表示端點不會處理順序根據檢查`CreateSequence`訊息之定址標頭。  
  
## <a name="protocol-composition"></a>通訊協定組合  
  
### <a name="composition-with-ws-addressing"></a>與 WS-Addressing 組合  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 支援兩種版本的 WS-Addressing：WS-Addressing 2004/08 [WS-ADDR] 和 W3C WS-Addressing 1.0 建議 [WS-ADDR-CORE] 和 [WS-ADDR-SOAP]。  
  
 儘管 WS-Reliable 訊息規格只提到 WS-Addressing 2004/08，它並未限制要使用的 WS-Addressing 版本。 下列清單列出適用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的條件約束：  
  
-   R2101： 兩個 Ws-addressing 2004/08 和 Ws-addressing 1.0 可與 WS 可靠傳訊。  
  
-   R2102:A 單一版本的 Ws-addressing 必須在整個指定的 Ws-reliable 訊息序列或一組使用相互關聯的反向序列`wsrm:Offer`機制。  
  
### <a name="composition-with-soap"></a>與 SOAP 組合  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 同時支援 SOAP 1.1 和 SOAP 1.2 搭配 WS-Reliable 訊息一起使用。  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a>與 WS-Security 和 WS-SecureConversation 組合  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 透過安全傳輸 (HTTPS)、與 WS-Security 組合，以及與 WS-Secure Conversation 組合，為 WS-Reliable 訊息序列提供保護。 下列清單列出適用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的條件約束：  
  
-   R2301： 若要保護的個別訊息，除了完整性 Ws-reliable 訊息序列的完整性與機密性[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]必須使用 Ws-secure Conversation。  
  
-   R2302:AWS-必須建立安全對話工作階段中之前建立 Ws-reliable 訊息序列。  
  
-   R2303：如果 WS-Reliable 訊息序列的存留期超過 WS-Secure Conversation 工作階段的存留期，則使用 WS-Secure Conversation 建立的 `SecurityContextToken` 必須透過對應的 WS-Secure Conversation 更新繫結來加以更新。  
  
-   B2304:WS-可信賴傳訊序列或一組相互關聯的反向順序永遠會繫結至單一的 Ws-secureconversation 工作階段。  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 來源會在 `wsse:SecurityTokenReference` 訊息的項目擴充性區段中產生 `CreateSequence` 項目。  
  
-   將工作與 Ws-secure Conversation，R2305:When`CreateSequence`訊息必須包含`wsse:SecurityTokenReference`項目。  
  
## <a name="ws-reliable-messaging-ws-policy-assertion"></a>WS-Reliable 訊息 WS-Policy 判斷提示  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 使用 WS-Reliable 訊息 WS-Policy 判斷提示 `wsrm:RMAssertion` 來描述各項端點功能。 下列清單列出適用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的條件約束：  
  
-   B3001：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會將 `wsrm:RMAssertion` WS-Policy 判斷提示附加至 `wsdl:binding` 元素。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 同時支援附加至 `wsdl:binding` 和 `wsdl:port` 元素。  
  
-   B3002：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 支援下列選用的 WS-Reliable 訊息判斷提示屬性，並在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]`ReliableMessagingBindingElement` 上針對它們提供控制：  
  
    -   `wsrm:InactivityTimeout`  
  
    -   `wsrm:AcknowledgementInterval`  
  
     下列為範例。  
  
    ```xml  
    <wsrm:RMAssertion>  
      <wsrm:InactivityTimeout Milliseconds="600000" />  
      <wsrm:AcknowledgementInterval Milliseconds="200" />  
    </wsrm:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliable-messaging-extension"></a>WS-Reliable 訊息延伸的流量控制  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會透過 WS-Reliable 訊息擴充性，針對序列訊息流量提供其他更嚴格的選擇性控制。  
  
 藉由設定已啟用流量控制`ReliableSessionBindingElement`的`FlowControlEnabled``bool`屬性`true`。 下列清單列出適用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的條件約束：  
  
-   B4001：一旦啟用了可信賴傳訊流量控制，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 就會在 `netrm:BufferRemaining` 標頭的項目擴充性中產生 `SequenceAcknowledgement` 項目。  
  
-   B4002：一旦啟用了可信賴傳訊流量控制，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不會要求 `netrm:BufferRemaining` 中一定得存在 `SequenceAcknowledgement` 項目，如下列範例所示。  
  
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
  
-   B4003：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 使用 `netrm:BufferRemaining` 來指出可信賴傳訊目的地可以緩衝處理的新訊息數量。  
  
-   B4004:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]可靠的訊息處理服務會先調節的可信賴傳訊目的地應用程式都能快速地接收訊息時，傳輸的訊息數目。 可信賴傳訊目的地會緩衝處理訊息，並讓項目值降為 0。  
  
-   B4005：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會產生介於 0 到 4096 (含) 之間的 `netrm:BufferRemaining` 整數值，並讀取介於 0 和 `xs:int` 的 `maxInclusive` 值 214748364 (含) 之間的整數值。  
  
## <a name="message-exchange-patterns"></a>訊息交換模式  
 本節將說明當不同訊息交換模式使用 WS-Reliable 訊息時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的行為。 在每個訊息交換模式中，會考慮下列兩種部署案例：  
  
-   不可定址的啟動器：啟動器位於防火牆後方，回應程式只能透過 HTTP 回應將訊息傳送至啟動器。  
  
-   可定址的啟動器：可將 HTTP 要求同時傳送給啟動器與回應程式，亦即可建立兩個反向 HTTP 連線。  
  
### <a name="one-way-non-addressable-initiator"></a>單向、不可定址啟動器  
  
#### <a name="binding"></a>繫結  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 透過在一個 HTTP 通道上使用一個序列的方式，提供單向的訊息交換模式。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會使用 HTTP 要求將所有訊息從 RMS 傳送至 RMD，並使用 HTTP 回應將所有訊息從 RMD 傳送至 RMS。  
  
#### <a name="createsequence-exchange"></a>CreateSequence 交換  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會產生不含提議的 `CreateSequence` 訊息。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會在建立序列之前，確保 `CreateSequence` 不含提議。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會以 `CreateSequence` 訊息來回覆 `CreateSequenceResponse` 要求。  
  
#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會處理所有訊息回覆的認可，除了 `CreateSequence` 訊息與錯誤訊息以外。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式一律產生獨立認可，以同時回應序列和 `AckRequested` 訊息。  
  
#### <a name="terminatesequence-message"></a>TerminateSequence 訊息  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會將 `TerminateSequence` 視為單向作業，代表 HTTP 回應具有空白主體與 HTTP 202 狀態碼。  
  
### <a name="one-way-addressable-initiator"></a>單向、可定址啟動器  
  
#### <a name="binding"></a>繫結  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 透過在傳入與傳出 HTTP 通道上使用一個序列的方式，提供單向的訊息交換模式。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會使用 HTTP 要求來傳送所有訊息。 所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。  
  
#### <a name="createsequence-exchange"></a>CreateSequence 交換  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會產生不含提議的 `CreateSequence` 訊息。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會在建立序列之前，確保 `CreateSequence` 不含提議。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會透過以 `CreateSequenceResponse` 端點參考發出的 HTTP 要求來傳送 `ReplyTo` 訊息。  
  
### <a name="duplex-addressable-initiator"></a>雙工、可定址啟動器  
  
#### <a name="binding"></a>繫結  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 透過在一個傳入與一個傳出 HTTP 通道上使用兩個序列的方式，提供完全非同步的雙向訊息交換模式。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會使用 HTTP 要求來傳送所有訊息。 所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。  
  
#### <a name="createsequence-exchange"></a>CreateSequence 交換  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會產生內含提議的 `CreateSequence` 訊息。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會在建立序列之前，確保 `CreateSequence` 包含提議。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會依定址為 `CreateSequenceResponse` 之 `CreateSequence` 端點參考的 HTTP 要求來傳送 `ReplyTo`。  
  
#### <a name="sequence-lifetime"></a>序列存留期  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會將兩個序列視為一個全雙工工作階段。  
  
 在產生可挑剔某個序列的錯誤時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 預期遠端端點將同時挑剔兩個序列。 在讀取可挑剔某個序列的錯誤時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 將同時挑剔兩個序列。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可關閉本身的傳出序列並繼續處理其傳入序列中的訊息。 反之，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可以處理傳入序列的關閉作業並繼續傳送其傳出序列中的訊息。  
  
### <a name="request-reply-non-addressable-initiator"></a>要求-回覆、不可定址啟動器  
  
#### <a name="binding"></a>繫結  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 透過在一個 HTTP 通道上使用兩個序列的方式，提供單向、要求-回覆的訊息交換模式。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會使用 HTTP 要求來傳送要求序列的訊息，並透過 HTTP 回應來傳送回覆序列的訊息。  
  
#### <a name="createsequence-exchange"></a>CreateSequence 交換  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會產生內含提議的 `CreateSequence` 訊息。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會在建立序列之前，確保 `CreateSequence` 包含提議。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會以 `CreateSequence` 訊息來回覆 `CreateSequenceResponse` 要求。  
  
#### <a name="one-way-message"></a>單向訊息  
 為了成功完成單向訊息交換通訊協定，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會透過 HTTP 要求傳送要求序列訊息，並透過 HTTP 回應接收獨立的 `SequenceAcknowledgement` 訊息。 `SequenceAcknowledgement` 必須認可傳送的訊息。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式可透過認可、錯誤或是內含空白主體與 HTTP 202 狀態碼的回應來回覆要求。  
  
#### <a name="two-way-messages"></a>雙向訊息  
 為了成功完成雙向訊息交換通訊協定，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會透過 HTTP 要求傳送要求序列訊息，並透過 HTTP 回應接收回覆序列訊息。 回應中必須包含認可傳輸之要求序列訊息的 `SequenceAcknowledgement`。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式可透過應用程式回覆、錯誤或是內含空本文與 HTTP 202 狀態碼的回應來回覆要求。  
  
 由於單向訊息與應用程式回覆時機的緣故，要求序列訊息的序號與回應訊息的序號彼此並未互相關聯。  
  
#### <a name="retrying-replies"></a>重試回覆  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 仰賴 HTTP 要求-回覆相互關聯來執行雙向訊息交換通訊協定的相互關聯作業。 由於這個緣故，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器不會在認可要求序列訊息時停止重試要求序列訊息，而會在 HTTP 回應內含認可、使用者訊息，或是錯誤時，才停止重試要求序列訊息。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會在與回覆相互關聯之要求的 HTTP 要求階段上重試回覆。  
  
#### <a name="lastmessage-exchange"></a>LastMessage 交換  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會在 HTTP 要求階段上產生及傳送主體空白的最後一則訊息。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 需要回應，但會忽略實際的回應訊息。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會透過回覆序列中主體空白的最後一則訊息，回覆要求序列中主體空白的最後一則訊息。  
  
 如果 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式收到的最後一則訊息所包含的動作 URI 不是 http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage，則 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會透過最後一則訊息來回覆。 在雙向訊息交換通訊協定的情況中，最後一則訊息包含應用程式訊息；在單向訊息交換通訊協定的情況中，最後一則訊息包含空白主體。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式不會要求針對回覆序列中主體空白的最後一則訊息進行認可。  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence 交換  
 一旦所有要求都收到有效回覆，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會在 HTTP 要求階段上產生及傳送要求序列的 `TerminateSequence` 訊息。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 需要回應，但會忽略實際的回應訊息。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會透過回覆序列的 `TerminateSequence` 訊息，回覆要求序列的 `TerminateSequence` 訊息。  
  
 在正常的關機序列中，兩個 `TerminateSequence` 訊息會同時包含完整範圍的 `SequenceAcknowledgement`。  
  
### <a name="requestreply-addressable-initiator"></a>要求/回覆、可定址啟動器  
  
#### <a name="binding"></a>繫結  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 透過在一個傳入與一個傳出 HTTP 通道上使用兩個序列的方式，提供要求-回覆訊息交換模式。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會使用 HTTP 要求來傳送所有訊息。 所有的 HTTP 回應都有空本文和 HTTP 202 狀態碼。  
  
#### <a name="createsequence-exchange"></a>CreateSequence 交換  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會產生內含提議的 `CreateSequence` 訊息。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會在建立序列之前，確保 `CreateSequence` 包含提議。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會依定址為 `CreateSequenceResponse` 之 `CreateSequence` 端點參考的 HTTP 要求來傳送 `ReplyTo`。  
  
#### <a name="requestreply-correlation"></a>要求/回覆相互關聯  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會確保所有應用程式要求訊息都帶有 `MessageId` 和 `ReplyTo` 端點參考。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動器會將 `CreateSequence` 訊息的 `ReplyTo` 端點參照套用到每個應用程式要求訊息上。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會要求傳入的要求訊息都帶有 `MessageId` 和 `ReplyTo`。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 回應程式會確保 `CreateSequence` 和所有應用程式要求訊息的端點參照一模一樣。

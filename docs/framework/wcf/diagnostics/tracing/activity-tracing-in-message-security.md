---
title: 訊息安全性中的活動追蹤
ms.date: 03/30/2017
ms.assetid: 68862534-3b2e-4270-b097-8121b12a2c97
ms.openlocfilehash: 4ab34e3a3ef8487a747c9f9dac71a22006ea515a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265007"
---
# <a name="activity-tracing-in-message-security"></a>訊息安全性中的活動追蹤

此主題將說明安全性處理中的活動追蹤 (將於下列三個階段中發生)。  
  
- 交涉/SCT 交換。 這個情況會發生在傳輸層 (透過二進位資料交換) 或訊息層 (透過 SOAP 訊息交換)。  
  
- 訊息加密/解密，包含簽章驗證 (verification) 與驗證 (authentication)。 追蹤項目會在環境活動中發生 (通常是「處理動作」)。  
  
- 授權與驗證 這個情況會在本機或於端點之間進行通訊時發生。  
  
## <a name="negotiationsct-exchange"></a>交涉/SCT 交換  

 在交涉/SCT 交換階段，會在用戶端上建立兩種活動類型：「設定安全工作階段」與「關閉安全工作階段」。 「設定安全工作階段」涵蓋了 RST/RSTR/SCT 訊息交換的追蹤，而「關閉安全工作階段」則包含了取消訊息的追蹤。  
  
 在伺服器上，RST/RSTR/SCT 的每個要求/回覆都會出現在自己的活動中。 如果 `propagateActivity` = `true` 伺服器和用戶端上的活動，伺服器上的活動都有相同的識別碼，並在透過服務追蹤檢視器查看時，出現在「設定安全會話」中。  
  
 此活動追蹤模型可應用在使用者名稱/密碼驗證、憑證驗證，以及 NTLM 驗證上。  
  
 下表列出交涉與 SCT 交換的活動及追蹤。  
  
||交涉/SCT 交換發生的時間|活動|追蹤|  
|-|-------------------------------------------------|----------------|------------|  
|安全傳輸<br /><br /> (HTTPS、SSL)|在收到第一則訊息時。|環境活動中會發出追蹤。|-Exchange 追蹤<br />-已建立安全通道<br />-已取得共用秘密。|  
|安全訊息層<br /><br /> (WSHTTP)|在收到第一則訊息時。|在用戶端上：<br /><br /> -在第一則訊息的「處理動作」中，針對 RST/RSTR/SCT 的每個要求/回復，「設定安全會話」。<br />-[關閉 Proxy 活動] 中的 [取消交換] 的 [關閉安全會話]。 此活動可能出自其他一些環境活動，視安全工作階段關閉時間而定。<br /><br /> 在伺服器上：<br /><br /> -在伺服器上針對 RST/SCT/Cancel 的每個要求/回復，各有一個「處理動作」活動。 如果為 `propagateActivity` = `true` ，則 RST/RSTR/SCT 活動會與「設定安全會話」合併，而「取消」會與用戶端的「關閉」活動合併。<br /><br /> 「設定安全工作階段」共有兩個階段：<br /><br /> 1. 驗證協商。 如果用戶端已經具有適當的認證，則此選項將為選用。 您可以透過安全傳輸或是訊息交換來完成此階段。 在稍後階段，可能發生 1 或 2 次 RST/RSTR 交換。 在這些交換當中，新的要求/回覆活動會按照原先設計發出追蹤。<br />2. 安全會話建立 (SCT) ，其中有一個 RST/RSTR 交換發生于此處。 此交換與先前所述一樣，具備相同的環境活動。|-Exchange 追蹤<br />-已建立安全通道<br />-已取得共用秘密。|  
  
> [!NOTE]
> 在混合式安全性模式中，交涉驗證會於二進位交換中發生，但是 SCT 則是在訊息交換中發生。 在單純的傳輸模式中，交涉只會在不包含額外活動的傳輸中發生。  
  
## <a name="message-encryption-and-decryption"></a>訊息加密與解密  

 下表列出訊息加密/解密，以及簽章驗證的活動及追蹤。  
  
||安全傳輸<br /><br /> (HTTPS、SSL) 與安全訊息層<br /><br /> (WSHTTP)|  
|-|---------------------------------------------------------------------------------|  
|訊息加密/解密，以及簽章驗證發生的時間|在收到訊息時|  
|活動|用戶端與伺服器上的 ProcessAction 活動會發出追蹤。|  
|追蹤|-sendSecurityHeader (寄件者) ：<br />-簽署訊息<br />-加密要求資料<br />-receiveSecurityHeader (接收器) ：<br />-驗證簽章<br />-解密回應資料<br />-驗證|  
  
> [!NOTE]
> 在單純的傳輸模式中，訊息加密/解密只會在不包含額外活動的傳輸中發生。  
  
## <a name="authorization-and-verification"></a>授權與驗證  

 下表列出授權的活動與追蹤。  
  
||發生授權的時間|活動|追蹤|  
|-|-------------------------------------|----------------|------------|  
|本機 (預設)|當伺服器上的訊息解密之後|伺服器上的 ProcessAction 活動會發出追蹤。|使用者已授權。|  
|遠端|當伺服器上的訊息解密之後|由 ProcessAction 活動叫用的新活動會發出追蹤。|使用者已授權。|

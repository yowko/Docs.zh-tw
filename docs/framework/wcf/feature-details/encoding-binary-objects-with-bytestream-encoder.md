---
title: 以位元組資料流編碼器將二進位物件編碼
ms.date: 03/30/2017
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
ms.openlocfilehash: cc63cb8de1e245c3b58fb69819e59cb815b777d3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276733"
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a>以位元組資料流編碼器將二進位物件編碼

使用設定 Windows Communication Foundation (WCF) 來傳送和接收原始二進位資料 <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> 。  
  
## <a name="byte-stream-message-encoder-architecture"></a>位元組資料流訊息編碼器架構  

 WCF 所使用的二進位訊息編碼器沒有處理、驗證或識別訊息中基礎二進位資料的功能。 資料封裝會編碼為 XML，傳送、接收及解碼。 編碼器處理資料的時間，是在資料傳遞到傳輸之後，且在訊息傳送至訊息佇列之前。 在功能上，二進位編碼器會將訊息資料包裝在 `<binary>` 項目中進行傳送，而在訊息接收到之後會移除這些項目。  
  
## <a name="using-the-byte-stream-message-encoder"></a>使用位元組資料流訊息編碼器  

 下列範例示範實作位元組資料流訊息編碼器的服務合約。  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 下列範例示範正在叫用的服務。  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 如果使用實作訊息基礎結構 (例如路由器) 的服務，處理訊息時並不會檢查、驗證訊息，或是與訊息有其他形式的互動，如以下範例所示。  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## <a name="scenarios"></a>案例  

 在下列案例中，位元組資料流編碼器很有用。  
  
- 使用 WCF 在電腦之間傳送 JPEG 影像。 在此案例中，影像將透過外部來源的傳輸送達，而且所傳送的資料是構成影像的未經處理位元組。 服務將會接收二進位資料並顯示影像。  
  
- 從訊息佇列中讀取資訊並加以處理。 系統將從訊息佇列管理員讀取訊息，並且在即將處理的訊息佇列通道中向上傳遞。 訊息佇列通道會作為 WCF 通道堆疊中的佇列管理員。  
  
 如果透過訊息佇列通道傳送訊息，寄件者將無法控制從佇列管理員接收的位元組。 如果接收處理序無法讀取未經處理的位元組，接收的訊息格式將會呈現錯誤而且無法處理。系統會假設接收處理序能夠將接收的位元組轉譯回可用的格式。

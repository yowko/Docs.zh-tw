---
title: 要求資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sending data
- WebRequest class, sending and receiving data
- requesting data from Internet, about requesting data
- WebClient class, sending and receiving data
- network, requesting data
- receiving data
- sending data, about sending data
- response to Internet request, about responding to Internet requests
- data requests
- receiving data, about receiving data
- Internet, requesting data
ms.assetid: df6f1e1d-6f2a-45dd-8141-4a85c3dafe1d
author: mcleblanc
ms.author: markl
ms.openlocfilehash: a163374810cbc06ca048c1bdd304de9519db140c
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47195702"
---
# <a name="requesting-data"></a>要求資料
開發在現今網際網路分散式作業環境中執行的應用程式，需要從所有類型的資源中擷取資料的有效且易用的方法。 可插式通訊協定可讓您開發應用程式，而應用程式使用單一介面來擷取多個網際網路通訊協定中的資料。  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a>從網際網路伺服器上傳和下載資料  
 針對簡單要求和回應交易，<xref:System.Net.WebClient> 類別提供最簡單的模型，將資料上傳至網際網路伺服器，或從中下載資料。 **WebClient** 提供方法來上傳和下載檔案、傳送和接收資料流，並將資料緩衝區傳送至伺服器以及接收回應。 **WebClient** 會使用 <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse> 類別進行實際網際網路資源連線，讓任何註冊的插入式通訊協定可供使用。  
  
 需要使用 **WebRequest** 類別和其子系，從伺服器製作更複雜交易要求資料的用戶端應用程式。 **WebRequest** 會封裝連線至伺服器、傳送要求以及接收回應的詳細資料。 **WebRequest** 是定義一組屬性和方法的抽象類別，而屬性和方法可供使用可插式通訊協定的所有應用程式使用。 **WebRequest** 子系 (例如 <xref:System.Net.HttpWebRequest>) 會使用與基礎通訊協定一致的方式，來實作 **WebRequest** 所定義的屬性和方法。  
  
 **WebRequest** 類別會使用傳遞至其 <xref:System.Net.WebRequest.Create%2A> 方法的 URI 值來建立 **WebRequest** 子系的通訊協定特定執行個體，以判斷要建立的特定衍生類別執行個體。 應用程式指出應該使用哪個 **WebRequest** 子系來處理要求，方法是使用 <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> 方法來註冊子系的建構函式。  
  
 要求網際網路資源的方式是在 **WebRequest** 上呼叫 <xref:System.Net.WebRequest.GetResponse%2A> 方法。 **GetResponse** 方法會從 **WebRequest** 的屬性建構通訊協定特定要求，並建立與伺服器的 TCP 或 UDP 通訊端連線，然後傳送要求。 針對將資料傳送至伺服器的要求 (例如 HTTP **Post** 或 FTP **Put** 要求)，<xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> 方法提供在其中傳送資料的網路資料流。  
  
 **GetResponse** 方法會傳回符合 **WebRequest** 的通訊協定特定 **WebResponse**。  
  
 **WebResponse** 類別也是定義屬性和方法的抽象類別，而屬性和方法可供使用可插式通訊協定的所有應用程式使用。 **WebResponse** 子系會針對基礎通訊協定實作這些屬性和方法。 例如，<xref:System.Net.HttpWebResponse> 類別實作 **WebResponse** 類別來進行 HTTP。  
  
 向 <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> 方法所傳回資料流中的應用程式呈現伺服器所傳回的資料。 您可以像使用任何其他資料流的方式一樣來使用此資料流，如下列範例所示。  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a>請參閱  
 [以 .NET Framework 進行網路程式設計](../../../docs/framework/network-programming/index.md)  
 [如何：要求網頁並擷取結果當作資料流](../../../docs/framework/network-programming/how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)  
 [如何：擷取符合 WebRequest 的通訊協定特定 WebResponse](../../../docs/framework/network-programming/how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)

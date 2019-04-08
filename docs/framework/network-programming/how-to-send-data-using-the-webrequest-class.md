---
title: 作法：使用 WebRequest 類別傳送資料
ms.date: 03/25/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: 6d7a2e52177c05ead6300e775021572f3a64340a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822250"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a>作法：使用 WebRequest 類別傳送資料
下列程序描述將資料傳送到伺服器的步驟。 本程序通常用於在網頁上張貼資料。 
  
## <a name="to-send-data-to-a-host-server"></a>將資料傳送到主機伺服器  
  
1.  使用接受資料之資源 (例如，指令碼或 ASP.NET 網頁) 的 URI 呼叫 <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>，以建立 <xref:System.Net.WebRequest> 執行個體。 例如： 
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")  
    ```  
  
    > [!NOTE]
    > .NET Framework 針對以 *http:*、*https:*、*ftp:* 和 *file:* 開頭的 URI，提供了衍生自 <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse> 類別的通訊協定專用類別。
    如果您需要設定或讀取通訊協定專用屬性，必須將 <xref:System.Net.WebRequest> 或 <xref:System.Net.WebResponse> 物件轉換為通訊協定專用物件類型。 如需詳細資訊，請參閱[可插式通訊協定程式設計](programming-pluggable-protocols.md)。 
  
2.  在 `WebRequest` 物件中設定任何需要的屬性值。 例如，若要啟用驗證，請將 <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> 屬性設定為 <xref:System.Net.NetworkCredential> 類別的執行個體：
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
3.  指定允許資料與要求一起傳送的通訊協定方法，例如 HTTP `POST` 方法：  
  
    ```csharp  
    request.Method = "POST";  
    ```  
  
    ```vb  
    request.Method = "POST"  
    ```  
  
4.  將 <xref:System.Web.HttpRequest.ContentLength> 屬性設定為您要求中包含的位元組數目。 例如： 
  
    ```csharp  
    request.ContentLength = byteArray.Length;  
    ```  
  
    ```vb  
    request.ContentLength = byteArray.Length  
    ```  
  
5.  將 <xref:System.Web.HttpRequest.ContentType> 屬性設定為適當值。 例如：
  
    ```csharp  
    request.ContentType = "application/x-www-form-urlencoded";  
    ```  
  
    ```vb  
    request.ContentType = "application/x-www-form-urlencoded"  
    ```  
  
6.  藉由呼叫 <xref:System.Net.WebRequest.GetRequestStream%2A> 方法，取得保留要求資料的資料流。 例如：
  
    ```csharp  
    Stream dataStream = request.GetRequestStream();  
    ```  
  
    ```vb  
    Stream dataStream = request.GetRequestStream()  
    ```  
  
7.  將資料寫入 `GetRequestStream` 方法所傳回的 <xref:System.IO.Stream> 物件。 例如：
  
    ```csharp  
    dataStream.Write(byteArray, 0, byteArray.Length);  
    ```  
  
    ```vb  
    dataStream.Write(byteArray, 0, byteArray.Length)  
    ```  
  
8.  呼叫 <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> 方法來關閉要求資料流。 例如：
  
    ```csharp  
    dataStream.Close();  
    ```  
  
    ```vb  
    dataStream.Close()  
    ```  
  
9. 藉由呼叫 <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>，將要求傳送到伺服器。 這個方法會傳回包含伺服器回應的物件。 傳回的 `WebResponse` 物件類型取決於要求 URI 的配置。 例如：
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
10. 您可以存取 `WebResponse` 物件的屬性，或將其轉換為通訊協定專用執行個體，以讀取通訊協定專用屬性。 

    例如，若要存取 <xref:System.Net.HttpWebResponse> 的 HTTP 專用屬性，請將 `WebResponse` 物件轉換為 <xref:System.Net.HttpWebResponse> 參考。 下列程式碼範例示範如何顯示與回應一起傳送的 HTTP 專用 <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> 屬性：
  
    ```csharp  
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);    
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. 若要取得含有伺服器所傳送之回應資料的資料流，請呼叫 `WebResponse` 物件的 <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> 方法。 例如：
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
12. 從回應物件讀取資料之後，請使用 <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> 方法關閉它，或使用 <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> 方法關閉回應資料流。 如果不關閉回應或資料流，應用程式可能會耗盡伺服器連線，而變得無法處理其他要求。 `WebResponse.Close` 方法在關閉回應時會呼叫 `Stream.Close`，因此不需要對回應和資料流物件呼叫 `Close`，但是這麼做也不會造成損害。 例如：
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a>範例  
  
下列程式碼範例示範如何將資料傳送到網頁伺服器，並讀取其回應中的資料：  

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

  
## <a name="see-also"></a>另請參閱
- [建立網際網路要求](creating-internet-requests.md)
- [在網路上使用資料流](using-streams-on-the-network.md)
- [透過 Proxy 存取網際網路](accessing-the-internet-through-a-proxy.md)
- [要求資料](requesting-data.md)
- [如何：使用 WebRequest 類別要求資料](how-to-request-data-using-the-webrequest-class.md)

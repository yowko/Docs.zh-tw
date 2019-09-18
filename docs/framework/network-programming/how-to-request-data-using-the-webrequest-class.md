---
title: HOW TO：使用 WebRequest 類別要求資料
ms.date: 03/21/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- downloading Internet resources, steps
- requesting data from Internet, steps
- WebRequest class, receiving data
- receiving data, using WebRequest class
- Internet, requesting data
ms.assetid: 368b8d0f-dc5e-4469-a8b8-b2adbf5dd800
ms.openlocfilehash: e670a2a503ce704eff847e9e0b3ee340ab52fe62
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048158"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a>HOW TO：使用 WebRequest 類別要求資料

下列程序描述向伺服器要求資源 (例如網頁或檔案) 的步驟。 資源必須是以 URI 識別。

## <a name="to-request-data-from-a-host-server"></a>向主機伺服器要求資料

1. 使用資源的 URI 來呼叫 <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>，以建立 <xref:System.Net.WebRequest> 執行個體。 例如：

    ```csharp
    WebRequest request = WebRequest.Create("https://docs.microsoft.com");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("https://docs.microsoft.com")
    ```

    > [!NOTE]
    > .NET Framework 針對以 *http:* 、*https:* 、*ftp:* 和 *file:* 開頭的 URI，提供了衍生自 <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse> 類別的通訊協定專用類別。

    如果您需要設定或讀取通訊協定專用屬性，必須將 <xref:System.Net.WebRequest> 或 <xref:System.Net.WebResponse> 物件轉換為通訊協定專用物件類型。 如需詳細資訊，請參閱[可插式通訊協定程式設計](programming-pluggable-protocols.md)。

2. 在 `WebRequest` 物件中設定任何需要的屬性值。 例如，若要啟用驗證，請將 <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> 屬性設定為 <xref:System.Net.NetworkCredential> 類別的執行個體：

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. 藉由呼叫 <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>，將要求傳送到伺服器。 這個方法會傳回包含伺服器回應的物件。 傳回的 <xref:System.Net.WebResponse> 物件類型取決於要求 URI 的配置。 例如：

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

4. 您可以存取 `WebResponse` 物件的屬性，或將其轉換為通訊協定專用執行個體，以讀取通訊協定專用屬性。

    例如，若要存取 <xref:System.Net.HttpWebResponse> 的 HTTP 專用屬性，請將 `WebResponse` 物件轉換為 `HttpWebResponse` 參考。 下列程式碼範例示範如何顯示與回應一起傳送的 HTTP 專用 <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> 屬性：

    ```csharp
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)
    ```

5. 若要取得含有伺服器所傳送之回應資料的資料流，請呼叫 <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> 方法。 例如：

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

6. 從回應物件讀取資料之後，請使用 <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> 方法關閉它，或使用 <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> 方法關閉回應資料流。 如果不關閉回應物件或資料流，應用程式可能會耗盡伺服器連線，而變得無法處理其他要求。 `WebResponse.Close` 方法在關閉回應時會呼叫 `Stream.Close`，因此不需要對回應和資料流物件呼叫 `Close`，但是這麼做也不會造成損害。 例如：

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a>範例

下列程式碼範例示範如何對網頁伺服器建立要求，並讀取其回應中的資料：

[!code-csharp[RequestDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/RequestDataUsingWebRequest/cs/WebRequestGetExample.cs)]
[!code-vb[RequestDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/RequestDataUsingWebRequest/vb/WebRequestGetExample.vb)]

## <a name="see-also"></a>另請參閱

- [建立網際網路要求](creating-internet-requests.md)
- [在網路上使用資料流](using-streams-on-the-network.md)
- [透過 Proxy 存取網際網路](accessing-the-internet-through-a-proxy.md)
- [要求資料](requesting-data.md)
- [如何：使用 WebRequest 類別傳送資料](how-to-send-data-using-the-webrequest-class.md)

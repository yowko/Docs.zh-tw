---
title: 衍生自 WebRequest
ms.date: 03/30/2017
helpviewer_keywords:
- WebRequest class, pluggable protocols
- protocol-specific request handler
- sending data, pluggable protocols
- pluggable protocols, class criteria
- Internet, pluggable protocols
- receiving data, pluggable protocols
- protocols, pluggable
ms.assetid: 9810c177-973e-43d7-823c-14960bd625ea
ms.openlocfilehash: f840e042321b636443b6763e168abd144b05edae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717450"
---
# <a name="deriving-from-webrequest"></a>衍生自 WebRequest
<xref:System.Net.WebRequest> 類別是抽象的基底類別，提供基本的方法和屬性以建立特定通訊協定要求，其符合 .NET Framework 插入式通訊協定模型的處理常式。 使用 **WebRequest** 類別的應用程式可以使用任何支援的通訊協定要求資料，不需要指定使用的通訊協定。  
  
 為使特定通訊協定類別用為插入式通訊協定，必須符合兩個準則：類別必須實作 <xref:System.Net.IWebRequestCreate> 介面，且必須使用 <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> 方法登錄。 類別必須覆寫 **WebRequest** 所有的抽象方法和屬性，才能提供插入式介面。  
  
 **WebRequest** 執行個體僅供單次使用，如果您想要提出另一項要求，請建立新的 **WebRequest**。 **WebRequest** 支援 <xref:System.Runtime.Serialization.ISerializable> 介面，可讓開發人員序列化範本 **WebRequest**，然後重新建構其他要求的範本。  
  
## <a name="iwebrequest-create-method"></a>IWebRequest 建立方法  
 <xref:System.Net.IWebRequestCreate.Create%2A> 方法負責初始化特定通訊協定類別的新執行個體。 建立新的 **WebRequest** 時，<xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> 方法會比對要求的 URI 和以 **RegisterPrefix** 方法登錄的 URI 前置詞。 正確特定通訊協定子代的 **Create** 方法，必須傳回能夠執行通訊協定標準要求/回應交易的子代初始化執行個體，不需要修改特定通訊協定的任何欄位。  
  
## <a name="connectiongroupname-property"></a>ConnectionGroupName 屬性  
 <xref:System.Net.WebRequest.ConnectionGroupName%2A> 屬性用於命名一組對資源的連線，以便透過單一連線提出多項要求。 若要實作連線共用，您必須使用共用和指派連線的特定通訊協定方法。 例如，提供的 <xref:System.Net.ServicePointManager> 類別會實作 <xref:System.Net.HttpWebRequest> 類別的連線共用。 **ServicePointManager** 類別會建立 <xref:System.Net.ServicePoint>，為每個連線群組提供特定伺服器的連線。  
  
## <a name="contentlength-property"></a>ContentLength 屬性  
 <xref:System.Net.WebRequest.ContentLength%2A> 屬性指定的資料位元組數目，會在上傳資料時傳送到伺服器。  
  
 一般必須設定 <xref:System.Net.WebRequest.Method%2A> 屬性，以指出當 **ContentLength** 屬性設定為大於零的值時，上傳正在進行中。  
  
## <a name="contenttype-property"></a>ContentType 屬性  
 <xref:System.Net.WebRequest.ContentType%2A> 屬性會提供您的通訊協定要求您傳送至伺服器的任何特殊資訊，以識別您要傳送的內容類型。 這通常是任何上傳資料的 MIME 內容類型。  
  
## <a name="credentials-property"></a>Credentials 屬性  
 <xref:System.Net.WebRequest.Credentials%2A> 屬性包含向伺服器驗證要求所需要的資訊。 您必須為您的通訊協定實作驗證程序的詳細資料。 <xref:System.Net.AuthenticationManager> 類別負責驗證要求及提供驗證權杖。 提供您通訊協定所用認證的類別，必須實作 <xref:System.Net.ICredentials> 介面。  
  
## <a name="headers-property"></a>Headers 屬性  
 <xref:System.Net.WebRequest.Headers%2A> 屬性包含與要求建立關聯的中繼資料名稱/值組任意集合。 **Headers** 屬性可以包含可表示為名稱/值組的通訊協定所需要的任何中繼資料。 通常必須先設定這項資訊，再呼叫 <xref:System.Net.WebRequest.GetRequestStream%2A> 或 <xref:System.Net.WebRequest.GetResponse%2A> 方法；一旦提出要求，中繼資料即視為唯讀。  
  
 您不需要使用 **Headers** 屬性，也能使用標頭中繼資料。 通訊協定特定的中繼資料可以公開為屬性。例如，<xref:System.Net.HttpWebRequest.UserAgent%2A?displayProperty=nameWithType> 屬性會公開 **User-Agent** HTTP 標頭。 當您將標頭中繼資料公開為屬性時，您不應該允許使用 **Headers** 屬性設定相同的屬性。  
  
## <a name="method-property"></a>Method 屬性  
 <xref:System.Net.WebRequest.Method%2A> 屬性包含要求會要求伺服器執行的動詞或動作。 **Method** 屬性的預設值必須啟用標準的要求/回應動作，不需要設定任何通訊協定特有的屬性。 例如，<xref:System.Net.HttpWebResponse.Method%2A> 方法預設為 GET，會從網頁伺服器要求資源並傳回回應。  
  
 當 **Method** 屬性設定為動詞或動作，指出上傳正在進行中時，**ContentLength** 屬性一般必須設定成大於零的值。  
  
## <a name="preauthenticate-property"></a>PreAuthenticate 屬性  
 應用程式設定 <xref:System.Net.WebRequest.PreAuthenticate%2A> 屬性，指出驗證資訊應該隨初始要求一起傳送，而不是等待驗證挑戰。 只有當通訊協定支援隨初始要求一起傳送驗證認證時，**PreAuthenticate** 屬性才有意義。  
  
## <a name="proxy-property"></a>Proxy 屬性  
 <xref:System.Net.WebRequest.Proxy%2A> 屬性包含存取要求資源所使用的 <xref:System.Net.IWebProxy> 介面。 只有當通訊協定支援 Proxy 的要求時，**Proxy** 屬性才有意義。 如果您的通訊協定要求，您就必須設定預設的 Proxy。  
  
 在某些環境中，例如公司的防火牆後端，您的通訊協定可能要求使用 Proxy。 在此情況下，您必須實作 **IWebProxy** 介面來建立適用於您通訊協定的 proxy 類別。  
  
## <a name="requesturi-property"></a>RequestUri 屬性  
 <xref:System.Net.WebRequest.RequestUri%2A> 屬性包含的 URI 已傳遞至 **WebRequest.Create** 方法。 它是唯讀的，且一旦建立 **WebRequest** 即無法變更。 如果您的通訊協定支援重新導向，回應可能來自不同 URI 所識別的資源。 如果您需要提供對所回應 URI 的存取權，即必須提供包含該 URI 的額外屬性。  
  
## <a name="timeout-property"></a>Timeout 屬性  
 <xref:System.Net.WebRequest.Timeout%2A> 屬性包含要求逾時及擲回例外狀況所需等候的時間長度，以毫秒為單位。 **Timeout** 僅適用於以 <xref:System.Net.WebRequest.GetResponse%2A> 方法提出的同步要求，非同步要求必須使用 <xref:System.Net.WebRequest.Abort%2A> 方法來取消暫止的要求。  
  
 只有當特定通訊協定類別實作逾時處理序時，設定 **Timeout** 屬性才有意義。  
  
## <a name="abort-method"></a>Abort 方法  
 <xref:System.Net.WebRequest.Abort%2A> 方法會取消伺服器的暫止非同步要求。 取消要求之後，呼叫 **GetResponse**、**BeginGetResponse**、**EndGetResponse**、**GetRequestStream**、**BeginGetRequestStream** 或 **EndGetRequestStream** 會擲回將 <xref:System.Net.WebException.Status%2A> 屬性設為 <xref:System.Net.WebExceptionStatus> 的 <xref:System.Net.WebException>。  
  
## <a name="begingetrequeststream-and-endgetrequeststream-methods"></a>BeginGetRequestStream 和 EndGetRequestStream 方法  
 <xref:System.Net.WebRequest.BeginGetRequestStream%2A> 方法會啟動資料流的非同步要求，用來將資料上傳到伺服器。 <xref:System.Net.WebRequest.EndGetRequestStream%2A> 方法會完成非同步要求，並傳回所要求的資料流。 這些方法會實作使用標準 .NET Framework 非同步模式的 **GetRequestStream** 方法。  
  
## <a name="begingetresponse-and-endgetresponse-methods"></a>BeginGetResponse 和 EndGetResponse 方法  
 <xref:System.Net.WebRequest.BeginGetResponse%2A> 方法會啟動伺服器的非同步要求。 <xref:System.Net.WebRequest.EndGetResponse%2A> 方法會完成非同步要求，並傳回所要求的回應。 這些方法會實作使用標準 .NET Framework 非同步模式的 **GetResponse** 方法。  
  
## <a name="getrequeststream-method"></a>GetRequestStream 方法  
 <xref:System.Net.WebRequest.GetRequestStream%2A> 方法會傳回資料流，用來將資料寫入要求的伺服器。 傳回的資料流應該是不會搜尋的唯寫資料流，它原來是要寫入伺服器的單向資料流資料。 資料流針對 <xref:System.IO.Stream.CanRead%2A> 和 <xref:System.IO.Stream.CanSeek%2A> 屬性傳回 false，針對 <xref:System.IO.Stream.CanWrite%2A> 屬性傳回 true。  
  
 **GetRequestStream** 方法通常會開啟伺服器連線，並在傳回資料流之前，先傳送標頭資訊，指出正將該資料傳送到伺服器。 因為是 **GetRequestStream** 開始的要求，所以通常不允許在呼叫 **GetRequestStream** 之後設定任何 **Header** 屬性或 **ContentLength** 屬性。  
  
## <a name="getresponse-method"></a>GetResponse 方法  
 <xref:System.Net.WebRequest.GetResponse%2A> 方法會傳回 <xref:System.Net.WebResponse> 類別的特定通訊協定子代，表示伺服器的回應。 除非 **GetRequestStream** 方法已起始要求，否則 **GetResponse** 方法會建立 **RequestUri** 所識別的資源連線，傳送標頭資訊，指出正在提出的要求類型，然後從資源接收回應。  
  
 一旦呼叫了 **GetResponse**，所有屬性都應該視為唯讀。 **WebRequest** 執行個體僅供單次使用，如果您想要提出另一項要求，您應該建立新的 **WebRequest**。  
  
 **GetResponse** 方法負責建立適當的 **WebResponse** 子代，以包含傳入的回應。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Net.WebRequest>
- <xref:System.Net.HttpWebRequest>
- <xref:System.Net.FileWebRequest>
- [可插式通訊協定程式設計](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
- [衍生自 WebResponse](../../../docs/framework/network-programming/deriving-from-webresponse.md)

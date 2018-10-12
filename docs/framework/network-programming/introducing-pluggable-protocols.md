---
title: 可插式通訊協定簡介
ms.date: 03/30/2017
helpviewer_keywords:
- data requests, pluggable protocols
- WebRequest class, pluggable protocols
- response to Internet request, pluggable protocols
- URI
- Windows Sockets
- request/response model
- sending data, pluggable protocols
- pluggable protocols
- WebClient class, about WebClient class
- pluggable protocols, about pluggable protocols
- Internet, pluggable protocols
- path identifiers
- Uniform Resource Identifier
- application development [.NET Framework], pluggable protocols
- requesting data from Internet, pluggable protocols
- receiving data, pluggable protocols
- protocols, pluggable
- server identifiers
- scheme identifiers
ms.assetid: 4b48e22d-e4e5-48f0-be80-d549bda97415
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 7fcc3c78192866ecbcefe03573d3e253ac6b6138
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47198419"
---
# <a name="introducing-pluggable-protocols"></a>可插式通訊協定簡介
Microsoft .NET Framework 提供有層次、可擴充和網際網路服務的 Managed 實作，可以迅速而簡易地整合到您的應用程式。 <xref:System.Net> 和 <xref:System.Net.Sockets> 命名空間中的網際網路存取類別，可用來實作 Web 架構和以網際網路為基礎的應用程式。  
  
## <a name="internet-applications"></a>網際網路應用程式  
 網際網路應用程式可以概分為兩類：要求資訊的用戶端應用程式，和回應用戶端資訊要求的伺服器應用程式。 傳統的網際網路用戶端/伺服器應用程式是全球資訊網，使用者使用瀏覽器在此存取儲存在全球網頁伺服器上的文件和其他資料。  
  
 應用程式並不限於其中一個角色。例如，熟悉的中介層應用程式伺服器回應用戶端要求的方法是向另一部伺服器要求資料，在此情況下，它同時擔任伺服器和用戶端。  
  
 用戶端應用程式透過識別要求的網際網路資源以及用於要求和回應的通訊協定，提出要求。 必要時，用戶端也會提供完成要求所需的任何其他資料，例如 Proxy 位置或驗證資訊 (使用者名稱、密碼等等)。 一旦形成要求，就可將要求傳送到伺服器。  
  
## <a name="identifying-resources"></a>識別資源  
 .NET Framework 使用統一資源識別碼 (URI)，識別所要求的網際網路資源與通訊協定。 URI 包含至少三個片段，可能四個：配置識別碼，識別要求和回應的通訊協定；伺服器識別碼，由網域名稱系統 (DNS) 主機名稱，或在網際網路上可唯一識別伺服器的 TCP 位址；路徑識別碼，找出伺服器上要求的資訊；以及選擇性查詢字串，將資訊從用戶端傳遞至伺服器。 例如，URI `http://www.contoso.com/whatsnew.aspx?date=today` 的構成為配置識別碼 "http"、伺服器識別碼 "www.contoso.com"、路徑 "/whatsnew.aspx" 和查詢字串 "?date=today"。  
  
 伺服器收到要求並處理回應之後，它會將回應傳回到用戶端應用程式。 此回應包含補充資訊，例如內容類型 (例如，未經處理文字或 XML 資料)。  
  
## <a name="requests-and-responses-in-the-net-framework"></a>.NET Framework 中的要求和回應  
 .NET Framework 使用特定的類別提供透過要求/回應模型存取網際網路資源的三段必要資訊：<xref:System.Uri> 類別，包含您所尋找之網際網路資源的 URI；<xref:System.Net.WebRequest> 類別，包含資源的要求；以及 <xref:System.Net.WebResponse> 類別，提供連入回應的容器。  
  
 用戶端應用程式藉由將網路資源的 URI 傳遞到 <xref:System.Net.WebRequest.Create%2A> 方法，建立 `WebRequest` 執行個體。 這個靜態方法會為特定的通訊協定建立 `WebRequest`，例如 HTTP。 傳回的 `WebRequest` 可讓您存取屬性，同時控制伺服器的要求和提出要求時傳送的資料流存取。 `WebRequest` 上的 <xref:System.Net.WebRequest.GetResponse%2A> 方法會將要求從用戶端應用程式傳送至在 URI 中找到的伺服器。 如果回應可能延遲，則可在 **WebRequest** 上使用 <xref:System.Net.WebRequest.BeginGetResponse%2A> 方法以非同步方式提出要求，稍後使用 <xref:System.Net.WebRequest.EndGetResponse%2A> 方法傳回回應。  
  
 **GetResponse** 和 **EndGetResponse** 方法傳回的 **WebResponse**，可讓您存取伺服器傳回的資料。 因為此資料是 <xref:System.Net.WebResponse.GetResponseStream%2A> 方法以資料流的形式提供給提出要求的應用程式，所以可用於應用程式中任何使用資料流的位置。  
  
 **WebRequest** 和 **WebResponse** 類別是可插式通訊協定的基礎：這是一項網路服務實作，可讓您開發應用程式使用網際網路資源，而不用擔心每項資源所使用的通訊協定特定詳細資料。 **WebRequest** 的子代類別是向 **WebRequest** 類別註冊，以管理建立網際網路資源實際連線的詳細資料。  
  
 例如，<xref:System.Net.HttpWebRequest> 類別管理使用 HTTP 連線到網際網路資源的詳細資料。 根據預設，當 **WebRequest.Create** 方法遇到開頭為 "http:" 或 "https:" (HTTP 與安全的 HTTP 通訊協定識別碼) 的 URI 時，傳回的 **WebRequest** 可依現況使用，或將類型轉換成 **HttpWebRequest** 以存取通訊協定特有的屬性。 在大部分情況下，**WebRequest** 會提供提出要求的所有必要資訊。  
  
 可以要求/回應交易表示的任何通訊協定都可用於 **WebRequest**。 您也可以從 **WebRequest** 和 **WebResponse** 衍生通訊協定特定類別，然後註冊它們供應用程式搭配靜態 <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> 方法使用。  
  
 當用於網際網路要求的用戶端驗證為必要時，**WebRequest** 的 <xref:System.Net.WebRequest.Credentials%2A> 屬性會提供所需的認證。 這些認證可以是基本 HTTP 或摘要式驗證的簡單名稱/密碼組，或者是 NTLM 或 Kerberos 驗證的名稱/密碼/網域集。 一組認證可以儲存在 <xref:System.Net.NetworkCredential> 執行個體中，或多組認證同時儲存在 <xref:System.Net.CredentialCache> 執行個體中。 **CredentialCache** 使用要求的 URI 和伺服器支援的驗證配置，以判斷要傳送到伺服器的認證。  
  
## <a name="simple-requests-with-webclient"></a>使用 WebClient 的簡單要求  
 凡是需要提出網際網路資源簡單要求的應用程式，<xref:System.Net.WebClient> 類別都會提供常見方法，在網際網路伺服器上傳資料或下載資料。 **WebClient** 依賴 **WebRequest** 類別提供對網際網路資源的存取；因此，**WebClient** 類別可以使用任何已註冊的可插式通訊協定。  
  
 對於無法使用要求/回應模型的應用程式，或需要接聽網路以及傳送要求的應用程式，**System.Net.Sockets**命名空間會提供 <xref:System.Net.Sockets.TcpClient>、<xref:System.Net.Sockets.TcpListener> 和 <xref:System.Net.Sockets.UdpClient> 類別。 這些類別會處理使用不同的傳輸通訊協定建立連線的詳細資料，並將應用程式的網路連線公開為資料流。  
  
 熟悉 Windows Sockets 介面的開發人員，或需要在通訊端層級由程式設計提供控制項的開發人員，會發現 **System.Net.Sockets** 類別符合他們的需要。 **System.Net.Sockets** 類別是在 **System.Net** 類別內從 Managed 程式碼到原生程式碼的轉換點。 在大部分情況下，**System.Net.Sockets** 類別會將資料封送處理到其 Windows 32 位元的對應項目，以及處理任何必要的安全性檢查。  
  
## <a name="see-also"></a>請參閱  
 [可插式通訊協定程式設計](../../../docs/framework/network-programming/programming-pluggable-protocols.md)  
 [以 .NET Framework 進行網路程式設計](../../../docs/framework/network-programming/index.md)  
 [網路程式設計範例](../../../docs/framework/network-programming/network-programming-samples.md)  
 [MSDN Code Gallery 上的 .NET 網路範例](https://code.msdn.microsoft.com/Wiki/View.aspx?ProjectName=nclsamples)

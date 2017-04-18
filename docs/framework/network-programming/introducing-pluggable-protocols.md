---
title: "可插式通訊協定簡介 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "資料要求，可插式通訊協定"
  - "WebRequest 類別，可插式通訊協定"
  - "網際網路要求回應，可插式通訊協定"
  - "URI"
  - "Windows Sockets"
  - "要求/回應模型"
  - "傳送資料，可插式通訊協定"
  - "可插式通訊協定"
  - "WebClient 類別，關於 WebClient 類別"
  - "可插式通訊協定，關於可插式通訊協定"
  - "網際網路，可插式通訊協定"
  - "路徑識別項"
  - "統一資源識別項"
  - "應用程式開發 [.NET Framework]，可插式通訊協定"
  - "從網際網路要求資料，可插式通訊協定"
  - "接收資料，可插式通訊協定"
  - "通訊協定，可插式"
  - "伺服器識別項"
  - "配置識別項"
ms.assetid: 4b48e22d-e4e5-48f0-be80-d549bda97415
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# 可插式通訊協定簡介
. Microsoft .NET Framework 提供一層，可擴充，並處置的網際網路服務的實作可以快速輕鬆地整合到您的應用程式。  在 <xref:System.Net> 的網際網路存取類別和 <xref:System.Net.Sockets> 命名空間可用來實作網路和網際網路架構的應用程式。  
  
## 網際網路應用程式  
 網際網路應用程式可廣泛地分為兩種:要求的用戶端應用程式資訊和回應訊息的伺服器應用程式向用戶端要求。  一般網際網路用戶端與伺服器應用程式為全球資訊網協會，人存取檔案和其他資料的使用瀏覽器儲存在 Web 伺服器全球各地。  
  
 應用程式並不限於一個角色，例如，熟悉的中介層應用程式伺服器回應來自用戶端的要求透過要求從另一個伺服器上的資料，在這種情況下，它為伺服器和用戶端的情況下。  
  
 用戶端應用程式可以識別要求的網際網路資源和通訊協定的要求和回應使用提出要求。  如果需要，用戶端也提供需要的任何其他資料完成要求，例如 Surrogate 位置或驗證資訊 \(使用者名稱，密碼，依此類推\)。  所要求的格式，可以要求傳送至伺服器。  
  
## 識別資源  
 .NET Framework 使用統一資源識別元 \(URI\) \(URI\) 識別要求的網際網路資源的通訊協定。  URI 包括三個，也有可能是四個區段:配置識別項，識別要求和回應的通訊協定，伺服器識別項，包括網域名稱系統 \(DNS\) \(DNS\) 主機名稱或位址 TCP 唯一識別在網際網路上的伺服器，路徑識別項，偵測到需要的資訊，伺服器以及選擇性的查詢字串，則伺服器會將來自用戶端的相關資訊。  例如， URI 「http:\/\/www.contoso.com\/whatsnew.aspx?date\=today」包括配置識別項「http」，伺服器識別項「www.contoso.com」，路徑「\/whatsnew.aspx」和查詢字串「? date\=today」。  
  
 在伺服器收到要求並處理回應之後，它會傳回至用戶端應用程式的回應。  回應包含補充資訊，例如內容類型 \(例如未經處理的文字或 XML 資料，\)。  
  
## 要求和回應在 .NET Framework  
 .NET Framework 使用具象類別提供需要的三項資訊透過要求\/回應模型存取網際網路資源: <xref:System.Uri> 類別，包含網際網路資源的 URI 您搜尋， <xref:System.Net.WebRequest> 類別，包含要求資源;然後 <xref:System.Net.WebResponse> 類別，提供連入回應提供容器 \(Container\)。  
  
 用戶端應用程式可以透過網路資源的 URI 建立 `WebRequest`<xref:System.Net.WebRequest.Create%2A> 執行個體傳遞至方法。  這個靜態方法會建立特定通訊協定，例如 HTTP 的 `WebRequest` 。  傳回的 `WebRequest` 提供對控制項儲存至資料流的要求至伺服器和存取所傳送的屬性，當提出要求時。  在 `WebRequest` 的 <xref:System.Net.WebRequest.GetResponse%2A> 方法由用戶端應用程式的要求至 URI 識別的伺服器。  在回應中可能會延遲的情況下，要求可以進行非同步使用 <xref:System.Net.WebRequest.BeginGetResponse%2A> 方法在 **WebRequest**，使用方法， <xref:System.Net.WebRequest.EndGetResponse%2A> ，而且回應之後可以傳回。  
  
 **GetResponse** 和 **EndGetResponse** 方法會提供對伺服器所傳回之資料的 **WebResponse** 。  由於這項資料提供給要求的應用程式為資料流。 <xref:System.Net.WebResponse.GetResponseStream%2A> 方法，可用於任何應用程式資料流使用。  
  
 **WebRequest** 和 **WebResponse** 類別是可外掛式通訊協定的基礎—讓您開發應用程式使用網際網路資源，而不讓通訊協定特定詳細資料的每個資源使用擔心網路服務的實作。  **WebRequest** 子代類別 **WebRequest** 向註冊類別處理常式建立對網際網路資源的實際連接詳細資料。  
  
 例如，使用 HTTP， <xref:System.Net.HttpWebRequest> 類別管理詳細資料連接至網際網路資源。  根據預設，在中，當從「http 開始的 **WebRequest.Create** 方法遇到 URI: 」或「https: 」\(的 HTTP 通訊協定識別項和安全 HTTP\)，傳回的 **WebRequest** 可以使用像是或可以轉換成 **HttpWebRequest** 存取通訊協定的特定屬性。  在許多情況下， **WebRequest** 針對要求提供所有必要的資訊。  
  
 可以表示為要求\/回應交易的任何通訊協定可用來 **WebRequest**。  您可以從 **WebRequest** 和 **WebResponse** 衍生通訊協定的特定類別會註冊它們適用於靜態 <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=fullName> 方法的應用程式使用。  
  
 當需要網際網路要求的用戶端授權， **WebRequest** 的 <xref:System.Net.WebRequest.Credentials%2A> 屬性提供必要的認證。  這些憑證可以是基本 HTTP 的簡單名稱\/密碼為或摘要式驗證或使用 NTLM 或 Kerberos 驗證設定名稱\/密碼\/網域。  一組認證在 [NetworkCredentials](frlrfsystemnetnetworkcredentialclasstopic) 執行個體可以儲存多個集合，或在 <xref:System.Net.CredentialCache> 執行個體可以同時儲存。  **CredentialCache** 使用伺服器支援判斷要求和驗證配置的 URI 傳送哪個認證傳遞至伺服器。  
  
## 與 Web 用戶端的簡單的需求  
 需要進行簡單的需求網際網路資源的應用程式， <xref:System.Net.WebClient> 類別提供上載資料至或下載資料提供常用的方法是從網際網路伺服器。  **WebClient** 依賴 **WebRequest** 類別提供對網際網路資源;因此， **WebClient** 類別可以使用任何已登錄的可外掛式通訊協定。  
  
 無法使用要求\/回應模型的應用程式中，或是需要在網路上接聽以及傳送要求的應用程式， **System.Net.Sockets** 命名空間提供 [TCPClient](frlrfsystemnetsocketstcpclientclasstopic)、 [TCPListener](frlrfsystemnetsocketstcplistenerclasstopic)和 [UDPClient](frlrfsystemnetsocketsudpclientclasstopic) 類別。  這些類別處理使用不同的傳輸通訊協定以產生連接的詳細資訊，並公開網路連接至應用程式做為資料流。  
  
 開發人員熟悉 Windows Sockets 連接或需要程式設計提供的控制項在通訊端層級的人尋找 **System.Net.Sockets** 類別符合其需求。  **System.Net.Sockets** 類別是從 Managed 程式碼中設定中斷點 **System.Net** 加入至類別內的機器碼。  在許多情況下， **System.Net.Sockets** 類別封送處理資料到其 Windows 32 位元的對應，以及處理所有必要的安全性檢查。  
  
## 請參閱  
 [可插式通訊協定程式設計](../../../docs/framework/network-programming/programming-pluggable-protocols.md)   
 [以 .NET Framework 進行網路程式設計](../../../docs/framework/network-programming/index.md)   
 [網路程式設計範例](../../../docs/framework/network-programming/network-programming-samples.md)   
 [.NET 的網路範例 MSDN Code Gallery](http://code.msdn.microsoft.com/Wiki/View.aspx?ProjectName=nclsamples)
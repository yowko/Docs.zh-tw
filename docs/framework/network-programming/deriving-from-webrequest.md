---
title: "衍生自 WebRequest | Microsoft Docs"
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
  - "WebRequest 類別，可插式通訊協定"
  - "通訊協定特定要求處理常式"
  - "傳送資料，可插式通訊協定"
  - "可插式通訊協定、類別準則"
  - "網際網路，可插式通訊協定"
  - "接收資料，可插式通訊協定"
  - "通訊協定，可插式"
ms.assetid: 9810c177-973e-43d7-823c-14960bd625ea
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 7
---
# 衍生自 WebRequest
<xref:System.Net.WebRequest> 類別是建立一個通訊協定的特定要求處理常式會提供基本的方法和屬性調整 .NET Framework 可外掛式通訊協定模型的抽象基底類別。  使用 **WebRequest** 類別的應用程式可以要求資料使用任何支援的通訊協定，而不需要指定所使用的通訊協定。  
  
 必須符合兩個準則以及要做為可外掛式通訊協定使用的通訊協定的特定類別:類別必須實作介面， <xref:System.Net.IWebRequestCreate> ，而且必須向 <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=fullName> 方法註冊。  類別必須覆寫 **WebRequest** 所有抽象方法和屬性來提供可插入的介面。  
  
 **WebRequest** 供處置執行個體使用，如果您想要讓另一個要求，請建立新的 **WebRequest**。  **WebRequest** 支援 <xref:System.Runtime.Serialization.ISerializable> 介面可讓開發人員序列化樣板 **WebRequest** 然後重新建置其他需求的範本。  
  
## IWebRequest 建立方法  
 <xref:System.Net.IWebRequestCreate.Create%2A> 方法以通訊協定專屬的初始化類別的新執行個體。  當新的 **WebRequest** 建立時， <xref:System.Net.WebRequest.Create%2A?displayProperty=fullName> 方法與所要求的 URI 為 URI 前置詞移至 **RegisterPrefix** 方法註冊。  適當的通訊協定專屬的子代的 **建立** 方法必須傳回這個從屬的已初始化之執行個體的執行通訊協定的一種標準要求\/回應交易不需要修改的任何通訊協定的特定欄位。  
  
## ConnectionGroupName 屬性  
 <xref:System.Net.WebRequest.ConnectionGroupName%2A> 屬性是用來命名連線的群組與資源的，讓多個要求可以在單一連接。  若要實作連接共用，您必須使用共用一個通訊協定的特定方法和指派連接。  例如，共用。 <xref:System.Net.HttpWebRequest> 類別所提供的 <xref:System.Net.ServicePointManager> 類別實作介面。  為每個連接群組提供與特定伺服器連接的 **ServicePointManager** 類別建立 <xref:System.Net.ServicePoint> 。  
  
## ContentLength 屬性  
 <xref:System.Net.WebRequest.ContentLength%2A> 屬性所指定的位元組數將傳送至伺服器，以上載資料時的資料。  
  
 通常不需要設定 <xref:System.Net.WebRequest.Method%2A> 屬性指示上載時，就會發生 **ContentLength** 屬性設定為大於零的值時。  
  
## ContentType 屬性  
 <xref:System.Net.WebRequest.ContentType%2A> 屬性提供任何特殊資訊的通訊協定需要您傳送至伺服器識別您傳送內容的型別。  這通常是上載之所有資料的 MIME 內容類型。  
  
## 驗證屬性  
 <xref:System.Net.WebRequest.Credentials%2A> 屬性包含必要的資訊進行伺服器的要求。  您必須實作驗證程序的詳細資料則通訊協定的。  <xref:System.Net.AuthenticationManager> 類別負責驗證要求並提供驗證語彙基元負責。  提供您所使用的通訊協定 \(Protocol\) 認證的類別必須實作介面 <xref:System.Net.ICredentials> 。  
  
## 標題屬性。  
 <xref:System.Net.WebRequest.Headers%2A> 屬性包含名稱\/值組的選擇性集合相關聯的中繼資料要求。  可以表示為名稱\/值組的通訊協定所需的所有中繼資料儲存在 **Headers** 屬性可以加入中。  通常必須在呼叫 <xref:System.Net.WebRequest.GetRequestStream%2A> 或 <xref:System.Net.WebRequest.GetResponse%2A> 方法之前設定這個資訊;一次要求後，中繼資料被視為唯讀。  
  
 不需要使用 **Headers** 屬性使用標頭中繼資料。  通訊協定專屬中繼資料可以公開 \(Expose\) 為屬性，例如， <xref:System.Net.HttpWebRequest.UserAgent%2A?displayProperty=fullName> 屬性公開 **User\-Agent** HTTP 標頭。  當您公開標題中繼資料做為屬性時，會使用 **Headers** 屬性，則不應該允許相同的屬性設定為。  
  
## 方法屬性  
 <xref:System.Net.WebRequest.Method%2A> 屬性包含這個動詞命令或動作需要要求伺服器上執行。  **Method** 屬性的預設值必須啟用一次標準要求\/回應動作而不需要任何通訊協定的特定屬性設定。  例如， [HttpWebResponse](frlrfSystemNetHttpWebResponseClassMethodTopic) 方法預設取得，從 Web 伺服器要求的資源並傳回回應。  
  
 通常不需要設定 **ContentLength** 屬性設定為大於零的值， **Method** 當屬性設定為表示動詞命令或動作時上載時發生。  
  
## PreAuthenticate 屬性  
 應用程式設定 <xref:System.Net.WebRequest.PreAuthenticate%2A> 屬性指示應該傳送驗證資訊和初始要求而不是等待驗證要求。  如果通訊協定支援驗證認證傳送的初始要求， **PreAuthenticate** 屬性才有意義。  
  
## Proxy 屬性。  
 <xref:System.Net.WebRequest.Proxy%2A> 屬性包含用於存取所要求的資源。 <xref:System.Net.IWebProxy> 介面。  只有在您的通訊協定支援 Proxy 要求逾時， **Proxy** 屬性才有意義。  此外，如果您的通訊協定，需要一個您必須設定預設 Proxy。  
  
 在某些環境下，像是在公司防火牆之後，可能需要通訊協定使用 Proxy。  在這種情況下，您必須實作介面 **IWebProxy** 針對通訊協定將工作的 Proxy 類別。  
  
## RequestUri 屬性  
 傳遞至方法的 **WebRequest.Create**<xref:System.Net.WebRequest.RequestUri%2A> 屬性包含 URI。  **WebRequest** ，一旦建立，它是唯讀的，無法變更。  如果您的通訊協定支援重新導向，回應可能來自不同的 URI 識別的資源。  如果您需要提供對回應的 URI，您必須提供包含該 URI 的其他屬性。  
  
## timeout 屬性  
 <xref:System.Net.WebRequest.Timeout%2A> 屬性以毫秒為單位的時間，，在要求之前的等候時間並且擲回例外狀況。  **Timeout** 只適用於以 <xref:System.Net.WebRequest.GetResponse%2A> 方法執行的同步要求;非同步要求必須使用 <xref:System.Net.WebRequest.Abort%2A> 方法取消暫止的要求。  
  
 只有當通訊協定的特定類別實作暫止處理序，設定 **Timeout** 屬性才有意義。  
  
## 中止方法  
 <xref:System.Net.WebRequest.Abort%2A> 方法取消暫止的非同步要求至伺服器。  在要求取消後，會呼叫 **GetResponse**， **BeginGetResponse**、 **EndGetResponse**、 **GetRequestStream**、 **BeginGetRequestStream**或 **EndGetRequestStream** 會擲回以 <xref:System.Net.WebException.Status%2A> 屬性的 <xref:System.Net.WebException> 設為 [RequestCanceled](frlrfSystemNetWebExceptionStatusClassTopic)。  
  
## BeginGetRequestStream 和 EndGetRequestStream 方法  
 <xref:System.Net.WebRequest.BeginGetRequestStream%2A> 方法會啟動用來上載資料至伺服器的資料流的非同步要求。  <xref:System.Net.WebRequest.EndGetRequestStream%2A> 方法來完成這個非同步要求並傳回要求的資料流。  使用標準 .NET Framework 非同步模式，這些方法會執行 **GetRequestStream** 方法。  
  
## BeginGetResponse 和 EndGetResponse 方法  
 <xref:System.Net.WebRequest.BeginGetResponse%2A> 方法會啟動非同步要求至伺服器。  <xref:System.Net.WebRequest.EndGetResponse%2A> 方法來完成這個非同步要求並傳回所要求的回應。  使用標準 .NET Framework 非同步模式，這些方法會執行 **GetResponse** 方法。  
  
## GetRequestStream 方法  
 <xref:System.Net.WebRequest.GetRequestStream%2A> 方法傳回用來寫入要求的伺服器寫入資料的資料流。  傳回的資料流應該不要尋找的唯寫資料流;做為寫入伺服器所撰寫的單向資料流。  資料流傳回錯誤 <xref:System.IO.Stream.CanRead%2A> 和 <xref:System.IO.Stream.CanSeek%2A> 屬性的 <xref:System.IO.Stream.CanWrite%2A> 並將屬性設定為 true。  
  
 **GetRequestStream** 方法會傳回資料流之前通常會開啟與伺服器的連接，然後，指出，傳送的標頭資訊的資料傳送至伺服器。  由於 **GetRequestStream** 啟動要求，將任何 **Header** 屬性或 **ContentLength** 屬性沒有在呼叫之後 **GetRequestStream**通常不允許。  
  
## GetResponse 方法  
 <xref:System.Net.WebRequest.GetResponse%2A> 方法傳回表示來自伺服器的回應 <xref:System.Net.WebResponse> 類別的一個通訊協定專屬的子代。  除非 **GetRequestStream** 方法已經開始要求， **GetResponse** 方法建立 **RequestUri**所識別的資源的連接，表示傳送要求的型別標頭資訊進行，然後接收資源的回應。  
  
 一旦 **GetResponse** 呼叫方法時，應該考慮所有屬性都是唯讀的。  **WebRequest** 供處置執行個體使用，如果您想要讓另一個要求，您應該建立新的 **WebRequest**。  
  
 **GetResponse** 方法建立適當的 **WebResponse** 子代管理包含傳入的回應。  
  
## 請參閱  
 <xref:System.Net.WebRequest>   
 <xref:System.Net.HttpWebRequest>   
 <xref:System.Net.FileWebRequest>   
 [可插式通訊協定程式設計](../../../docs/framework/network-programming/programming-pluggable-protocols.md)   
 [衍生自 WebResponse](../../../docs/framework/network-programming/deriving-from-webresponse.md)
---
title: "使用用戶端通訊端 | Microsoft Docs"
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
  - "應用程式通訊協定，通訊端"
  - "傳送資料，通訊端"
  - "資料要求，通訊端"
  - "從網際網路要求資料，通訊端"
  - "接收資料，通訊端"
  - "通訊端類別，用戶端通訊端"
  - "通訊協定，通訊端"
  - "網際網路，通訊端"
  - "通訊端，用戶端通訊端"
  - "用戶端通訊端"
ms.assetid: 81de9f59-8177-4d98-b25d-43fc32a98383
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# 使用用戶端通訊端
在您可以 <xref:System.Net.Sockets.Socket>之前啟始對話，您必須在您的應用程式和遠端裝置之間的資料管道。  雖然其他位址家族和通訊協定存在，這個範例示範如何使用一項遠端服務的 TCP\/IP 連接。  
  
 一個使用 TCP\/IP 網路位址與服務通訊埠編號唯一識別服務。  網路位址識別在網路上的特定裝置;通訊埠編號識別該裝置的特定服務連接。  Web 服務位址和連接埠的組合稱為端點， .NET Framework 以 <xref:System.Net.EndPoint> 類別。  **EndPoint** 子代針對每個支援的通訊協定家族中定義，對於 IP 位址家族，類別是 <xref:System.Net.IPEndPoint>。  
  
 <xref:System.Net.Dns> 類別為使用 TCP\/IP 網際網路服務的應用程式定義域提供服務。  <xref:System.Net.Dns.Resolve%2A> 方法查詢 DNS 伺服器對應以方便使用網域名稱 \(例如「host.contoso.com」\) 轉換為數字網際網路位址 \(例如 192.168.1.1\)。  **Resolve** 傳回包含位址和別名清單所要求名稱的 [IPHostEnty](frlrfsystemnetiphostentryclasstopic) 。  在許多情況下，您可以在 <xref:System.Net.IPHostEntry.AddressList%2A> 陣列可以使用傳回的第一個位址。  下列程式碼會取得包含伺服器的 host.contoso.com <xref:System.Net.IPAddress> IP 位址。  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 Internet Assigned Numbers Authority \(Iana\) 定義通用服務的通訊埠編號 \(如需詳細資訊，請參閱 www.iana.org\/assignments\/port\-numbers\) \(英文\)。  其他服務可以註冊介於 1,024 到 65,535 的通訊埠編號。  下列程式碼包含 host.contoso.com 的 IP 位址和通訊埠編號來建立連接的遠端端點。  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 在判斷遠端裝置的位址和選取連接埠之後此連接使用，應用程式可以嘗試與遠端裝置的連接。  下列範例會使用現有的 **IPEndPoint** 連接至遠端裝置並攔截任何擲回的例外狀況。  
  
```vb  
Try  
    s.Connect(ipe)  
Catch ae As ArgumentNullException  
    Console.WriteLine("ArgumentNullException : {0}", _  
        ae.ToString())  
Catch se As SocketException  
    Console.WriteLine("SocketException : {0}", se.ToString())  
Catch e As Exception  
    Console.WriteLine("Unexpected exception : {0}", e.ToString())  
End Try  
  
```  
  
```csharp  
try {  
    s.Connect(ipe);  
} catch(ArgumentNullException ae) {  
    Console.WriteLine("ArgumentNullException : {0}", ae.ToString());  
} catch(SocketException se) {  
    Console.WriteLine("SocketException : {0}", se.ToString());  
} catch(Exception e) {  
    Console.WriteLine("Unexpected exception : {0}", e.ToString());  
}  
```  
  
## 請參閱  
 [使用同步用戶端通訊端](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)   
 [使用非同步用戶端通訊端](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)   
 [如何：建立通訊端](../../../docs/framework/network-programming/how-to-create-a-socket.md)   
 [通訊端](../../../docs/framework/network-programming/sockets.md)
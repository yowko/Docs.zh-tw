---
title: "透過通訊端接聽 | Microsoft Docs"
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
  - "通訊端，透過通訊端接聽"
  - "資料要求，通訊端"
  - "從網際網路要求資料，通訊端"
  - "接收資料，通訊端"
  - "通訊協定，通訊端"
  - "透過通訊端接聽"
  - "網際網路，通訊端"
ms.assetid: 40e426cc-13db-4371-95eb-f7388bd23ebf
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# 透過通訊端接聽
接聽程式或伺服器通訊端開啟 Web 上的連接埠然後等候用戶端連接到該連接埠。  雖然其他位址家族和通訊協定存在，範例會示範如何建立 TCP\/IP 網路上的遠端服務。  
  
 TCP\/IP 服務的唯一的位址會結合主機的 IP 位址定義與服務的通訊埠編號建立服務的端點。  <xref:System.Net.Dns> 類別可提供與網路位址的傳回資訊由區域網路裝置支援的方法。  當區域網路裝置具有一個以上的位址時，則為，如果由本機系統上支援一個以上的網路裝置， **Dns** 類別傳回所有關於網路位址的相關資訊，因此，應用程式必須先選取適當的服務的位址。  Internet Assigned Numbers Authority \(Iana\) 定義通用服務的通訊埠編號 \(如需詳細資訊，請參閱 www.iana.org\/assignments\/port\-numbers\) \(英文\)。  其他服務可以註冊介於 1,024 到 65,535 的通訊埠編號。  
  
 下列範例會以合併主機電腦的 **Dns** 傳回的第一個 IP 位址建立伺服器的 <xref:System.Net.IPEndPoint> 與從註冊的通訊埠編號選取的通訊埠編號範圍。  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
Dim localEndPoint As New IPEndPoint(ipAddress, 11000)  
  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
IPEndPoint localEndPoint = new IPEndPoint(ipAddress, 11000);  
```  
  
 在區域端點來決定的之後，在端點必須與使用 <xref:System.Net.Sockets.Socket.Listen%2A> 方法， <xref:System.Net.Sockets.Socket> 與該端點使用 <xref:System.Net.Sockets.Socket.Bind%2A> 方法和設定接聽。  如果特定位址和連接埠組合已經在使用中，**繫結** 擲回例外狀況。  下列範例示範相關聯 **Socket** 與 **IPEndPoint**。  
  
```vb  
listener.Bind(localEndPoint)  
listener.Listen(100)  
```  
  
```csharp  
listener.Bind(localEndPoint);  
listener.Listen(100);  
```  
  
 **Listen** 方法會使用指定的單一參數與 **Socket** 多少暫止連接允許，則伺服器忙碌錯誤傳回至連接的用戶端。  在這種情況下，在這種情況下，一個伺服器忙碌的回應傳回給客戶編號 101 之前， 100 用戶端在連接佇列中的位置。  
  
## 請參閱  
 [使用同步伺服器通訊端](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)   
 [使用非同步伺服器通訊端](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)   
 [使用用戶端通訊端](../../../docs/framework/network-programming/using-client-sockets.md)   
 [如何：建立通訊端](../../../docs/framework/network-programming/how-to-create-a-socket.md)   
 [通訊端](../../../docs/framework/network-programming/sockets.md)
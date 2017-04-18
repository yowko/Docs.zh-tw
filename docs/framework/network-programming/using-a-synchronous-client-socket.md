---
title: "使用同步用戶端通訊端 | Microsoft Docs"
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
  - "同步用戶端通訊端"
  - "通訊端類別，同步用戶端通訊端"
  - "接收資料，通訊端"
  - "通訊端，同步用戶端通訊端"
  - "通訊協定，通訊端"
  - "網際網路，通訊端"
  - "用戶端通訊端"
ms.assetid: 945d00c6-7202-466c-9df9-140b84156d43
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# 使用同步用戶端通訊端
要在網路作業完成時，一個同步用戶端通訊端暫停應用程式。  同步通訊端不適用於大量使用其作業的網路應用程式，但是，可啟用對 Web 服務的簡單存取其他應用程式的。  
  
 若要傳送資料，將位元組陣列為其中一個 <xref:System.Net.Sockets.Socket> 傳送資料<xref:System.Net.Sockets.Socket.Send%2A><xref:System.Net.Sockets.Socket.SendTo%2A>方法 \(和\)。  使用 **傳送** 方法，所以下列範例會將字串編碼成位元組陣列緩衝區使用 <xref:System.Text.Encoding.ASCII%2A?displayProperty=fullName> 屬性然後傳送緩衝區寫入網路裝置。  **傳送** 方法傳回位元組數目傳送至網路裝置。  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 **傳送** 方法從緩衝區位元組並移除佇列它們與要傳送之網路介面的網路裝置。  網路介面可能不會立即傳送資料，不過，它最後會傳送，，只要連接正常關閉。 <xref:System.Net.Sockets.Socket.Shutdown%2A> 方法。  
  
 若要從接收網路裝置的資料，請傳遞的緩衝區為其中一個 **Socket** 的接收資料<xref:System.Net.Sockets.Socket.Receive%2A><xref:System.Net.Sockets.Socket.ReceiveFrom%2A>方法 \(和\)。  同步處理的通訊端將逾時應用程式，直到位元組從網路接收，或者關閉通訊端。  下列範例會從 Web 下載資料並將其顯示在主控台。  這個範例假設，來自網路的資料是以 ASCII 編碼的文字。  **Receive** 方法會從網路接收的位元組數目。  
  
```vb  
Dim bytes(1024) As Byte  
Dim bytesRec = s.Receive(bytes)  
Console.WriteLine("Echoed text = {0}", _  
    System.Text.Encoding.ASCII.GetString(bytes, 0, bytesRec))  
  
```  
  
```csharp  
byte[] bytes = new byte[1024];  
int bytesRec = s.Receive(bytes);  
Console.WriteLine("Echoed text = {0}",  
    System.Text.Encoding.ASCII.GetString(bytes, 0, bytesRec));  
```  
  
 發生通訊端不再需要物件時，您需要呼叫 <xref:System.Net.Sockets.Socket.Shutdown%2A> 方法再呼叫方法 **關閉** 釋放它。  下列範例會釋放 **Socket**。  <xref:System.Net.Sockets.SocketShutdown> 列舉定義表示的常數是否應關閉通訊端的傳送，會接收，或這兩個使用權限。  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## 請參閱  
 [使用非同步用戶端通訊端](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)   
 [透過通訊端接聽](../../../docs/framework/network-programming/listening-with-sockets.md)   
 [同步用戶端通訊端範例](../../../docs/framework/network-programming/synchronous-client-socket-example.md)
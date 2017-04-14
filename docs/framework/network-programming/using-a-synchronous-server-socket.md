---
title: "使用同步伺服器通訊端 | Microsoft Docs"
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
  - "同步伺服器通訊端"
  - "傳送資料，通訊端"
  - "資料要求，通訊端"
  - "從網際網路要求資料，通訊端"
  - "伺服器通訊端"
  - "接收資料，通訊端"
  - "通訊端類別，同步伺服器通訊端"
  - "通訊協定，通訊端"
  - "通訊端，同步伺服器通訊端"
  - "網際網路，通訊端"
ms.assetid: d1ce882e-653e-41f5-9289-844ec855b804
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# 使用同步伺服器通訊端
同步處理伺服器通訊端暫停應用程式的執行，直到連接要求在通訊端接收。  同步處理伺服器通訊端不適用於大量使用在其作業的網路應用程式，不過，它們可以適用於簡單的 Web 應用程式。  
  
 使用 <xref:System.Net.Sockets.Socket.Bind%2A> 和 <xref:System.Net.Sockets.Socket.Listen%2A> 方法之後，在 <xref:System.Net.Sockets.Socket> 在端點設定接聽，使用方法， <xref:System.Net.Sockets.Socket.Accept%2A> 準備就緒以接受輸入的連接要求。  應用程式會被暫止，直到接收到連接要求，則 **接受** 時呼叫方法。  
  
 當接收到連接要求時， **接受** 傳回與連接用戶端的 **Socket** 新執行個體。  下列範例從用戶端讀取資料，然後將其顯示在主控台上，並且回應資料傳回給用戶端。  **Socket** 並未指定任何訊息通訊協定，因此字串「\<EOF\>」標記訊息資料的結尾。  這個範例假設，名為 `listener`的 **Socket** 已初始化並繫結到端點。  
  
```vb  
Console.WriteLine("Waiting for a connection...")  
Dim handler As Socket = listener.Accept()  
Dim data As String = Nothing  
  
While True  
    bytes = New Byte(1024) {}  
    Dim bytesRec As Integer = handler.Receive(bytes)  
    data += Encoding.ASCII.GetString(bytes, 0, bytesRec)  
    If data.IndexOf("<EOF>") > - 1 Then  
        Exit While  
    End If  
End While  
  
Console.WriteLine("Text received : {0}", data)  
  
Dim msg As Byte() = Encoding.ASCII.GetBytes(data)  
handler.Send(msg)  
handler.Shutdown(SocketShutdown.Both)  
handler.Close()  
  
```  
  
```csharp  
Console.WriteLine("Waiting for a connection...");  
Socket handler = listener.Accept();  
String data = null;  
  
while (true) {  
    bytes = new byte[1024];  
    int bytesRec = handler.Receive(bytes);  
    data += Encoding.ASCII.GetString(bytes,0,bytesRec);  
    if (data.IndexOf("<EOF>") > -1) {  
        break;  
    }  
}  
  
Console.WriteLine( "Text received : {0}", data);  
  
byte[] msg = Encoding.ASCII.GetBytes(data);  
handler.Send(msg);  
handler.Shutdown(SocketShutdown.Both);  
handler.Close();  
```  
  
## 請參閱  
 [使用非同步伺服器通訊端](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)   
 [同步伺服器通訊端範例](../../../docs/framework/network-programming/synchronous-server-socket-example.md)   
 [透過通訊端接聽](../../../docs/framework/network-programming/listening-with-sockets.md)
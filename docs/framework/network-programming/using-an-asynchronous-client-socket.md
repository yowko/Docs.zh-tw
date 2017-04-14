---
title: "使用非同步用戶端通訊端 | Microsoft Docs"
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
  - "非同步用戶端通訊端"
  - "通訊端類別，非同步用戶端通訊端"
  - "從網際網路要求資料，通訊端"
  - "通訊端，非同步用戶端通訊端"
  - "接收資料，通訊端"
  - "通訊協定，通訊端"
  - "網際網路，通訊端"
  - "用戶端通訊端"
ms.assetid: fd85bc88-e06c-467d-a30d-9fd7cffcfca1
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# 使用非同步用戶端通訊端
非同步用戶端通訊端未暫停應用程式，在等待網路作業完成時。  相反地，，當應用程式在原始執行緒繼續執行時，它會使用標準 .NET Framework 非同步程式設計模型中處理執行緒的網路連接。  非同步通訊端方大量使用網路或無法等待網路作業在繼續進行之前完成的應用程式是適當的。  
  
 <xref:System.Net.Sockets.Socket> 類別遵循非同步方法的 .NET Framework 命名模式，例如，同步處理 <xref:System.Net.Sockets.Socket.Receive%2A> 方法對應於非同步 <xref:System.Net.Sockets.Socket.BeginReceive%2A> 和 <xref:System.Net.Sockets.Socket.EndReceive%2A> 方法。  
  
 非同步作業要求回呼方法傳回作業的結果。  如果您的應用程式不需要知道結果，則不需要回呼方法。  本節中的範例程式碼將示範如何使用方法啟動連接至網路裝置和回呼方法完成連接、方法開始傳送資料和回呼方法完成傳送和方法開始接收資料和回呼方法結束接收資料。  
  
 以非同步方式從系統的通訊端使用多執行緒集區處理網路連接。  一個執行緒啟始傳送或接收負責資料;其他執行緒完成與網路裝置的連接並傳送或接收資料。  在下列範例中， <xref:System.Threading.ManualResetEvent?displayProperty=fullName> 類別的執行個體來暫停主執行緒和信號執行時無法繼續。  
  
 在下列範例中，連接非同步通訊端的網路裝置， `Connect`方法初始化 **Socket** 接著呼叫方法，傳遞做為 [BeginConnect](frlrfsystemnetsocketssocketclassconnecttopic) 表示網路裝置、連接回呼方法和狀態物件的遠端端點 \(用戶端 **Socket**\)，用來傳遞狀態資訊在非同步呼叫之間。  這個範例會執行 `Connect` 方法連結指定的 **Socket** 至指定的端點。  它會假設名為 `connectDone`的全域 **ManualResetEvent** 。  
  
```vb  
Public Shared Sub Connect(remoteEP As EndPoint, client As Socket)  
    client.BeginConnect(remoteEP, _  
       AddressOf ConnectCallback, client)  
  
    connectDone.WaitOne()  
End Sub 'Connect  
```  
  
```csharp  
public static void Connect(EndPoint remoteEP, Socket client) {  
    client.BeginConnect(remoteEP,   
        new AsyncCallback(ConnectCallback), client );  
  
   connectDone.WaitOne();  
}  
```  
  
 連接回呼方法 `ConnectCallback` 實作 <xref:System.AsyncCallback> 委派。  會連接至遠端裝置，當遠端裝置可用時然後通知應用程式執行緒連接是透過設定 **ManualResetEvent**`connectDone`完成。  下列程式碼會執行 `ConnectCallback` 方法。  
  
```vb  
Private Shared Sub ConnectCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the socket from the state object.  
        Dim client As Socket = CType(ar.AsyncState, Socket)  
  
        ' Complete the connection.  
        client.EndConnect(ar)  
  
        Console.WriteLine("Socket connected to {0}", _  
            client.RemoteEndPoint.ToString())  
  
        ' Signal that the connection has been made.  
        connectDone.Set()  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'ConnectCallback  
  
```  
  
```csharp  
private static void ConnectCallback(IAsyncResult ar) {  
    try {  
        // Retrieve the socket from the state object.  
        Socket client = (Socket) ar.AsyncState;  
  
        // Complete the connection.  
        client.EndConnect(ar);  
  
        Console.WriteLine("Socket connected to {0}",  
            client.RemoteEndPoint.ToString());  
  
        // Signal that the connection has been made.  
        connectDone.Set();  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 範例方法 `Send` 輸入為 ASCII 格式的指定字串資料並將其傳送至指定的非同步通訊端表示的網路裝置。  下列範例會執行 `Send` 方法。  
  
```vb  
Private Shared Sub Send(client As Socket, data As [String])  
    ' Convert the string data to byte data using ASCII encoding.  
    Dim byteData As Byte() = Encoding.ASCII.GetBytes(data)  
  
    ' Begin sending the data to the remote device.  
    client.BeginSend(byteData, 0, byteData.Length, SocketFlags.None, _  
        AddressOf SendCallback, client)  
End Sub 'Send  
  
```  
  
```csharp  
private static void Send(Socket client, String data) {  
    // Convert the string data to byte data using ASCII encoding.  
    byte[] byteData = Encoding.ASCII.GetBytes(data);  
  
    // Begin sending the data to the remote device.  
    client.BeginSend(byteData, 0, byteData.Length, SocketFlags.None,  
        new AsyncCallback(SendCallback), client);  
}  
```  
  
 傳送回呼方法 `SendCallback` 實作 <xref:System.AsyncCallback> 委派。  當 Web 裝置準備接收訊息時，傳送資料。  下列範例顯示 `SendCallback` 方法的實作。  它會假設名為 `sendDone`的全域 **ManualResetEvent** 。  
  
```vb  
Private Shared Sub SendCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the socket from the state object.  
        Dim client As Socket = CType(ar.AsyncState, Socket)  
  
        ' Complete sending the data to the remote device.  
        Dim bytesSent As Integer = client.EndSend(ar)  
        Console.WriteLine("Sent {0} bytes to server.", bytesSent)  
  
        ' Signal that all bytes have been sent.  
        sendDone.Set()  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'SendCallback  
  
```  
  
```csharp  
private static void SendCallback(IAsyncResult ar) {  
    try {  
        // Retrieve the socket from the state object.  
        Socket client = (Socket) ar.AsyncState;  
  
        // Complete sending the data to the remote device.  
        int bytesSent = client.EndSend(ar);  
        Console.WriteLine("Sent {0} bytes to server.", bytesSent);  
  
        // Signal that all bytes have been sent.  
        sendDone.Set();  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 從用戶端讀取通訊端的資料要求傳遞值在非同步呼叫之間的狀態物件。  下列類別會接收之資料的範例狀態物件從用戶端通訊端。  它包含用戶端上的欄位，接收之資料的緩衝區和 <xref:System.Text.StringBuilder> 物件所傳入的資料字串。  將這些欄位在狀態物件允許其值跨多個呼叫將會從用戶端通訊端的資料。  
  
```vb  
Public Class StateObject  
    ' Client socket.  
    Public workSocket As Socket = Nothing   
    ' Size of receive buffer.  
    Public BufferSize As Integer = 256  
    ' Receive buffer.  
    Public buffer(256) As Byte   
    ' Received data string.  
    Public sb As New StringBuilder()  
End Class 'StateObject  
  
```  
  
```csharp  
public class StateObject {  
    // Client socket.  
    public Socket workSocket = null;  
    // Size of receive buffer.  
    public const int BufferSize = 256;  
    // Receive buffer.  
    public byte[] buffer = new byte[BufferSize];  
    // Received data string.  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 範例 `Receive` 方法設定狀態物件會呼叫方法 **BeginReceive** 讀取用戶端通訊端的資料同步。  下列範例會執行 `Receive` 方法。  
  
```vb  
Private Shared Sub Receive(client As Socket)  
    Try  
        ' Create the state object.  
        Dim state As New StateObject()  
        state.workSocket = client  
  
        ' Begin receiving the data from the remote device.  
        client.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf ReceiveCallback, state)  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'Receive  
  
```  
  
```csharp  
private static void Receive(Socket client) {  
    try {  
        // Create the state object.  
        StateObject state = new StateObject();  
        state.workSocket = client;  
  
        // Begin receiving the data from the remote device.  
        client.BeginReceive( state.buffer, 0, StateObject.BufferSize, 0,  
            new AsyncCallback(ReceiveCallback), state);  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 接收回呼方法 `ReceiveCallback` 實作 **AsyncCallback** 委派。  它會從網路裝置的資料並建置訊息字串。  從其中一個或多個位元組從網路資料至資料緩衝區 **BeginReceive** 然後再次呼叫方法，直到用戶端傳送的資料都完成為止。  一旦所有資料從用戶端讀取， `ReceiveCallback` 通知應用程式執行緒資料 \(藉由設定 **ManualResetEvent** `sendDone`完成。  
  
 下列範例程式碼會執行 `ReceiveCallback`方法。  它會假設為名為的 `receiveDone`接收的資料和全域 **ManualResetEvent** 負載名為的全域 `response` 字串。  伺服器必須立即關閉用戶端通訊端結束網路工作階段。  
  
```vb  
Private Shared Sub ReceiveCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the state object and the client socket   
        ' from the asynchronous state object.  
        Dim state As StateObject = CType(ar.AsyncState, StateObject)  
        Dim client As Socket = state.workSocket  
  
        ' Read data from the remote device.  
        Dim bytesRead As Integer = client.EndReceive(ar)  
  
        If bytesRead > 0 Then  
            ' There might be more data, so store the data received so far.  
            state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, _  
                bytesRead))  
  
            '  Get the rest of the data.  
            client.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
                AddressOf ReceiveCallback, state)  
        Else  
            ' All the data has arrived; put it in response.  
            If state.sb.Length > 1 Then  
                response = state.sb.ToString()  
            End If  
            ' Signal that all bytes have been received.  
            receiveDone.Set()  
        End If  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'ReceiveCallback  
  
```  
  
```csharp  
private static void ReceiveCallback( IAsyncResult ar ) {  
    try {  
        // Retrieve the state object and the client socket   
        // from the asynchronous state object.  
        StateObject state = (StateObject) ar.AsyncState;  
        Socket client = state.workSocket;  
        // Read data from the remote device.  
        int bytesRead = client.EndReceive(ar);  
        if (bytesRead > 0) {  
            // There might be more data, so store the data received so far.  
            state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,bytesRead));  
                //  Get the rest of the data.  
            client.BeginReceive(state.buffer,0,StateObject.BufferSize,0,  
                new AsyncCallback(ReceiveCallback), state);  
        } else {  
            // All the data has arrived; put it in response.  
            if (state.sb.Length > 1) {  
                response = state.sb.ToString();  
            }  
            // Signal that all bytes have been received.  
            receiveDone.Set();  
        }  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
## 請參閱  
 [使用同步用戶端通訊端](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)   
 [透過通訊端接聽](../../../docs/framework/network-programming/listening-with-sockets.md)   
 [非同步用戶端通訊端範例](../../../docs/framework/network-programming/asynchronous-client-socket-example.md)
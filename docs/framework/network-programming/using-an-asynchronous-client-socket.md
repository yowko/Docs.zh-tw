---
title: "使用非同步用戶端通訊端"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- asynchronous client sockets
- Socket class, asynchronous client sockets
- requesting data from Internet, sockets
- sockets, asynchronous client sockets
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- client sockets
ms.assetid: fd85bc88-e06c-467d-a30d-9fd7cffcfca1
caps.latest.revision: 14
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3f8bffcd94f3fb9c516e2201bd932480ab51c1a5
ms.contentlocale: zh-tw
ms.lasthandoff: 08/21/2017

---
# <a name="using-an-asynchronous-client-socket"></a>使用非同步用戶端通訊端
非同步用戶端通訊端等待網路作業完成時，不會暫停應用程式。 相反地，它會使用標準 .NET Framework 非同步程式設計模型，在一個執行緒上處理網路連線，同時應用程式繼續在原始執行緒上執行。 非同步通訊端適用於大量使用網路的應用程式，或是無法等候網路作業完成再繼續進行的應用程式。  
  
 <xref:System.Net.Sockets.Socket> 類別遵循非同步方法的 .NET Framework 命名模式；例如，同步 <xref:System.Net.Sockets.Socket.Receive%2A> 方法對應於非同步 <xref:System.Net.Sockets.Socket.BeginReceive%2A> 和 <xref:System.Net.Sockets.Socket.EndReceive%2A> 方法。  
  
 非同步作業需要回呼方法以傳回作業的結果。 如果您的應用程式不需要知道結果，則不需要回呼方法。 本節的範例程式碼示範如何使用方法來開始連線到網路裝置以及使用回呼方法完成連線、使用方法開始傳送資料以及使用回呼方法完成傳送，還有使用方法開始接收資料以及使用回呼方法結束接收資料。  
  
 非同步通訊端使用系統執行緒集區中的多個執行緒來處理網路連線。 一個執行緒負責初始化資料的傳送或接收；其他執行緒則完成與網路裝置的連線並且傳送或接收資料。 在下列範例中，<xref:System.Threading.ManualResetEvent?displayProperty=fullName> 類別的執行個體會暫停執行主執行緒，並在可以繼續執行時發出訊號。  
  
 在下列範例中，為了將非同步通訊端連線到網路裝置，`Connect` 方法會初始化**通訊端**，然後呼叫 <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=fullName> 方法、傳遞代表網路裝置的遠端端點、連線回呼方法和狀態物件 (用戶端**通訊端**)，這用來在非同步呼叫之間傳遞狀態資訊。 此範例會實作 `Connect` 方法，將指定的**通訊端**連線到指定的端點。 它會假設一個名為 `connectDone` 的全域 **ManualResetEvent**。  
  
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
  
 連線回呼方法 `ConnectCallback` 會實作 <xref:System.AsyncCallback> 委派。 它在遠端裝置可用時連線到遠端裝置，然後設定**ManualResetEvent** `connectDone`，通知應用程式執行緒連線已完成。 下例程式碼會實作 `ConnectCallback` 方法。  
  
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
  
 範例方法 `Send` 將指定的字串資料以 ASCII 格式編碼，並將它以非同步方式傳送到指定通訊端所代表的網路裝置。 下列範例會實作 `Send` 方法。  
  
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
  
 傳送回呼方法 `SendCallback` 會實作 <xref:System.AsyncCallback> 委派。 網路裝置準備好接收時，它會傳送資料。 下列範例會示範 `SendCallback` 方法的實作。 它會假設一個名為 `sendDone` 的全域 **ManualResetEvent**。  
  
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
  
 從用戶端通訊端讀取資料時，需要在非同步呼叫之間傳遞值的狀態物件。 下列類別是從用戶端通訊端接收資料的範例狀態物件。 它包含用戶端通訊端的欄位、已接收資料的緩衝區，以及儲存進入之資料字串的 <xref:System.Text.StringBuilder>。 將這些欄位放置在狀態物件，可允許在多個呼叫間保留其值，以從用戶端通訊端讀取資料。  
  
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
  
 `Receive` 方法範例會設定狀態物件，然後呼叫 **BeginReceive** 方法，以非同步方式從用戶端通訊端讀取資料。 下列範例會實作 `Receive` 方法。  
  
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
  
 接收回呼方法 `ReceiveCallback` 會實作 **AsyncCallback** 委派。 它會從網路裝置接收資料，並建立訊息字串。 它會將來自網路的一或多個位元組資料讀取到資料緩衝區，然後重新呼叫 **BeginReceive** 方法，直到用戶端所傳送的資料完整為止。 從用戶端讀取所有資料之後，`ReceiveCallback` 會設定 **ManualResetEvent** `sendDone` 通知應用程式執行緒資料已完整。  
  
 下列範例程式碼會實作 `ReceiveCallback` 方法。 它會假設名為 `response` 的全域字串負責保存收到的字串，以及一個名為 `receiveDone` 的全域 **ManualResetEvent**。 伺服器必須先依正常程序關閉用戶端通訊端，結束網路工作階段。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [使用同步用戶端通訊端](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)   
 [透過通訊端接聽](../../../docs/framework/network-programming/listening-with-sockets.md)   
 [非同步用戶端通訊端範例](../../../docs/framework/network-programming/asynchronous-client-socket-example.md)


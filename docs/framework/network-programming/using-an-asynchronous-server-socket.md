---
title: 使用非同步伺服器通訊端
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- Socket class, asynchronous server sockets
- data requests, sockets
- sockets, asynchronous server sockets
- requesting data from Internet, sockets
- server sockets
- receiving data, sockets
- asynchronous server sockets
- protocols, sockets
- Internet, sockets
ms.assetid: 813489a9-3efd-41b6-a33f-371d55397676
ms.openlocfilehash: 11ed53a4e51ba6993fd4e240116b0e1de910a01e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047039"
---
# <a name="using-an-asynchronous-server-socket"></a>使用非同步伺服器通訊端
非同步伺服器通訊端會使用 .NET Framework 非同步程式設計模型來處理網路服務要求。 <xref:System.Net.Sockets.Socket> 類別會遵循標準 .NET Framework 非同步命名模式；例如，同步 <xref:System.Net.Sockets.Socket.Accept%2A> 方法對應於非同步 <xref:System.Net.Sockets.Socket.BeginAccept%2A> 和 <xref:System.Net.Sockets.Socket.EndAccept%2A> 方法。  
  
 非同步伺服器通訊端需要一個用來開始接受網路連線要求的方法、一個用來處理連線要求並開始接收網路資料的回呼方法，以及一個用來結束接收資料的回呼方法。 本節會進一步討論所有這些方法。  
  
 在下列範例中，若要開始接受網路的連線要求，`StartListening` 方法會初始化**通訊端**，然後使用 **BeginAccept** 方法來開始接受新連線。 在通訊端上收到新的連線要求時，就會呼叫接受回呼方法。 它會負責取得將處理連線的**通訊端**執行個體，並將該**通訊端**移交給將處理要求的執行緒。 接受回呼方法會實作 <xref:System.AsyncCallback> 委派；它會傳回 void，並採用 <xref:System.IAsyncResult> 類型的單一參數。 下列範例是接受回呼方法的殼層。  
  
```vb  
Sub AcceptCallback(ar As IAsyncResult)  
    ' Add the callback code here.  
End Sub 'AcceptCallback  
```  
  
```csharp  
void AcceptCallback(IAsyncResult ar)
{  
    // Add the callback code here.  
}  
```  
  
 **BeginAccept** 方法採用兩個參數：指向接受回呼方法的 **AsyncCallback** 委派和用來將狀態資訊傳遞至回呼方法的物件。 在下列範例中，接聽**通訊端**會透過 *stat* 參數傳遞至回呼方法。 這個範例會建立 **AsyncCallback** 委派並開始接受來自網路的連線。  
  
```vb  
listener.BeginAccept( _  
    New AsyncCallback(SocketListener.AcceptCallback),_  
    listener)  
```  
  
```csharp  
listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
```  
  
 非同步通訊端使用系統執行緒集區中的執行緒來處理連入連線。 其中一個執行緒負責接受連線、另一個執行緒用來處理每個連入連線，還有一個執行緒負責接收來自連線的資料。 這些可能是相同的執行緒，視執行緒集區所指派的執行緒而定。 在下列範例中，<xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> 類別會暫停執行主執行緒，並在可以繼續執行時發出訊號。  
  
 下列範例示範非同步方法，用來在本機電腦上建立非同步的 TCP/IP 通訊端，並開始接受連接。 它假設有一個名為 `allDone` 的全域 **ManualResetEvent**且該方法是 `SocketListener` 類別的成員，以及已定義名為 `AcceptCallback` 的回呼方法。  
  
```vb  
Public Sub StartListening()  
    Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
    Dim localEP = New IPEndPoint(ipHostInfo.AddressList(0), 11000)  
  
    Console.WriteLine($"Local address and port : {localEP.ToString()}")  
  
    Dim listener As New Socket(localEP.Address.AddressFamily, _  
       SocketType.Stream, ProtocolType.Tcp)  
  
    Try  
        listener.Bind(localEP)  
        listener.Listen(10)  
  
        While True  
            allDone.Reset()  
  
            Console.WriteLine("Waiting for a connection...")  
            listener.BeginAccept(New _  
                AsyncCallback(SocketListener.AcceptCallback), _  
                listener)  
  
            allDone.WaitOne()  
        End While  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
    Console.WriteLine("Closing the listener...")  
End Sub 'StartListening  
```  
  
```csharp  
public void StartListening()
{  
    IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
    IPEndPoint localEP = new IPEndPoint(ipHostInfo.AddressList[0], 11000);  
  
    Console.WriteLine($"Local address and port : {localEP.ToString()}");  
  
    Socket listener = new Socket(localEP.Address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);  
  
    try 
    {  
        listener.Bind(localEP);  
        listener.Listen(10);  
  
        while (true)
        {  
            allDone.Reset();  
  
            Console.WriteLine("Waiting for a connection...");  
            listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
  
            allDone.WaitOne();  
        }  
    }
    catch (Exception e)
    {  
        Console.WriteLine(e.ToString());  
    }  
  
    Console.WriteLine("Closing the listener...");  
}  
```  
  
 接受回呼方法 (在上述範例中為 `AcceptCallback`) 負責指示主要應用程式執行緒繼續處理、建立與用戶端的連線，以及開始從用戶端非同步讀取資料。 下列範例是 `AcceptCallback` 方法實作的第一部分。 該方法的這個區段會指示主要應用程式執行緒繼續處理，並建立與用戶端的連線。 它會假設一個名為 `allDone` 的全域 **ManualResetEvent**。  
  
```vb  
Public Sub AcceptCallback(ar As IAsyncResult)  
    allDone.Set()  
  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Additional code to read data goes here.  
End Sub 'AcceptCallback  
```  
  
```csharp  
public void AcceptCallback(IAsyncResult ar) 
{  
    allDone.Set();  
  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Additional code to read data goes here.    
}  
```  
  
 從用戶端通訊端讀取資料時，需要在非同步呼叫之間傳遞值的狀態物件。 下列範例會實作從遠端用戶端接收字串的狀態物件。 其包含用於用戶端通訊端的欄位、用來接收資料的資料緩衝區，以及用來建立用戶端所傳送資料字串的 <xref:System.Text.StringBuilder>。 將這些欄位放置在狀態物件，可允許在多個呼叫間保留其值，以從用戶端通訊端讀取資料。  
  
```vb  
Public Class StateObject  
    Public workSocket As Socket = Nothing  
    Public BufferSize As Integer = 1024  
    Public buffer(BufferSize) As Byte  
    Public sb As New StringBuilder()  
End Class 'StateObject  
```  
  
```csharp  
public class StateObject 
{  
    public Socket workSocket = null;  
    public const int BufferSize = 1024;  
    public byte[] buffer = new byte[BufferSize];  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 開始從用戶端通訊端接收資料的 `AcceptCallback` 方法的個區段首先會初始化 `StateObject` 類別的執行個體，然後呼叫 <xref:System.Net.Sockets.Socket.BeginReceive%2A> 方法，開始以非同步方式從用戶端通訊端讀取資料。  
  
 下列範例示範完整的 `AcceptCallback` 方法。 它假設有一個名為 `allDone,` 的全域 **ManualResetEvent**，且其 `StateObject` 類別已定義，以及已在名為 `SocketListener` 的類別中定義 `ReadCallback` 方法。  
  
```vb  
Public Shared Sub AcceptCallback(ar As IAsyncResult)  
    ' Get the socket that handles the client request.  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Signal the main thread to continue.  
    allDone.Set()  
  
    ' Create the state object.  
    Dim state As New StateObject()  
    state.workSocket = handler  
    handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
        AddressOf AsynchronousSocketListener.ReadCallback, state)  
End Sub 'AcceptCallback  
```  
  
```csharp  
public static void AcceptCallback(IAsyncResult ar)
{  
    // Get the socket that handles the client request.  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Signal the main thread to continue.  
    allDone.Set();  
  
    // Create the state object.  
    StateObject state = new StateObject();  
    state.workSocket = handler;  
    handler.BeginReceive(state.buffer, 0, StateObject.BufferSize, 0,  
        new AsyncCallback(AsynchronousSocketListener.ReadCallback), state);  
}  
```  
  
 非同步通訊端伺服器必須實作的最後一個方法是讀取回呼方法，以傳回用戶端所傳送的資料。 如同接受回呼方法一樣，讀取回呼方法是 **AsyncCallback** 委派。 這個方法會從用戶端通訊端讀取一或多個位元組到資料緩衝區，然後重新呼叫 **BeginReceive** 方法，直到用戶端所傳送的資料完整為止。 從用戶端讀取整個訊息後，字串就會顯示在主控台上，並關閉處理用戶端連線的伺服器通訊端。  
  
 下列範例會實作 `ReadCallback` 方法。 它假設已定義了 `StateObject` 類別。  
  
```vb  
Public Shared Sub ReadCallback(ar As IAsyncResult)  
    Dim state As StateObject = CType(ar.AsyncState, StateObject)  
    Dim handler As Socket = state.workSocket  
  
    ' Read data from the client socket.   
    Dim read As Integer = handler.EndReceive(ar)  
  
    ' Data was read from the client socket.  
    If read > 0 Then  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, read))  
        handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf ReadCallback, state)  
    Else  
        If state.sb.Length > 1 Then  
            ' All the data has been read from the client;  
            ' display it on the console.  
            Dim content As String = state.sb.ToString()  
            Console.WriteLine($"Read {content.Length} bytes from socket. {ControlChars.Cr} Data : {content}")  
        End If  
    End If  
End Sub 'ReadCallback  
```  
  
```csharp  
public static void ReadCallback(IAsyncResult ar)
{  
    StateObject state = (StateObject) ar.AsyncState;  
    Socket handler = state.WorkSocket;  
  
    // Read data from the client socket.  
    int read = handler.EndReceive(ar);  
  
    // Data was read from the client socket.  
    if (read > 0)
    {  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,read));  
        handler.BeginReceive(state.buffer, 0, StateObject.BufferSize, 0,  
            new AsyncCallback(ReadCallback), state);  
    } 
    else 
    {  
        if (state.sb.Length > 1) 
        {  
            // All the data has been read from the client;  
            // display it on the console.  
            string content = state.sb.ToString();  
            Console.WriteLine($"Read {content.Length} bytes from socket.\n Data : {content}");
        }  
        handler.Close();  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱

- [使用同步伺服器通訊端](using-a-synchronous-server-socket.md)
- [非同步伺服器通訊端範例](asynchronous-server-socket-example.md)
- [執行緒處理](../../standard/threading/index.md)
- [透過通訊端接聽](listening-with-sockets.md)

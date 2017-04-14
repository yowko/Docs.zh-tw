---
title: "使用非同步伺服器通訊端 | Microsoft Docs"
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
  - "通訊端類別，非同步伺服器通訊端"
  - "資料要求，通訊端"
  - "通訊端，非同步伺服器通訊端"
  - "從網際網路要求資料，通訊端"
  - "伺服器通訊端"
  - "接收資料，通訊端"
  - "非同步伺服器通訊端"
  - "通訊協定，通訊端"
  - "網際網路，通訊端"
ms.assetid: 813489a9-3efd-41b6-a33f-371d55397676
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# 使用非同步伺服器通訊端
非同步通訊端伺服器使用 .NET Framework 非同步程式設計模型中處理 Web 服務要求。  <xref:System.Net.Sockets.Socket> 類別遵循標準 .NET Framework 非同步命名模式，例如，同步處理 <xref:System.Net.Sockets.Socket.Accept%2A> 方法對應於非同步 <xref:System.Net.Sockets.Socket.BeginAccept%2A> 和 <xref:System.Net.Sockets.Socket.EndAccept%2A> 方法。  
  
 非同步通訊端伺服器需要方法開始從網際網路、回呼方法以處理連接要求並開始接收資料從網路和回呼方法的連接要求結束接收資料。  這些方法會進一步將在此章節中討論。  
  
 在下列範例中，啟動接受來自網路的連接要求，則方法 `StartListening` 初始化 **Socket** 然後使用 **BeginAccept** 方法開始接受新的連接。  當新的連接要求在通訊端時，接收接受呼叫的回呼方法。  它會取得處理連接和送出該 **Socket** 對執行緒處理要求的執行個體 **Socket** 負責。  接受回呼方法實作 <xref:System.AsyncCallback> 委派;它會傳回虛值 \(Void\) 且 <xref:System.IAsyncResult>採用型別的單一參數。  下列範例是接受回呼方法的 Shell。  
  
```vb  
Sub acceptCallback(ar As IAsyncResult)  
    ' Add the callback code here.  
End Sub 'acceptCallback  
```  
  
```csharp  
void acceptCallback( IAsyncResult ar) {  
    // Add the callback code here.  
}  
```  
  
 **BeginAccept** 方法採用兩個參數，並接受回呼方法和物件來建立回呼方法傳遞狀態資訊的 **AsyncCallback** 委派。  在下列範例中，接聽的 **Socket** 傳遞至回呼方法 *狀態* 參數。  這個範例會建立 **AsyncCallback** 委派並啟動接受來自網路的連線。  
  
```vb  
listener.BeginAccept( _  
    New AsyncCallback(SocketListener.acceptCallback),_  
    listener)  
```  
  
```csharp  
listener.BeginAccept(  
    new AsyncCallback(SocketListener.acceptCallback),   
    listener);  
```  
  
 從系統的非同步通訊端使用執行緒集區處理連入連線。  一個執行緒會接受連接管理，另一個執行緒來處理每個連入連線，，而另一個執行緒加入至以接收連接資料管理。  這些都是相同的執行緒，執行緒會由執行緒集區指派。  在下列範例中，當執行，無法繼續執行時， <xref:System.Threading.ManualResetEvent?displayProperty=fullName> 類別暫停主執行緒和信號的執行。  
  
 下列範例顯示在本機電腦上建立非同步 TCP\/IP 通訊端 \(Socket\) 並啟動接受連接的非同步方法。  這個範例假設有一個名為， `allDone`的全域 **ManualResetEvent** ，方法是 `SocketListener`名稱為的類別成員，，且名為 `acceptCallback` 的回呼方法中定義。  
  
```vb  
Public Sub StartListening()  
    Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
    Dim localEP = New IPEndPoint(ipHostInfo.AddressList(0), 11000)  
  
    Console.WriteLine("Local address and port : {0}", localEP.ToString())  
  
    Dim listener As New Socket(localEP.Address.AddressFamily, _  
       SocketType.Stream, ProtocolType.Tcp)  
  
    Try  
        listener.Bind(localEP)  
        listener.Listen(10)  
  
        While True  
            allDone.Reset()  
  
            Console.WriteLine("Waiting for a connection...")  
            listener.BeginAccept(New _  
                AsyncCallback(SocketListener.acceptCallback), _  
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
public void StartListening() {  
    IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
    IPEndPoint localEP = new IPEndPoint(ipHostInfo.AddressList[0],11000);  
  
    Console.WriteLine("Local address and port : {0}",localEP.ToString());  
  
    Socket listener = new Socket( localEP.Address.AddressFamily,  
        SocketType.Stream, ProtocolType.Tcp );  
  
    try {  
        listener.Bind(localEP);  
        listener.Listen(10);  
  
        while (true) {  
            allDone.Reset();  
  
            Console.WriteLine("Waiting for a connection...");  
            listener.BeginAccept(  
                new AsyncCallback(SocketListener.acceptCallback),   
                listener );  
  
            allDone.WaitOne();  
        }  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
  
    Console.WriteLine( "Closing the listener...");  
}  
```  
  
 接受回呼方法 \(在上述範例中的`acceptCallback` \) 到通知主應用程式執行緒負責繼續處理，建立與用戶端的連線並開始非同步讀取來自用戶端的資料。  下列範例是 `acceptCallback` 方法實作的第一個部分。  方法的這個部分通知主應用程式執行緒繼續處理並建立與用戶端的連線。  它會假設名為 `allDone`的全域 **ManualResetEvent** 。  
  
```vb  
Public Sub acceptCallback(ar As IAsyncResult)  
    allDone.Set()  
  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Additional code to read data goes here.  
End Sub 'acceptCallback  
```  
  
```csharp  
public void acceptCallback(IAsyncResult ar) {  
    allDone.Set();  
  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Additional code to read data goes here.    
}  
```  
  
 從用戶端讀取通訊端的資料要求傳遞值在非同步呼叫之間的狀態物件。  下列範例會實作接收的資料將狀態物件從這個遠端用戶端。  它包含用戶端通訊端、資料緩衝區接收的資料和 <xref:System.Text.StringBuilder> 的欄位建立的用戶端傳送的資料字串。  將這些欄位在狀態物件允許其值跨多個呼叫將會從用戶端通訊端的資料。  
  
```vb  
Public Class StateObject  
    Public workSocket As Socket = Nothing  
    Public BufferSize As Integer = 1024  
    Public buffer(BufferSize) As Byte  
    Public sb As New StringBuilder()  
End Class 'StateObject  
```  
  
```csharp  
public class StateObject {  
    public Socket workSocket = null;  
    public const int BufferSize = 1024;  
    public byte[] buffer = new byte[BufferSize];  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 一開始先接收資料從用戶端通訊端 `acceptCallback` 方法的一部分 `StateObject` 初始化類別的執行個體會呼叫方法 <xref:System.Net.Sockets.Socket.BeginReceive%2A> 開始讀取用戶端通訊端的資料同步。  
  
 下列範例顯示完整 `acceptCallback` 方法。  這個範例假設有一個名為， `StateObject` 類別中定義的 `allDone,` 的全域 **ManualResetEvent** 和 `readCallback` 方法在類別中定義名為 `SocketListener`。  
  
```vb  
Public Shared Sub acceptCallback(ar As IAsyncResult)  
    ' Get the socket that handles the client request.  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Signal the main thread to continue.  
    allDone.Set()  
  
    ' Create the state object.  
    Dim state As New StateObject()  
    state.workSocket = handler  
    handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
        AddressOf AsynchronousSocketListener.readCallback, state)  
End Sub 'acceptCallback  
  
```  
  
```csharp  
public static void acceptCallback(IAsyncResult ar) {  
    // Get the socket that handles the client request.  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Signal the main thread to continue.  
    allDone.Set();  
  
    // Create the state object.  
    StateObject state = new StateObject();  
    state.workSocket = handler;  
    handler.BeginReceive( state.buffer, 0, StateObject.BufferSize, 0,  
        new AsyncCallback(AsynchronousSocketListener.readCallback), state);  
}  
```  
  
 需要進行非同步通訊端伺服器執行的是 Final 方法傳回用戶端所傳送之資料的讀取的回呼方法。  就像接受回呼方法，讀取回呼方法是 **AsyncCallback** 委派。  這個方法會從用戶端通訊端的一個或多個位元組至資料緩衝區 **BeginReceive** 然後再次呼叫方法，直到用戶端傳送的資料都完成為止。  一旦所有訊息從用戶端讀取，字串會顯示在主控台上，與管理用戶端的伺服器通訊端連接已關閉。  
  
 下列範例會執行 `readCallback` 方法。  這個範例假設， `StateObject` 類別中定義。  
  
```vb  
Public Shared Sub readCallback(ar As IAsyncResult)  
    Dim state As StateObject = CType(ar.AsyncState, StateObject)  
    Dim handler As Socket = state.workSocket  
  
    ' Read data from the client socket.   
    Dim read As Integer = handler.EndReceive(ar)  
  
    ' Data was read from the client socket.  
    If read > 0 Then  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, read))  
        handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf readCallback, state)  
    Else  
        If state.sb.Length > 1 Then  
            ' All the data has been read from the client;  
            ' display it on the console.  
            Dim content As String = state.sb.ToString()  
            Console.WriteLine("Read {0} bytes from socket." + _  
                ControlChars.Cr + " Data : {1}", content.Length, content)  
        End If  
    End If  
End Sub 'readCallback  
  
```  
  
```csharp  
public static void readCallback(IAsyncResult ar) {  
    StateObject state = (StateObject) ar.AsyncState;  
    Socket handler = state.WorkSocket;  
  
    // Read data from the client socket.  
    int read = handler.EndReceive(ar);  
  
    // Data was read from the client socket.  
    if (read > 0) {  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,read));  
        handler.BeginReceive(state.buffer,0,StateObject.BufferSize, 0,  
            new AsyncCallback(readCallback), state);  
    } else {  
        if (state.sb.Length > 1) {  
            // All the data has been read from the client;  
            // display it on the console.  
            string content = state.sb.ToString();  
            Console.WriteLine("Read {0} bytes from socket.\n Data : {1}",  
               content.Length, content);  
        }  
        handler.Close();  
    }  
}  
```  
  
## 請參閱  
 [使用同步伺服器通訊端](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)   
 [非同步伺服器通訊端範例](../../../docs/framework/network-programming/asynchronous-server-socket-example.md)   
 [Threading](../../../docs/standard/threading/index.md)   
 [透過通訊端接聽](../../../docs/framework/network-programming/listening-with-sockets.md)
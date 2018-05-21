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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ad52291f5f5f40a65d2f9ec1c07bfb3a3f39fc01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="using-an-asynchronous-server-socket"></a><span data-ttu-id="abc4e-102">使用非同步伺服器通訊端</span><span class="sxs-lookup"><span data-stu-id="abc4e-102">Using an Asynchronous Server Socket</span></span>
<span data-ttu-id="abc4e-103">非同步伺服器通訊端會使用 .NET Framework 非同步程式設計模型來處理網路服務要求。</span><span class="sxs-lookup"><span data-stu-id="abc4e-103">Asynchronous server sockets use the .NET Framework asynchronous programming model to process network service requests.</span></span> <span data-ttu-id="abc4e-104"><xref:System.Net.Sockets.Socket> 類別會遵循標準 .NET Framework 非同步命名模式；例如，同步 <xref:System.Net.Sockets.Socket.Accept%2A> 方法對應於非同步 <xref:System.Net.Sockets.Socket.BeginAccept%2A> 和 <xref:System.Net.Sockets.Socket.EndAccept%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="abc4e-104">The <xref:System.Net.Sockets.Socket> class follows the standard .NET Framework asynchronous naming pattern; for example, the synchronous <xref:System.Net.Sockets.Socket.Accept%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginAccept%2A> and <xref:System.Net.Sockets.Socket.EndAccept%2A> methods.</span></span>  
  
 <span data-ttu-id="abc4e-105">非同步伺服器通訊端需要一個用來開始接受網路連線要求的方法、一個用來處理連線要求並開始接收網路資料的回呼方法，以及一個用來結束接收資料的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="abc4e-105">An asynchronous server socket requires a method to begin accepting connection requests from the network, a callback method to handle the connection requests and begin receiving data from the network, and a callback method to end receiving the data.</span></span> <span data-ttu-id="abc4e-106">本節會進一步討論所有這些方法。</span><span class="sxs-lookup"><span data-stu-id="abc4e-106">All these methods are discussed further in this section.</span></span>  
  
 <span data-ttu-id="abc4e-107">在下列範例中，若要開始接受網路的連線要求，`StartListening` 方法會初始化**通訊端**，然後使用 **BeginAccept** 方法來開始接受新連線。</span><span class="sxs-lookup"><span data-stu-id="abc4e-107">In the following example, to begin accepting connection requests from the network, the method `StartListening` initializes the **Socket** and then uses the **BeginAccept** method to start accepting new connections.</span></span> <span data-ttu-id="abc4e-108">在通訊端上收到新的連線要求時，就會呼叫接受回呼方法。</span><span class="sxs-lookup"><span data-stu-id="abc4e-108">The accept callback method is called when a new connection request is received on the socket.</span></span> <span data-ttu-id="abc4e-109">它會負責取得將處理連線的**通訊端**執行個體，並將該**通訊端**移交給將處理要求的執行緒。</span><span class="sxs-lookup"><span data-stu-id="abc4e-109">It is responsible for getting the **Socket** instance that will handle the connection and handing that **Socket** off to the thread that will process the request.</span></span> <span data-ttu-id="abc4e-110">接受回呼方法會實作 <xref:System.AsyncCallback> 委派；它會傳回 void，並採用 <xref:System.IAsyncResult> 類型的單一參數。</span><span class="sxs-lookup"><span data-stu-id="abc4e-110">The accept callback method implements the <xref:System.AsyncCallback> delegate; it returns a void and takes a single parameter of type <xref:System.IAsyncResult>.</span></span> <span data-ttu-id="abc4e-111">下列範例是接受回呼方法的殼層。</span><span class="sxs-lookup"><span data-stu-id="abc4e-111">The following example is the shell of an accept callback method.</span></span>  
  
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
  
 <span data-ttu-id="abc4e-112">**BeginAccept** 方法採用兩個參數：指向接受回呼方法的 **AsyncCallback** 委派和用來將狀態資訊傳遞至回呼方法的物件。</span><span class="sxs-lookup"><span data-stu-id="abc4e-112">The **BeginAccept** method takes two parameters, an **AsyncCallback** delegate that points to the accept callback method and an object that is used to pass state information to the callback method.</span></span> <span data-ttu-id="abc4e-113">在下列範例中，接聽**通訊端**會透過 *stat* 參數傳遞至回呼方法。</span><span class="sxs-lookup"><span data-stu-id="abc4e-113">In the following example, the listening **Socket** is passed to the callback method through the *state* parameter.</span></span> <span data-ttu-id="abc4e-114">這個範例會建立 **AsyncCallback** 委派並開始接受來自網路的連線。</span><span class="sxs-lookup"><span data-stu-id="abc4e-114">This example creates an **AsyncCallback** delegate and starts accepting connections from the network.</span></span>  
  
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
  
 <span data-ttu-id="abc4e-115">非同步通訊端使用系統執行緒集區中的執行緒來處理連入連線。</span><span class="sxs-lookup"><span data-stu-id="abc4e-115">Asynchronous sockets use threads from the system thread pool to process incoming connections.</span></span> <span data-ttu-id="abc4e-116">其中一個執行緒負責接受連線、另一個執行緒用來處理每個連入連線，還有一個執行緒負責接收來自連線的資料。</span><span class="sxs-lookup"><span data-stu-id="abc4e-116">One thread is responsible for accepting connections, another thread is used to handle each incoming connection, and another thread is responsible for receiving data from the connection.</span></span> <span data-ttu-id="abc4e-117">這些可能是相同的執行緒，視執行緒集區所指派的執行緒而定。</span><span class="sxs-lookup"><span data-stu-id="abc4e-117">These could be the same thread, depending on which thread is assigned by the thread pool.</span></span> <span data-ttu-id="abc4e-118">在下列範例中，<xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> 類別會暫停執行主執行緒，並在可以繼續執行時發出訊號。</span><span class="sxs-lookup"><span data-stu-id="abc4e-118">In the following example, the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class suspends execution of the main thread and signals when execution can continue.</span></span>  
  
 <span data-ttu-id="abc4e-119">下列範例示範非同步方法，用來在本機電腦上建立非同步的 TCP/IP 通訊端，並開始接受連接。</span><span class="sxs-lookup"><span data-stu-id="abc4e-119">The following example shows an asynchronous method that creates an asynchronous TCP/IP socket on the local computer and begins accepting connections.</span></span> <span data-ttu-id="abc4e-120">它假設有一個名為 `allDone` 的全域 **ManualResetEvent**且該方法是 `SocketListener` 類別的成員，以及已定義名為 `acceptCallback` 的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="abc4e-120">It assumes that there is a global **ManualResetEvent** named `allDone`, that the method is a member of a class named `SocketListener`, and that a callback method named `acceptCallback` is defined.</span></span>  
  
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
  
 <span data-ttu-id="abc4e-121">接受回呼方法 (在上述範例中為 `acceptCallback`) 負責指示主要應用程式執行緒繼續處理、建立與用戶端的連線，以及開始從用戶端非同步讀取資料。</span><span class="sxs-lookup"><span data-stu-id="abc4e-121">The accept callback method (`acceptCallback` in the preceding example) is responsible for signaling the main application thread to continue processing, establishing the connection with the client, and starting the asynchronous read of data from the client.</span></span> <span data-ttu-id="abc4e-122">下列範例是 `acceptCallback` 方法實作的第一部分。</span><span class="sxs-lookup"><span data-stu-id="abc4e-122">The following example is the first part of an implementation of the `acceptCallback` method.</span></span> <span data-ttu-id="abc4e-123">該方法的這個區段會指示主要應用程式執行緒繼續處理，並建立與用戶端的連線。</span><span class="sxs-lookup"><span data-stu-id="abc4e-123">This section of the method signals the main application thread to continue processing and establishes the connection to the client.</span></span> <span data-ttu-id="abc4e-124">它會假設一個名為 `allDone` 的全域 **ManualResetEvent**。</span><span class="sxs-lookup"><span data-stu-id="abc4e-124">It assumes a global **ManualResetEvent** named `allDone`.</span></span>  
  
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
  
 <span data-ttu-id="abc4e-125">從用戶端通訊端讀取資料時，需要在非同步呼叫之間傳遞值的狀態物件。</span><span class="sxs-lookup"><span data-stu-id="abc4e-125">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="abc4e-126">下列範例會實作從遠端用戶端接收字串的狀態物件。</span><span class="sxs-lookup"><span data-stu-id="abc4e-126">The following example implements a state object for receiving a string from the remote client.</span></span> <span data-ttu-id="abc4e-127">其包含用於用戶端通訊端的欄位、用來接收資料的資料緩衝區，以及用來建立用戶端所傳送資料字串的 <xref:System.Text.StringBuilder>。</span><span class="sxs-lookup"><span data-stu-id="abc4e-127">It contains fields for the client socket, a data buffer for receiving data, and a <xref:System.Text.StringBuilder> for creating the data string sent by the client.</span></span> <span data-ttu-id="abc4e-128">將這些欄位放置在狀態物件，可允許在多個呼叫間保留其值，以從用戶端通訊端讀取資料。</span><span class="sxs-lookup"><span data-stu-id="abc4e-128">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
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
  
 <span data-ttu-id="abc4e-129">開始從用戶端通訊端接收資料的 `acceptCallback` 方法的個區段首先會初始化 `StateObject` 類別的執行個體，然後呼叫 <xref:System.Net.Sockets.Socket.BeginReceive%2A> 方法，開始以非同步方式從用戶端通訊端讀取資料。</span><span class="sxs-lookup"><span data-stu-id="abc4e-129">The section of the `acceptCallback` method that starts receiving the data from the client socket first initializes an instance of the `StateObject` class and then calls the <xref:System.Net.Sockets.Socket.BeginReceive%2A> method to start reading the data from the client socket asynchronously.</span></span>  
  
 <span data-ttu-id="abc4e-130">下列範例示範完整的 `acceptCallback` 方法。</span><span class="sxs-lookup"><span data-stu-id="abc4e-130">The following example shows the complete `acceptCallback` method.</span></span> <span data-ttu-id="abc4e-131">它假設有一個名為 `allDone,` 的全域 **ManualResetEvent**，且其 `StateObject` 類別已定義，以及已在名為 `SocketListener` 的類別中定義 `readCallback` 方法。</span><span class="sxs-lookup"><span data-stu-id="abc4e-131">It assumes that there is a global **ManualResetEvent** named `allDone,` that the `StateObject` class is defined, and that the `readCallback` method is defined in a class named `SocketListener`.</span></span>  
  
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
  
 <span data-ttu-id="abc4e-132">非同步通訊端伺服器必須實作的最後一個方法是讀取回呼方法，以傳回用戶端所傳送的資料。</span><span class="sxs-lookup"><span data-stu-id="abc4e-132">The final method that needs to be implemented for the asynchronous socket server is the read callback method that returns the data sent by the client.</span></span> <span data-ttu-id="abc4e-133">如同接受回呼方法一樣，讀取回呼方法是 **AsyncCallback** 委派。</span><span class="sxs-lookup"><span data-stu-id="abc4e-133">Like the accept callback method, the read callback method is an **AsyncCallback** delegate.</span></span> <span data-ttu-id="abc4e-134">這個方法會從用戶端通訊端讀取一或多個位元組到資料緩衝區，然後重新呼叫 **BeginReceive** 方法，直到用戶端所傳送的資料完整為止。</span><span class="sxs-lookup"><span data-stu-id="abc4e-134">This method reads one or more bytes from the client socket into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="abc4e-135">從用戶端讀取整個訊息後，字串就會顯示在主控台上，並關閉處理用戶端連線的伺服器通訊端。</span><span class="sxs-lookup"><span data-stu-id="abc4e-135">Once the entire message has been read from the client, the string is displayed on the console and the server socket handling the connection to the client is closed.</span></span>  
  
 <span data-ttu-id="abc4e-136">下列範例會實作 `readCallback` 方法。</span><span class="sxs-lookup"><span data-stu-id="abc4e-136">The following sample implements the `readCallback` method.</span></span> <span data-ttu-id="abc4e-137">它假設已定義了 `StateObject` 類別。</span><span class="sxs-lookup"><span data-stu-id="abc4e-137">It assumes that the `StateObject` class is defined.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="abc4e-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="abc4e-138">See Also</span></span>  
 [<span data-ttu-id="abc4e-139">使用同步伺服器通訊端</span><span class="sxs-lookup"><span data-stu-id="abc4e-139">Using a Synchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)  
 [<span data-ttu-id="abc4e-140">非同步伺服器通訊端範例</span><span class="sxs-lookup"><span data-stu-id="abc4e-140">Asynchronous Server Socket Example</span></span>](../../../docs/framework/network-programming/asynchronous-server-socket-example.md)  
 [<span data-ttu-id="abc4e-141">執行緒處理</span><span class="sxs-lookup"><span data-stu-id="abc4e-141">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="abc4e-142">透過通訊端接聽</span><span class="sxs-lookup"><span data-stu-id="abc4e-142">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)

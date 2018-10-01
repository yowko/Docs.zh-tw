---
title: 使用非同步用戶端通訊端
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: f4ab27a8e6cc5bd38620148b130823070e5102fa
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47198445"
---
# <a name="using-an-asynchronous-client-socket"></a><span data-ttu-id="b5bd6-102">使用非同步用戶端通訊端</span><span class="sxs-lookup"><span data-stu-id="b5bd6-102">Using an Asynchronous Client Socket</span></span>
<span data-ttu-id="b5bd6-103">非同步用戶端通訊端等待網路作業完成時，不會暫停應用程式。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-103">An asynchronous client socket does not suspend the application while waiting for network operations to complete.</span></span> <span data-ttu-id="b5bd6-104">相反地，它會使用標準 .NET Framework 非同步程式設計模型，在一個執行緒上處理網路連線，同時應用程式繼續在原始執行緒上執行。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-104">Instead, it uses the standard .NET Framework asynchronous programming model to process the network connection on one thread while the application continues to run on the original thread.</span></span> <span data-ttu-id="b5bd6-105">非同步通訊端適用於大量使用網路的應用程式，或是無法等候網路作業完成再繼續進行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-105">Asynchronous sockets are appropriate for applications that make heavy use of the network or that cannot wait for network operations to complete before continuing.</span></span>  
  
 <span data-ttu-id="b5bd6-106"><xref:System.Net.Sockets.Socket> 類別遵循非同步方法的 .NET Framework 命名模式；例如，同步 <xref:System.Net.Sockets.Socket.Receive%2A> 方法對應於非同步 <xref:System.Net.Sockets.Socket.BeginReceive%2A> 和 <xref:System.Net.Sockets.Socket.EndReceive%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-106">The <xref:System.Net.Sockets.Socket> class follows the .NET Framework naming pattern for asynchronous methods; for example, the synchronous <xref:System.Net.Sockets.Socket.Receive%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginReceive%2A> and <xref:System.Net.Sockets.Socket.EndReceive%2A> methods.</span></span>  
  
 <span data-ttu-id="b5bd6-107">非同步作業需要回呼方法以傳回作業的結果。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-107">Asynchronous operations require a callback method to return the result of the operation.</span></span> <span data-ttu-id="b5bd6-108">如果您的應用程式不需要知道結果，則不需要回呼方法。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-108">If your application does not need to know the result, then no callback method is required.</span></span> <span data-ttu-id="b5bd6-109">本節的範例程式碼示範如何使用方法來開始連線到網路裝置以及使用回呼方法完成連線、使用方法開始傳送資料以及使用回呼方法完成傳送，還有使用方法開始接收資料以及使用回呼方法結束接收資料。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-109">The example code in this section demonstrates using a method to start connecting to a network device and a callback method to complete the connection, a method to start sending data and a callback method to complete the send, and a method to start receiving data and a callback method to end receiving data.</span></span>  
  
 <span data-ttu-id="b5bd6-110">非同步通訊端使用系統執行緒集區中的多個執行緒來處理網路連線。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-110">Asynchronous sockets use multiple threads from the system thread pool to process network connections.</span></span> <span data-ttu-id="b5bd6-111">一個執行緒負責初始化資料的傳送或接收；其他執行緒則完成與網路裝置的連線並且傳送或接收資料。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-111">One thread is responsible for initiating the sending or receiving of data; other threads complete the connection to the network device and send or receive the data.</span></span> <span data-ttu-id="b5bd6-112">在下列範例中，<xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> 類別的執行個體會暫停執行主執行緒，並在可以繼續執行時發出訊號。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-112">In the following examples, instances of the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class are used to suspend execution of the main thread and signal when execution can continue.</span></span>  
  
 <span data-ttu-id="b5bd6-113">在下列範例中，為了將非同步通訊端連線到網路裝置，`Connect` 方法會初始化**通訊端**，然後呼叫 <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> 方法、傳遞代表網路裝置的遠端端點、連線回呼方法和狀態物件 (用戶端**通訊端**)，這用來在非同步呼叫之間傳遞狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-113">In the following example, to connect an asynchronous socket to a network device, the `Connect` method initializes a **Socket** and then calls the <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> method, passing a remote endpoint that represents the network device, the connect callback method, and a state object (the client **Socket**), which is used to pass state information between asynchronous calls.</span></span> <span data-ttu-id="b5bd6-114">此範例會實作 `Connect` 方法，將指定的**通訊端**連線到指定的端點。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-114">The example implements the `Connect` method to connect the specified **Socket** to the specified endpoint.</span></span> <span data-ttu-id="b5bd6-115">它會假設一個名為 `connectDone` 的全域 **ManualResetEvent**。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-115">It assumes a global **ManualResetEvent** named `connectDone`.</span></span>  
  
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
  
 <span data-ttu-id="b5bd6-116">連線回呼方法 `ConnectCallback` 會實作 <xref:System.AsyncCallback> 委派。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-116">The connect callback method `ConnectCallback` implements the <xref:System.AsyncCallback> delegate.</span></span> <span data-ttu-id="b5bd6-117">它在遠端裝置可用時連線到遠端裝置，然後設定**ManualResetEvent** `connectDone`，通知應用程式執行緒連線已完成。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-117">It connects to the remote device when the remote device is available and then signals the application thread that the connection is complete by setting the **ManualResetEvent** `connectDone`.</span></span> <span data-ttu-id="b5bd6-118">下例程式碼會實作 `ConnectCallback` 方法。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-118">The following code implements the `ConnectCallback` method.</span></span>  
  
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
  
 <span data-ttu-id="b5bd6-119">範例方法 `Send` 將指定的字串資料以 ASCII 格式編碼，並將它以非同步方式傳送到指定通訊端所代表的網路裝置。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-119">The example method `Send` encodes the specified string data in ASCII format and sends it asynchronously to the network device represented by the specified socket.</span></span> <span data-ttu-id="b5bd6-120">下列範例會實作 `Send` 方法。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-120">The following example implements the `Send` method.</span></span>  
  
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
  
 <span data-ttu-id="b5bd6-121">傳送回呼方法 `SendCallback` 會實作 <xref:System.AsyncCallback> 委派。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-121">The send callback method `SendCallback` implements the <xref:System.AsyncCallback> delegate.</span></span> <span data-ttu-id="b5bd6-122">網路裝置準備好接收時，它會傳送資料。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-122">It sends the data when the network device is ready to receive.</span></span> <span data-ttu-id="b5bd6-123">下列範例會示範 `SendCallback` 方法的實作。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-123">The following example shows the implementation of the `SendCallback` method.</span></span> <span data-ttu-id="b5bd6-124">它會假設一個名為 `sendDone` 的全域 **ManualResetEvent**。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-124">It assumes a global **ManualResetEvent** named `sendDone`.</span></span>  
  
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
  
 <span data-ttu-id="b5bd6-125">從用戶端通訊端讀取資料時，需要在非同步呼叫之間傳遞值的狀態物件。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-125">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="b5bd6-126">下列類別是從用戶端通訊端接收資料的範例狀態物件。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-126">The following class is an example state object for receiving data from a client socket.</span></span> <span data-ttu-id="b5bd6-127">它包含用戶端通訊端的欄位、已接收資料的緩衝區，以及儲存進入之資料字串的 <xref:System.Text.StringBuilder>。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-127">It contains a field for the client socket, a buffer for the received data, and a <xref:System.Text.StringBuilder> to hold the incoming data string.</span></span> <span data-ttu-id="b5bd6-128">將這些欄位放置在狀態物件，可允許在多個呼叫間保留其值，以從用戶端通訊端讀取資料。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-128">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
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
  
 <span data-ttu-id="b5bd6-129">`Receive` 方法範例會設定狀態物件，然後呼叫 **BeginReceive** 方法，以非同步方式從用戶端通訊端讀取資料。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-129">The example `Receive` method sets up the state object and then calls the **BeginReceive** method to read the data from the client socket asynchronously.</span></span> <span data-ttu-id="b5bd6-130">下列範例會實作 `Receive` 方法。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-130">The following example implements the `Receive` method.</span></span>  
  
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
  
 <span data-ttu-id="b5bd6-131">接收回呼方法 `ReceiveCallback` 會實作 **AsyncCallback** 委派。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-131">The receive callback method `ReceiveCallback` implements the **AsyncCallback** delegate.</span></span> <span data-ttu-id="b5bd6-132">它會從網路裝置接收資料，並建立訊息字串。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-132">It receives the data from the network device and builds a message string.</span></span> <span data-ttu-id="b5bd6-133">它會將來自網路的一或多個位元組資料讀取到資料緩衝區，然後重新呼叫 **BeginReceive** 方法，直到用戶端所傳送的資料完整為止。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-133">It reads one or more bytes of data from the network into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="b5bd6-134">從用戶端讀取所有資料之後，`ReceiveCallback` 會設定 **ManualResetEvent** `sendDone` 通知應用程式執行緒資料已完整。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-134">Once all the data is read from the client, `ReceiveCallback` signals the application thread that the data is complete by setting the **ManualResetEvent** `sendDone`.</span></span>  
  
 <span data-ttu-id="b5bd6-135">下列範例程式碼會實作 `ReceiveCallback` 方法。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-135">The following example code implements the `ReceiveCallback` method.</span></span> <span data-ttu-id="b5bd6-136">它會假設名為 `response` 的全域字串負責保存收到的字串，以及一個名為 `receiveDone` 的全域 **ManualResetEvent**。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-136">It assumes a global string named `response` that holds the received string and a global **ManualResetEvent** named `receiveDone`.</span></span> <span data-ttu-id="b5bd6-137">伺服器必須先依正常程序關閉用戶端通訊端，結束網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="b5bd6-137">The server must shut down the client socket gracefully to end the network session.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b5bd6-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="b5bd6-138">See Also</span></span>  
 [<span data-ttu-id="b5bd6-139">使用同步用戶端通訊端</span><span class="sxs-lookup"><span data-stu-id="b5bd6-139">Using a Synchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)  
 [<span data-ttu-id="b5bd6-140">透過通訊端接聽</span><span class="sxs-lookup"><span data-stu-id="b5bd6-140">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)  
 [<span data-ttu-id="b5bd6-141">非同步用戶端通訊端範例</span><span class="sxs-lookup"><span data-stu-id="b5bd6-141">Asynchronous Client Socket Example</span></span>](../../../docs/framework/network-programming/asynchronous-client-socket-example.md)

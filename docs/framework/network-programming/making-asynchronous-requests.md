---
title: "進行非同步要求 | Microsoft Docs"
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
  - "取網際網路，非同步存取"
  - "網路"
  - "非同步要求，網際網路資源"
  - "網路資源"
  - "WebRequest 類別，非同步存取"
ms.assetid: 735d3fce-f80c-437f-b02c-5c47f5739674
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# 進行非同步要求
<xref:System.Net> 類別提供對網際網路資源的非同步存取使用 .NET Framework 的標準非同步程式設計模型。  <xref:System.Net.WebRequest> 類別開始的 <xref:System.Net.WebRequest.BeginGetResponse%2A> 和 <xref:System.Net.WebRequest.EndGetResponse%2A> 方法和完成網際網路資源的非同步要求。  
  
> [!NOTE]
>  使用在非同步回呼方法的同步呼叫可能會導致嚴重的效能損失。  **WebRequest** 用做的網際網路要求及其子代 \(Descendant\) 必須使用 <xref:System.IO.Stream.BeginRead%2A?displayProperty=fullName><xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=fullName> 讀取方法所傳回的資料流。  
  
 下列程式碼範例示範如何使用 **WebRequest** 類別的非同步呼叫。  這個範例是將從命令列的 URI 的主控台程式，要求資源的 URI 中，然後將資料加入至主控台，因為它從網際網路接收。  
  
 程式會定義供本身使用的兩個類別， **RequestState** 類別，它可以跨非同步呼叫的資料和 **ClientGetAsync** 類別，實作非同步要求至網際網路資源。  
  
 **RequestState** 類別將需求的狀態跨越呼叫到服務要求的非同步方法。  它包含 **WebRequest** 和在回應包含目前要求至接收緩衝區包含來自網際網路資源目前接收的資料和 <xref:System.Text.StringBuilder> 的資源和資料流包含整個回應的 <xref:System.IO.Stream> 執行個體。  當 <xref:System.AsyncCallback> 方法移至 **WebRequest.BeginGetResponse**時， **RequestState**傳遞做為狀態參數。  
  
 **ClientGetAsync** 類別實作非同步要求至網際網路資源並寫入至主控台的回應。  它包含在下列清單和屬性描述的方法。  
  
-   `allDone` 屬性包含表示要求的完成 <xref:System.Threading.ManualResetEvent> 類別的執行個體。  
  
-   `Main()` 方法讀取命令列並啟動要求指定之網際網路資源。  它會建立 **WebRequest**`wreq` 和 **RequestState**`rs`，呼叫 **BeginGetResponse** 開始處理要求，然後呼叫方法 `allDone.WaitOne()`，讓應用程式不會結束，必須等到回呼完成。  在回應來自網際網路資源之後， `Main()` 讀取和寫入主控台應用程式結束寫入其中。  
  
-   `showusage()` 方法在主控台 \(Console\) 的範例命令列。  當要求，在命令列上，則不會提供由 `Main()` 呼叫。  
  
-   `RespCallBack()` 方法執行網際網路要求的非同步回呼方法。  它會建立包含來自網際網路資源的執行個體 **WebResponse** 回應，取得回應資料流，然後開始讀取資料流的非同步資料。  
  
-   `ReadCallBack()` 方法執行讀取回應資料流的非同步回呼方法。  它會從網際網路資源的資料傳輸接收到 **RequestState** **ResponseData** 執行個體的屬性，然後啟動另一個非同步讀取回應資料流，直到沒有其他未傳回資料。  一旦所有資料都已讀取， `ReadCallBack()` 關閉回應資料流並呼叫方法 `allDone.Set()` 表示整個回應存在於 **ResponseData**。  
  
    > [!NOTE]
    >  是重要的所有網路資料流已經關閉。  如果您不要關閉每個要求和回應資料流，您的應用程式會耗盡與伺服器的連接並無法處理其他要求。  
  
```csharp  
using System;  
using System.Net;  
using System.Threading;  
using System.Text;  
using System.IO;  
  
// The RequestState class passes data across async calls.  
public class RequestState  
{  
   const int BufferSize = 1024;  
   public StringBuilder RequestData;  
   public byte[] BufferRead;  
   public WebRequest Request;  
   public Stream ResponseStream;  
   // Create Decoder for appropriate enconding type.  
   public Decoder StreamDecode = Encoding.UTF8.GetDecoder();  
  
   public RequestState()  
   {  
      BufferRead = new byte[BufferSize];  
      RequestData = new StringBuilder(String.Empty);  
      Request = null;  
      ResponseStream = null;  
   }       
}  
  
// ClientGetAsync issues the async request.  
class ClientGetAsync   
{  
   public static ManualResetEvent allDone = new ManualResetEvent(false);  
   const int BUFFER_SIZE = 1024;  
  
   public static void Main(string[] args)   
   {  
      if (args.Length < 1)   
      {  
         showusage();  
         return;  
      }  
  
      // Get the URI from the command line.  
      Uri httpSite = new Uri(args[0]);  
  
      // Create the request object.  
      WebRequest wreq = WebRequest.Create(httpSite);  
  
      // Create the state object.  
      RequestState rs = new RequestState();  
  
      // Put the request into the state object so it can be passed around.  
      rs.Request = wreq;  
  
      // Issue the async request.  
      IAsyncResult r = (IAsyncResult) wreq.BeginGetResponse(  
         new AsyncCallback(RespCallback), rs);  
  
      // Wait until the ManualResetEvent is set so that the application   
      // does not exit until after the callback is called.  
      allDone.WaitOne();  
  
      Console.WriteLine(rs.RequestData.ToString());  
   }  
  
   public static void showusage() {  
      Console.WriteLine("Attempts to GET a URL");  
      Console.WriteLine("\r\nUsage:");  
      Console.WriteLine("   ClientGetAsync URL");  
      Console.WriteLine("   Example:");  
      Console.WriteLine("      ClientGetAsync http://www.contoso.com/");  
   }  
  
   private static void RespCallback(IAsyncResult ar)  
   {  
      // Get the RequestState object from the async result.  
      RequestState rs = (RequestState) ar.AsyncState;  
  
      // Get the WebRequest from RequestState.  
      WebRequest req = rs.Request;  
  
      // Call EndGetResponse, which produces the WebResponse object  
      //  that came from the request issued above.  
      WebResponse resp = req.EndGetResponse(ar);           
  
      //  Start reading data from the response stream.  
      Stream ResponseStream = resp.GetResponseStream();  
  
      // Store the response stream in RequestState to read   
      // the stream asynchronously.  
      rs.ResponseStream = ResponseStream;  
  
      //  Pass rs.BufferRead to BeginRead. Read data into rs.BufferRead  
      IAsyncResult iarRead = ResponseStream.BeginRead(rs.BufferRead, 0,   
         BUFFER_SIZE, new AsyncCallback(ReadCallBack), rs);   
   }  
  
   private static void ReadCallBack(IAsyncResult asyncResult)  
   {  
      // Get the RequestState object from AsyncResult.  
      RequestState rs = (RequestState)asyncResult.AsyncState;  
  
      // Retrieve the ResponseStream that was set in RespCallback.   
      Stream responseStream = rs.ResponseStream;  
  
      // Read rs.BufferRead to verify that it contains data.   
      int read = responseStream.EndRead( asyncResult );  
      if (read > 0)  
      {  
         // Prepare a Char array buffer for converting to Unicode.  
         Char[] charBuffer = new Char[BUFFER_SIZE];  
  
         // Convert byte stream to Char array and then to String.  
         // len contains the number of characters converted to Unicode.  
      int len =   
         rs.StreamDecode.GetChars(rs.BufferRead, 0, read, charBuffer, 0);  
  
         String str = new String(charBuffer, 0, len);  
  
         // Append the recently read data to the RequestData stringbuilder  
         // object contained in RequestState.  
         rs.RequestData.Append(  
            Encoding.ASCII.GetString(rs.BufferRead, 0, read));           
  
         // Continue reading data until   
         // responseStream.EndRead returns –1.  
         IAsyncResult ar = responseStream.BeginRead(   
            rs.BufferRead, 0, BUFFER_SIZE,   
            new AsyncCallback(ReadCallBack), rs);  
      }  
      else  
      {  
         if(rs.RequestData.Length>0)  
         {  
            //  Display data to the console.  
            string strContent;                    
            strContent = rs.RequestData.ToString();  
         }  
         // Close down the response stream.  
         responseStream.Close();           
         // Set the ManualResetEvent so the main thread can exit.  
         allDone.Set();                             
      }  
      return;  
   }      
}  
```  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Threading  
Imports System.Text  
Imports System.IO  
  
' The RequestState class passes data across async calls.  
Public Class RequestState  
  
      Public RequestData As New StringBuilder("")  
      Public BufferRead(1024) As Byte  
      Public Request As HttpWebRequest  
      Public ResponseStream As Stream  
      ' Create Decoder for appropriate encoding type.  
      Public StreamDecode As Decoder = Encoding.UTF8.GetDecoder()  
  
      Public Sub New  
         Request = Nothing  
         ResponseStream = Nothing  
      End Sub  
End Class  
  
' ClientGetAsync issues the async request.  
Class ClientGetAsync  
   Shared allDone As New ManualResetEvent(False)  
      Const BUFFER_SIZE As Integer = 1024  
  
    Shared Sub Main()  
        Dim Args As String() = Environment.GetCommandLineArgs()  
  
        If Args.Length < 2 Then  
            ShowUsage()  
            Return  
        End If  
  
      ' Get the URI from the command line.  
        Dim HttpSite As Uri = New Uri(Args(1))  
  
      ' Create the request object.  
        Dim wreq As HttpWebRequest = _  
           CType(WebRequest.Create(HttpSite), HttpWebRequest)  
  
      ' Create the state object.  
      Dim rs As RequestState = New RequestState()  
  
      ' Put the request into the state so it can be passed around.  
      rs.Request = wreq  
  
      ' Issue the async request.  
        Dim r As IAsyncResult = _  
           CType(wreq.BeginGetResponse( _  
           New AsyncCallback(AddressOf RespCallback), rs), IAsyncResult)  
  
      ' Wait until the ManualResetEvent is set so that the application  
      ' does not exit until after the callback is called.  
        allDone.WaitOne()  
    End Sub  
  
    Shared Sub ShowUsage()  
        Console.WriteLine("Attempts to GET a URI")  
        Console.WriteLine()  
        Console.WriteLine("Usage:")  
        Console.WriteLine("ClientGetAsync URI")  
        Console.WriteLine("Examples:")  
        Console.WriteLine("ClientGetAsync http://www.contoso.com/")  
    End Sub  
  
    Shared Sub RespCallback(ar As IAsyncResult)  
       ' Get the RequestState object from the async result.  
       Dim rs As RequestState = CType(ar.AsyncState, RequestState)  
  
       ' Get the HttpWebRequest from RequestState.  
       Dim req As HttpWebRequest= rs.Request  
  
       ' Call EndGetResponse, which returns the HttpWebResponse object  
       ' that came from the request issued above.  
       Dim resp As HttpWebResponse = _  
           CType(req.EndGetResponse(ar), HttpWebResponse)  
  
       ' Start reading data from the respons stream.  
       Dim ResponseStream As Stream = resp.GetResponseStream()  
  
       ' Store the reponse stream in RequestState to read  
       ' the stream asynchronously.  
       rs.ResponseStream = ResponseStream  
  
       ' Pass rs.BufferRead to BeginRead. Read data into rs.BufferRead.  
       Dim iarRead As IAsyncResult = _  
          ResponseStream.BeginRead(rs.BufferRead, 0, BUFFER_SIZE, _  
          New AsyncCallback(AddressOf ReadCallBack), rs)  
    End Sub  
  
   Shared Sub ReadCallBack(asyncResult As IAsyncResult)  
      ' Get the RequestState object from the AsyncResult.  
      Dim rs As RequestState = CType(asyncResult.AsyncState, RequestState)  
  
      ' Retrieve the ResponseStream that was set in RespCallback.  
      Dim responseStream As Stream = rs.ResponseStream  
  
      ' Read rs.BufferRead to verify that it contains data.  
      Dim read As Integer = responseStream.EndRead( asyncResult )  
      If read > 0 Then  
         ' Prepare a Char array buffer for converting to Unicode.  
         Dim charBuffer(1024) As Char  
  
         ' Convert byte stream to Char array and then String.  
         ' len contains the number of characters converted to Unicode.  
         Dim len As Integer = _  
           rs.StreamDecode.GetChars(rs.BufferRead, 0, read, charBuffer, 0)  
         Dim str As String = new String(charBuffer, 0, len)      
  
         ' Append the recently read data to the RequestData stringbuilder   
         ' object contained in RequestState.  
         rs.RequestData.Append( _  
            Encoding.ASCII.GetString(rs.BufferRead, 0, read))  
  
         ' Continue reading data until responseStream.EndRead  
         ' returns –1.  
         Dim ar As IAsyncResult = _  
            responseStream.BeginRead(rs.BufferRead, 0, BUFFER_SIZE, _  
            New AsyncCallback(AddressOf ReadCallBack), rs)  
      Else  
          If rs.RequestData.Length > 1 Then  
            ' Display data to the console.  
            Dim strContent As String  
            strContent = rs.RequestData.ToString()  
            Console.WriteLine(strContent)  
         End If  
  
         ' Close down the response stream.  
         responseStream.Close()  
  
         ' Set the ManualResetEvent so the main thread can exit.  
         allDone.Set()  
      End If  
  
      Return  
   End Sub  
End Class  
```  
  
## 請參閱  
 [要求資料](../../../docs/framework/network-programming/requesting-data.md)
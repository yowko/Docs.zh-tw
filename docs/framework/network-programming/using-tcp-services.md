---
title: "使用 TCP 服務 | Microsoft Docs"
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
  - "從網際網路要求資料，TCP"
  - "接收資料，TCP"
  - "TcpClient 類別，關於 TcpClient 類別"
  - "資料要求，TCP"
  - "應用程式通訊協定，TCP"
  - "網路資源，TCP"
  - "傳送資料，TCP"
  - "TCP"
  - "通訊協定，TCP"
  - "網際網路，TCP"
ms.assetid: d2811830-3bcb-495c-b82d-cda9cf919aad
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# 使用 TCP 服務
使用 TCP， <xref:System.Net.Sockets.TcpClient> 類別從網際網路資源要求的資料。  使用 TCP， **TcpClient** 方法和屬性擷取建立的 <xref:System.Net.Sockets.Socket> 詳細資料要求和接收資料。  由於與遠端裝置的連接表示為資料流，資料可以讀取和寫入資料流處理技術的 .NET Framework。  
  
 TCP 通訊協定以遠端方式傳送和接收資料封包的連接的端點會使用的連接。  TCP 負責確保資料封包傳送至端點並以正確的順序會組合在一起，當它們抵達時。  
  
 若要建立 TCP 連接，必須知道網路裝置的位址會裝載您所需服務的您，而且必須知道服務用於傳送的 TCP 通訊埠。  Internet Assigned Numbers Authority \(Iana\) 定義通用服務的通訊埠編號 \(請參閱 www.iana.org\/assignments\/port\-numbers\) \(英文\)。  服務不在 Iana 清單上可以有介於 1,024 到 65,535 的通訊埠編號。  
  
 下列範例會示範設定 **TcpClient** 連接至 TCP 通訊埠 13 上執行階段伺服器。  
  
```vb  
Imports System  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class TcpTimeClient  
    Private const portNum As Integer = 13  
    Private const hostName As String = "host.contoso.com"  
  
    ' Entry point  that delegates to C-style main Private Function.  
    Public Overloads Shared Sub Main()  
        System.Environment.ExitCode = _  
            Main(System.Environment.GetCommandLineArgs())  
    End Sub  
  
    Overloads Public Shared Function Main(args() As [String]) As Integer  
        Try  
            Dim client As New TcpClient(hostName, portNum)  
  
            Dim ns As NetworkStream = client.GetStream()  
  
            Dim bytes(1024) As Byte  
            Dim bytesRead As Integer = ns.Read(bytes, 0, bytes.Length)  
  
            Console.WriteLine(Encoding.ASCII.GetString(bytes, 0, bytesRead))  
  
        Catch e As Exception  
            Console.WriteLine(e.ToString())  
        End Try  
  
        client.Close()  
  
        Return 0  
    End Function 'Main  
End Class 'TcpTimeClient  
  
```  
  
```csharp  
using System;  
using System.Net.Sockets;  
using System.Text;  
  
public class TcpTimeClient {  
    private const int portNum = 13;  
    private const string hostName = "host.contoso.com";  
  
    public static int Main(String[] args) {  
        try {  
            TcpClient client = new TcpClient(hostName, portNum);  
  
            NetworkStream ns = client.GetStream();  
  
            byte[] bytes = new byte[1024];  
            int bytesRead = ns.Read(bytes, 0, bytes.Length);  
  
            Console.WriteLine(Encoding.ASCII.GetString(bytes,0,bytesRead));  
  
            client.Close();  
  
        } catch (Exception e) {  
            Console.WriteLine(e.ToString());  
        }  
  
        return 0;  
    }  
}  
```  
  
 <xref:System.Net.Sockets.TcpListener> 用於監視處理與用戶端的連線連入要求的 TCP 通訊埠會建立 **Socket** 或 **TcpClient** 。  <xref:System.Net.Sockets.TcpListener.Start%2A> 方法啟用接聽，因此， <xref:System.Net.Sockets.TcpListener.Stop%2A> 方法停用接聽 \(Listen\) 連接埠。  <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> 方法接受輸入的連接要求並建立 **TcpClient** 處理要求，因此， <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> 方法接受輸入的連接要求並建立 **Socket** 處理要求。  
  
 下列範例示範如何建立時間 Web 伺服器使用 **TcpListener** 監視 TCP 通訊埠 13。  當一連入連線要求被接受之後，時間伺服器回應與目前的日期和時間從主機伺服器。  
  
```vb  
Imports System  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class TcpTimeServer  
  
    Private const portNum As Integer = 13  
  
    ' Entry point that delegates to C-style main Private Function.  
    Public Overloads Shared Sub Main()  
        System.Environment.ExitCode = _  
            Main(System.Environment.GetCommandLineArgs())  
    End Sub  
  
    Overloads Public Shared Function Main(args() As [String]) As Integer  
        Dim done As Boolean = False  
  
        Dim listener As New TcpListener(portNum)  
  
        listener.Start()  
  
        While Not done  
            Console.Write("Waiting for connection...")  
            Dim client As TcpClient = listener.AcceptTcpClient()  
  
            Console.WriteLine("Connection accepted.")  
            Dim ns As NetworkStream = client.GetStream()  
  
            Dim byteTime As Byte() = _  
                Encoding.ASCII.GetBytes(DateTime.Now.ToString())  
  
            Try  
                ns.Write(byteTime, 0, byteTime.Length)  
                ns.Close()  
                client.Close()  
            Catch e As Exception  
                Console.WriteLine(e.ToString())  
            End Try  
        End While  
  
        listener.Stop()  
  
        Return 0  
    End Function 'Main  
End Class 'TcpTimeServer  
```  
  
```csharp  
using System;  
using System.Net.Sockets;  
using System.Text;  
  
public class TcpTimeServer {  
  
    private const int portNum = 13;  
  
    public static int Main(String[] args) {  
        bool done = false;  
  
        TcpListener listener = new TcpListener(portNum);  
  
        listener.Start();  
  
        while (!done) {  
            Console.Write("Waiting for connection...");  
            TcpClient client = listener.AcceptTcpClient();  
  
            Console.WriteLine("Connection accepted.");  
            NetworkStream ns = client.GetStream();  
  
            byte[] byteTime = Encoding.ASCII.GetBytes(DateTime.Now.ToString());  
  
            try {  
                ns.Write(byteTime, 0, byteTime.Length);  
                ns.Close();  
                client.Close();  
            } catch (Exception e) {  
                Console.WriteLine(e.ToString());  
            }  
        }  
  
        listener.Stop();  
  
        return 0;  
    }  
  
}  
```  
  
## 請參閱  
 [TCP\/UDP](../../../docs/framework/network-programming/tcp-udp.md)
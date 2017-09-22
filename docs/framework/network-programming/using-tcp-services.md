---
title: "使用 TCP 服務"
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
- requesting data from Internet, TCP
- receiving data, TCP
- TcpClient class, about TcpClient class
- data requests, TCP
- application protocols, TCP
- network resources, TCP
- sending data, TCP
- TCP
- protocols, TCP
- Internet, TCP
ms.assetid: d2811830-3bcb-495c-b82d-cda9cf919aad
caps.latest.revision: 11
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f462e99ecc78ddd6bcf3f231f712da8b04c71850
ms.contentlocale: zh-tw
ms.lasthandoff: 08/21/2017

---
# <a name="using-tcp-services"></a>使用 TCP 服務
<xref:System.Net.Sockets.TcpClient> 類別會使用 TCP 向網際網路資源要求資料。 **TcpClient** 的屬性和方法取出的詳細資料，可用來建立 <xref:System.Net.Sockets.Socket> 以使用 TCP 要求和接收資料。 因為遠端裝置的連線是以資料流表示，所以可以使用 .NET Framework 資料流處理技術來讀取和寫入資料。  
  
 TCP 通訊協定會建立與遠端端點的連線，然後使用該連接來傳送和接收資料封包。 TCP 負責確保將資料封包傳送到端點，並在送達時以正確的順序組合。  
  
 若要建立 TCP 傳線，您必須知道裝載所需服務之網路裝置的位址，以及服務用來通訊的 TCP 連接埠。 Internet Assigned Numbers Authority (Iana) 定義了通用服務的連接埠編號 (請參閱 www.iana.org/assignments/port-numbers)。 不在 Iana 清單上之服務的連接埠編號範圍可以是 1,024 到 65,535。  
  
 下列範例示範如何設定 **TcpClient**，以在 TCP 連接埠 13 上連線到時間伺服器。  
  
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
  
 <xref:System.Net.Sockets.TcpListener> 用來監視傳入要求的 TCP 連接埠，然後建立管理用戶端連線的 **Socket** 或 **TcpClient**。 <xref:System.Net.Sockets.TcpListener.Start%2A> 方法可啟用接聽，而 <xref:System.Net.Sockets.TcpListener.Stop%2A> 方法則可停用連接埠上的接聽。 <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> 方法會接受連入連線要求，並建立 **TcpClient** 來處理要求，而 <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> 方法會接受連入連線要求，並建立 **Socket** 來處理要求。  
  
 下列範例示範如何建立使用 **TcpListener** 來監視 TCP 連接埠 13 的網路時間伺服器。 接受連入連線要求時，時間伺服器會回應主機伺服器的目前日期和時間。  
  
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
  
## <a name="see-also"></a>另請參閱  
 


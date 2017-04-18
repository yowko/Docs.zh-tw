---
title: "使用 UDP 服務 | Microsoft Docs"
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
  - "通訊協定，UDP"
  - "網路資源，UDP"
  - "從網際網路要求資料，UDP"
  - "UDP"
  - "接收資料，UDP"
  - "網際網路，UDP"
  - "將訊息廣播至多個位址"
  - "資料要求，UDP"
  - "UdpClient 類別，關於 UdpClient 類別"
  - "傳送資料，UDP"
  - "應用程式通訊協定，UDP"
ms.assetid: d5c3477a-e798-454c-a890-738ba14c5707
caps.latest.revision: 15
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# 使用 UDP 服務
使用 UDP， <xref:System.Net.Sockets.UdpClient> 類別與 Web 服務進行通訊。  使用 UDP， <xref:System.Net.Sockets.UdpClient> 的屬性和方法的抽象類別建立要求和接收的資料 <xref:System.Net.Sockets.Socket> 詳細資料。  
  
 使用者資料包通訊協定 \(UDP\) \(UDP\) 是最佳的工作傳送資料至遠端主機的簡單通訊協定。  不過，在中，因為 UDP 通訊協定是無連接通訊協定，將 UDP 資料包傳送至遠端端點不保證到達，也不會保證到達其傳送的相同順序。  使用指定的應用程式必須準備處理遺漏、複製和不依順序的資料包。  
  
 使用 UDP，要傳送資料包，必須知道網路裝置的網址裝載您需要和 UDP 通訊埠編號服務使用通訊的服務進行。  Internet Assigned Numbers Authority \(Iana\) 定義通用服務的通訊埠編號 \(請參閱 www.iana.org\/assignments\/port\-numbers\) \(英文\)。  服務不在 Iana 清單上可以有介於 1,024 到 65,535 的通訊埠編號。  
  
 特殊的網路位址用來支援以 IP 網路的 UDP 廣播訊息。  下列討論透過網際網路 \(例如使用的 IP 第 4 版通訊協定家族 \(Family\)。  
  
 IP 第 4 版位址使用 32 位元指定網路位址。  對於類別使用 255.255.255.0 網路的 C 位址，將這些欄位分成四個\) 的八位元資料。  當以十進位表示，這四個八位元資料組形成熟悉的 IPv4 點分隔四組數字標記法，例如 192.168.100.2。  前兩個八進位 192.168 \(在此範例中為\) 以形成網路編號，第三個八位元資料組 \(100\) 定義子網路和 \(2\) 是主機識別項的最後一個八位元資料組。  
  
 設定 IP 位址的所有位元設定為一個、255.255.255.255，表單有限廣播位址。  將 UDP 資料包傳送至這個位址傳遞訊息給在區域網路區段中的任何主機。  由於路由器永遠不會將訊息傳送到該位址，在網路區段上只有主應用程式接收廣播訊息。  
  
 廣播可以導向至網路上的特定部分將主機識別項的所有欄位。  例如，傳送廣播至 IP 位址所識別的網路上的所有主機開始 192.168.1，請使用這個位址 192.168.1.255。  
  
 下列程式碼範例會使用 <xref:System.Net.Sockets.UdpClient> 接聽 UDP 資料包傳送至連接埠 11,000 的導向的廣播位址為 192.168.1.255。  用戶端接收訊息字串並將訊息寫入至主控台。  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class UDPListener  
   Private Const listenPort As Integer = 11000  
  
   Private Shared Sub StartListener()  
      Dim done As Boolean = False  
      Dim listener As New UdpClient(listenPort)  
      Dim groupEP As New IPEndPoint(IPAddress.Any, listenPort)  
      Try  
         While Not done  
            Console.WriteLine("Waiting for broadcast")  
            Dim bytes As Byte() = listener.Receive(groupEP)  
            Console.WriteLine("Received broadcast from {0} :", _  
                groupEP.ToString())   
            Console.WriteLine( _  
                Encoding.ASCII.GetString(bytes, 0, bytes.Length))  
            Console.WriteLine()  
         End While  
      Catch e As Exception  
         Console.WriteLine(e.ToString())  
      Finally  
         listener.Close()  
      End Try  
   End Sub 'StartListener  
  
   Public Shared Function Main() As Integer  
      StartListener()  
      Return 0  
   End Function 'Main  
End Class 'UDPListener  
```  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Sockets;  
using System.Text;  
  
public class UDPListener   
{  
    private const int listenPort = 11000;  
  
    private static void StartListener()   
    {  
        bool done = false;  
  
        UdpClient listener = new UdpClient(listenPort);  
        IPEndPoint groupEP = new IPEndPoint(IPAddress.Any,listenPort);  
  
        try   
        {  
            while (!done)   
            {  
                Console.WriteLine("Waiting for broadcast");  
                byte[] bytes = listener.Receive( ref groupEP);  
  
                Console.WriteLine("Received broadcast from {0} :\n {1}\n",  
                    groupEP.ToString(),  
                    Encoding.ASCII.GetString(bytes,0,bytes.Length));  
            }  
  
        }   
        catch (Exception e)   
        {  
            Console.WriteLine(e.ToString());  
        }  
        finally  
        {  
            listener.Close();  
        }  
    }  
  
    public static int Main()   
    {  
        StartListener();  
  
        return 0;  
    }  
}  
```  
  
 使用通訊埠 11,000，下列程式碼範例會使用 <xref:System.Net.Sockets.UdpClient> UDP 資料包傳送至導向的廣播位址為 192.168.1.255。  用戶端傳送在命令列上指定的訊息字串。  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class Program  
  
    Overloads Public Shared Function Main(args() As [String]) As Integer  
      Dim s As New Socket(AddressFamily.InterNetwork, SocketType.Dgram,  
          ProtocolType.Udp)  
      Dim broadcast As IPAddress = IPAddress.Parse("192.168.1.255")  
      Dim sendbuf As Byte() = Encoding.ASCII.GetBytes(args(0))  
      Dim ep As New IPEndPoint(broadcast, 11000)  
      s.SendTo(sendbuf, ep)  
      Console.WriteLine("Message sent to the broadcast address")  
   End Function 'Main  
End Class   
```  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Sockets;  
using System.Text;  
  
class Program   
{  
    static void Main(string[] args)   
    {  
        Socket s = new Socket(AddressFamily.InterNetwork, SocketType.Dgram,  
            ProtocolType.Udp);  
  
        IPAddress broadcast = IPAddress.Parse("192.168.1.255");  
  
        byte[] sendbuf = Encoding.ASCII.GetBytes(args[0]);  
        IPEndPoint ep = new IPEndPoint(broadcast, 11000);  
  
        s.SendTo(sendbuf, ep);  
  
        Console.WriteLine("Message sent to the broadcast address");  
    }  
}  
```  
  
## 請參閱  
 <xref:System.Net.Sockets.UdpClient>   
 <xref:System.Net.IPAddress>   
 [TCP\/UDP](../../../docs/framework/network-programming/tcp-udp.md)
---
title: "使用 UDP 服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- protocols, UDP
- network resources, UDP
- requesting data from Internet, UDP
- UDP
- receiving data, UDP
- Internet, UDP
- broadcasting messages to multiple addresses
- data requests, UDP
- UdpClient class, about UdpClient class
- sending data, UDP
- application protocols, UDP
ms.assetid: d5c3477a-e798-454c-a890-738ba14c5707
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c535710175423ebd0d163edc9bce78cfb2e18168
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="using-udp-services"></a>使用 UDP 服務
<xref:System.Net.Sockets.UdpClient> 類別使用 UDP 與網路服務通訊。 <xref:System.Net.Sockets.UdpClient> 類別屬性和方法使用 UDP 取出建立 <xref:System.Net.Sockets.Socket> 來要求和接收資料的詳細資料。  
  
 使用者資料包通訊協定 (UDP) 是一種簡單的通訊協定，致力於將資料傳遞到遠端主機。 不過，因為 UDP 通訊協定是一種無連線的通訊協定，所以傳送到遠端端點的 UDP 資料包不保證會送達，也不保證會以傳送的相同順序送達。 使用 UDP 應用程式必須準備好處理遺失、重複和不依順序的資料包。  
  
 若要使用 UDP 傳送資料包，您必須知道裝載所需服務的網路裝置的網路位址，以及服務用來通訊的 UDP 連接埠編號。 Internet Assigned Numbers Authority (Iana) 定義了通用服務的連接埠編號 (請參閱 www.iana.org/assignments/port-numbers)。 不在 Iana 清單上的服務的連接埠編號範圍可以是 1,024 到 65,535。  
  
 特殊的網路位址可用來支援 IP 型網路上的 UDP 廣播訊息。 下列討論內容會以網際網路上使用的 IP 第 4 版位址系列作為範例。  
  
 IP 第 4 版位址會使用 32 位元來指定網路位址。 對於使用網路遮罩 255.255.255.0 的類別 C 位址，這些位元會分成四個八位元。 以十進位表示時，四個八位元會形成熟悉的四點區隔標記法，例如 192.168.100.2。 前兩個八位元 (在此範例中為 192.168) 形成網路編號，第三個八位元 (100) 定義子網路，而最後一個八位元 (2) 主機識別碼。  
  
 將 IP 位址的所有位元設定為其中一個或 255.255.255.255，構成受限的廣播位址。 將 UDP 資料包傳送到這個位址時，會將訊息傳遞到本機網路區段上的任何主機。 因為路由器永遠不會轉送傳送到這個位址的訊息，所以只有網路區段上的主機會收到廣播訊息。  
  
 藉由設定主機識別碼的所有位元，即可將廣播導向至網路的特定部分。 例如，若要將廣播傳送至開頭為 192.168.1 之 IP 位址所識別網路上的所有主機，請使用位址 192.168.1.255。  
  
 下列程式碼範例使用 <xref:System.Net.Sockets.UdpClient>，在連接埠 11,000 上接聽傳送到導向廣播位址 192.168.1.255 的 UDP 資料包。 用戶端會接收訊息字串，並將訊息寫入至主控台。  
  
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
  
 下列程式碼範例使用 <xref:System.Net.Sockets.UdpClient>透過連接埠 11,000 將 UDP 資料包傳送到導向廣播位址 192.168.1.255。 用戶端會傳送命令列上指定的訊息字串。  
  
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
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Net.Sockets.UdpClient>  
 <xref:System.Net.IPAddress>  
 

---
title: 如何：取得介面和通訊協定資訊
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: fd88d26c-4063-495e-a253-736ac3e6b23f
author: mcleblanc
ms.author: markl
ms.openlocfilehash: ae4eb38c72a7f7629cea0f8137a4337553457808
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47200902"
---
# <a name="how-to-get-interface-and-protocol-information"></a><span data-ttu-id="b2ac2-102">如何：取得介面和通訊協定資訊</span><span class="sxs-lookup"><span data-stu-id="b2ac2-102">How to: Get Interface and Protocol Information</span></span>
<span data-ttu-id="b2ac2-103">這個範例示範如何讀取網路介面的 TCP 統計資料。</span><span class="sxs-lookup"><span data-stu-id="b2ac2-103">This sample shows how to read the TCP statistics of a network interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2ac2-104">範例</span><span class="sxs-lookup"><span data-stu-id="b2ac2-104">Example</span></span>  
  
```  
public static void ShowTcpStatistics(NetworkInterfaceComponent version)  
{  
    IPGlobalProperties properties =  
          IPGlobalProperties.GetIPGlobalProperties();  
    TcpStatistics tcpstat = null;  
    Console.WriteLine("");  
    switch (version)  
    {  
        case NetworkInterfaceComponent.IPv4:  
             tcpstat = properties.GetTcpIPv4Statistics();  
            Console.WriteLine("TCP/IPv4 Statistics:");  
            break;  
        case NetworkInterfaceComponent.IPv6:  
            tcpstat = properties.GetTcpIPv6Statistics();  
            Console.WriteLine("TCP/IPv6 Statistics:");  
            break;  
        default:  
            throw new ArgumentException("version");  
            break;  
    }  
    Console.WriteLine("  Minimum Transmission Timeout. : {0}",   
        tcpstat.MinimumTransmissionTimeout);  
    Console.WriteLine("  Maximum Transmission Timeout. : {0}",   
        tcpstat.MaximumTransmissionTimeout);  
  
    Console.WriteLine("  Connection Data:");  
    Console.WriteLine("      Current : {0}",   
    tcpstat.CurrentConnections);  
    Console.WriteLine("      Cumulative : {0}",   
        tcpstat.CumulativeConnections);  
    Console.WriteLine("      Initiated  : {0}",   
        tcpstat.ConnectionsInitiated);  
    Console.WriteLine("      Accepted : {0}",   
        tcpstat.ConnectionsAccepted);  
    Console.WriteLine("      Failed Attempts : {0}",   
        tcpstat.FailedConnectionAttempts);  
    Console.WriteLine("      Reset : {0}",   
        tcpstat.ResetConnections);  
  
    Console.WriteLine("");  
    Console.WriteLine("  Segment Data:");  
    Console.WriteLine("      Received  ................... : {0}",   
        tcpstat.SegmentsReceived);  
    Console.WriteLine("      Sent : {0}",   
        tcpstat.SegmentsSent);  
    Console.WriteLine("      Retransmitted : {0}",   
        tcpstat.SegmentsResent);  
  
    Console.WriteLine("");  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b2ac2-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b2ac2-105">Compiling the Code</span></span>  
 <span data-ttu-id="b2ac2-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="b2ac2-106">This example requires:</span></span>  
  
-   <span data-ttu-id="b2ac2-107">對 **System.Net** 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="b2ac2-107">References to the **System.Net** namespace.</span></span>

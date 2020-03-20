---
title: 如何：偵測網路可用性和位址變更
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: d4377115-4a76-4848-ab23-4898d65c771c
ms.openlocfilehash: 9e265a97d339da59bb9d0af6ab6757e16af00e06
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "70894956"
---
# <a name="how-to-detect-network-availability-and-address-changes"></a><span data-ttu-id="0b7be-102">如何：偵測網路可用性和位址變更</span><span class="sxs-lookup"><span data-stu-id="0b7be-102">How to: Detect Network Availability and Address Changes</span></span>
<span data-ttu-id="0b7be-103">這個範例示範如何偵測介面的網路位址變更。</span><span class="sxs-lookup"><span data-stu-id="0b7be-103">This sample shows how to detect changes in the network address of an interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b7be-104">範例</span><span class="sxs-lookup"><span data-stu-id="0b7be-104">Example</span></span>  
  
```csharp
using System;  
using System.Net;  
using System.Net.NetworkInformation;  
  
namespace Examples.Net.AddressChanges  
{  
    public class NetworkingExample  
    {  
        public static void Main()  
        {  
            NetworkChange.NetworkAddressChanged += new
             NetworkAddressChangedEventHandler(AddressChangedCallback);  
            Console.WriteLine("Listening for address changes. Press any key to exit.");  
            Console.ReadLine();  
        }  
        static void AddressChangedCallback(object sender, EventArgs e)  
        {  
  
            NetworkInterface[] adapters = NetworkInterface.GetAllNetworkInterfaces();  
            foreach(NetworkInterface n in adapters)  
            {  
                Console.WriteLine("   {0} is {1}", n.Name, n.OperationalStatus);  
            }  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0b7be-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="0b7be-105">Compiling the Code</span></span>  
 <span data-ttu-id="0b7be-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="0b7be-106">This example requires:</span></span>  
  
- <span data-ttu-id="0b7be-107">對 **System.Net** 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="0b7be-107">References to the **System.Net** namespace.</span></span>

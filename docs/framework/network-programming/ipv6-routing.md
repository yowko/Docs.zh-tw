---
title: "IPv6 路由"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
caps.latest.revision: "4"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: c7bfb79c5ab5406793a27f653b7e6a1abf2b2859
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ipv6-routing"></a>IPv6 路由
IPv6 的優點是彈性的路由機制。 因為 IPv4 網路識別碼過去和現在的配置方式，大型的路由表需要由位於網際網路骨幹的路由器維護。 這些路由器必須知道所有路由，才能轉送在網際網路上可能導向至任何節點的封包。 因為其能彙總位址，IPv6 可讓您彈性定址，並大幅降低路由表大小。 在這個新的定址架構中，中繼路由器必須只持續追蹤其網路的本機部分，才能正確地轉寄訊息。  
  
## <a name="neighbor-discovery"></a>鄰居搜索  
 鄰居探索提供的部分功能包括：  
  
-   路由器探索。 這可讓主機識別本機路由器。  
  
-   位址解析。 這可讓節點解析連結層位址，以對應下個躍點位址 (位址解析通訊協定 [ARP] 的取代項目)。  
  
-   處理自動組態。 這可讓主機自動設定網站-本機和全域位址。  
  
 鄰居探索使用 IPv6 的網際網路控制訊息通訊協定 (ICMPv6) 訊息，包括：  
  
-   路由器通告。 由路由器依虛擬週期傳送，或回應路由器請求。 IPv6 路由器使用路由器通告公告其可用性、位址前置詞和其他參數。  
  
-   路由器請求。 由主機傳送，以要求連結上的路由器立即傳送路由器通告。  
  
-   芳鄰請求。 由節點傳送，以處理位址解析、重複位址偵測，或驗證是否仍然可以連線到芳鄰。  
  
-   芳鄰通告。 由節點傳送以回應請求，或通知芳鄰連結層位址中的變更。  
  
-   重新導向。 由路由器傳送，以指出傳送節點之特定目的地的下一個較佳躍點位址。  
  
## <a name="see-also"></a>請參閱  
 [網際網路通訊協定第 6 版](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [通訊端](../../../docs/framework/network-programming/sockets.md)

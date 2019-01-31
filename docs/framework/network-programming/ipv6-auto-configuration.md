---
title: IPv6 自動設定
ms.date: 03/30/2017
ms.assetid: 581c1d21-1013-43a3-bf3e-2d9ead62b79c
ms.openlocfilehash: 2184b02f6f4c8ba4e8a79279f212ffca2cb41959
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726347"
---
# <a name="ipv6-auto-configuration"></a>IPv6 自動設定
IPv6 的一個重要目標是支援節點隨插即用。 亦即，節點應該可能插入 IPv6 網路，並且可以自動設定，不需要人為介入。  
  
## <a name="type-of-auto-configuration"></a>自動組態的類型  
 IPv6 支援下列類型的自動組態：  
  
-   **具狀態的自動組態**。 這種組態需要某種程度的人為介入，因為它需要 IPv6 的動態主機設定通訊協定 (DHCPv6) 伺服器來安裝與管理節點。 DHCPv6 伺服器會保留一份要提供組態資訊的節點。 它也會維護狀態資訊，讓伺服器知道每個位址使用多長時間，以及何時可供重新指派。  
  
-   **無狀態的自動組態**。 這種組態適合小型組織和個人。 在此情況下，每部主機都會從接收到的路由器通告內容中判斷其位址。 使用 IEEE EUI-64 標準定義位址的網路識別碼部分，就可合理假設主機位址在連結上的唯一性。  
  
 無論以何方式判斷位址，節點都必須確認其潛在位址對本機連結而言是唯一的。 這是透過將芳鄰請求訊息傳送給潛在位址所完成。 如果節點收到任何回應，它會知道位址已在使用中，必須判斷另一個位址。  
  
## <a name="ipv6-mobility"></a>IPv6 行動性  
 行動裝置的大量增加帶來了新的需求：裝置必須能夠在 IPv6 網際網路上任意變更位置，同時仍保有現有的連線。 為提供這項功能，要指派給行動節點一個隨時可以連線的主目錄位址。 當行動節點在主目錄時，它會連接到主目錄連結，並使用主目錄位址。 當行動節點離開主目錄時，主目錄代理程式 (通常是路由器)，會在行動節點和它通訊的節點之間轉送訊息。  
  
## <a name="see-also"></a>另請參閱
- [網際網路通訊協定第 6 版](../../../docs/framework/network-programming/internet-protocol-version-6.md)
- [通訊端](../../../docs/framework/network-programming/sockets.md)

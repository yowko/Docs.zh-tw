---
title: IPv6 定址
ms.date: 03/30/2017
helpviewer_keywords:
- Internet Protocol version 6, addresses in
- Neighbor Discovery
- IPv6, enabling
- IPv6, mobility and
- Internet Protocol version 6, anycast addresses
- IPv6, Neighbor Discovery
- Internet Protocol version 6, auto-configuring
- Internet Protocol version 6, enabling
- IPv6, unicast addresses
- IPv6, auto-configuring
- Internet Protocol version 6, routing
- IPv6, RFC documents
- IPv6, routing
- Internet Protocol version 6, disabling
- Internet Protocol version 6, unicast addresses
- IPv6, multicast addresses
- Internet Protocol version 6, mobility and
- Internet Protocol version 6, RFC documents
- Internet Protocol version 6, Neighbor Discovery
- IPv6, anycast addresses
- Internet Protocol version 6, multicast addresses
- IPv6, addresses in
- IPv6, disabling
ms.assetid: 20a104ae-1649-4649-a005-531a5cf74c93
ms.openlocfilehash: ac8b8bae69ba20f34bb74fbff533ba53f915a150
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50183408"
---
# <a name="ipv6-addressing"></a>IPv6 定址
網際網路通訊協定第 6 版 (IPv6) 的位址長度為 128 個位元長。 使用這類大型位址空間的其中一個原因是，將可用的位址細分到路由網域的階層，反映網際網路的拓撲。 另一個原因是，將連線裝置之網路網路介面卡 (或介面) 的位址對應至網路。 IPv6 特有的固有功能，是在其最低層級解析位址，即網路介面層級，且也擁有自動組態功能。  
  
## <a name="text-representation"></a>文字表示法  
 下列是三種使用文字字串表示 IPv6 位址的慣例格式：  
  
-   **冒號:十六進位格式**。 這是慣用的格式 n:n:n:n:n:n:n:n。 每個 n 代表位址的八個 16 位元項目的一個十六進位值。 例如：`3FFE:FFFF:7654:FEDA:1245:BA98:3210:4562`。  
  
-   **壓縮格式**。 因為位址長度的原因，位址通常會包含由零組成的長字串。 若要簡化撰寫這些地址，請使用壓縮格式，其中單一連續序列的 0 區塊會以雙冒號符號 (::) 表示。 這個符號在位址中只會出現一次。 例如，多點傳送位址 `FFED:0:0:0:0:BA98:3210:4562` 的壓縮格式是 `FFED::BA98:3210:4562`。 單點傳播位址 `3FFE:FFFF:0:0:8:800:20C4:0` 的壓縮格式是 `3FFE:FFFF::8:800:20C4:0`。 回送位址 `0:0:0:0:0:0:0:1` 的壓縮格式是 `::`1。 未指定的位址 `0:0:0:0:0:0:0:0` 的壓縮格式是 `::`。  
  
-   **混合格式**。 這種格式結合了 IPv4 和 IPv6 位址。 在此情況下，位址格式是 n:n:n:n:n:n:d.d.d.d，每個 n 代表六個 IPv6 高序位 16 位元位址項目的十六進位值，每個 d 代表 IPv4 位址的十進位值。  
  
## <a name="address-types"></a>位址類型  
 位址中的前置位元會定義特定的 IPv6 位址類型。 包含這些前置位元的變數長度欄位稱為格式首碼 (FP)。  
  
 IPv6 單點傳播位址分為兩個部分。 第一個部分包含位址前置詞，第二個部分包含介面識別碼。 表示 IPv6 位址/前置詞組合的簡潔方式如下：ipv6 位址/前置詞長度。  
  
 下例是具有 64 位元前置詞的位址。  
  
 `3FFE:FFFF:0:CD30:0:0:0:0/64`.  
  
 本例中的前置詞為 `3FFE:FFFF:0:CD30`。 位址也可以壓縮格式寫入，如 `3FFE:FFFF:0:CD30::/64`。  
  
 IPv6 會定義下列位址類型：  
  
-   **單點傳播位址**。 單一介面的識別碼。 傳送到此位址的封包會被傳遞到已識別的介面。 單點傳播位址是高序位八位元值從多點傳送位址中區隔出來的。 多點傳送位址之高序位八位元的十六進位值為 FF。 此八位元的任何其他值會識別單點傳播位址。 以下是不同類型的單點傳播位址：  
  
    -   **連結-本機位址**。 這些位址是用在單一連結，且具有下列格式：FE80::*InterfaceID*。 連結上的節點之間在處理自動位址組態、鄰居探索，或沒有路由器時，會使用連結-本機位址。 連結-本機位址主要是用在啟動時，以及系統尚未取得較大範圍的位址時。  
  
    -   **網站-本機位址**。 這些位址是用在單一網站，且具有下列格式：FEC0::*SubnetID*:*InterfaceID*。 網站-本機位址可用來在網站中定址，不需要全域前置詞。  
  
    -   **全域 IPv6 單點傳播位址**。 這些位址可以用在整個網際網路上，而且具有下列格式：010(FP，3 位元) TLA ID (13 位元) 保留項目 (8 位元) NLA ID (24 位元) SLA ID (16 位元) *InterfaceID* (64 位元)。  
  
-   **多點傳送位址**。 一組介面 (通常屬於不同的節點) 的識別碼。 傳送到此位址的封包會被傳遞到該位址所識別的所有介面。 多點傳送位址類型取代 IPv4 廣播位址。  
  
-   **任一傳播位址**。 一組介面 (通常屬於不同的節點) 的識別碼。 傳送到此位址的封包只會被傳遞該位址所識別的一個介面。 這是路由計量所識別的最近介面。 任一傳播位址皆是取自單點傳播位址空間，而且語法上沒有分別。 位址介面會將單點傳播與任一傳播位址之間的差異當成其組態的函式執行。  
  
 一般情況下，節點一律會有連結-本機位址。 它可能有網站-本機位址和一或多個全域位址。  
  
## <a name="see-also"></a>請參閱  
 [網際網路通訊協定第 6 版](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [通訊端](../../../docs/framework/network-programming/sockets.md)

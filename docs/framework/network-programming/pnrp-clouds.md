---
title: PNRP 雲端
ms.date: 03/30/2017
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
ms.openlocfilehash: 22401459a183d8d21e37211d942b24dbc76a6f94
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195355"
---
# <a name="pnrp-clouds"></a>PNRP 雲端
PNRP「雲端」代表一組節點，可以透過網路彼此進行通訊。 「雲端」這個詞相當於「對等網格」和「點對點圖形」。  
  
 節點之間的通訊絕對不應該跨越不同的雲端。 <xref:System.Net.PeerToPeer.Cloud> 執行個體可透過其區分大小寫的名稱唯一進行識別。 單一對等或節點可能已連線至多個雲端。  
  
 雲端極為緊密地繫結至網路介面。  在有兩張網路卡連結至不同子網路的多重主目錄電腦上，將會傳回三個雲端：一個介面的一個連結本機位址有一個，以及單一全域範圍雲端。  
  
 PNRP 會使用三個雲端「範圍」，而範圍是一組可找到彼此的電腦：  
  
-   全域雲端對應至全域 IPv6 位址範圍和全域位址，並代表整個 IPv6 網際網路上的所有電腦。 單一全域雲端只有一個。  
  
-   連結-本機雲端對應至連結-本機 IPv6 位址範圍與連結-本機位址。 連結-本機雲端用於特定連結，而且通常與本機連接的子網路相同。 可以有多個連結-本機雲端。  
  
 第三個雲端是網站特定雲端，並對應至網站 IPv6 位址範圍和網站-本機位址。 此雲端已過時，不過 PNRP 中仍然支援此雲端。  
  
## <a name="clouds"></a>雲端  
 PNRP 雲端是由 <xref:System.Net.PeerToPeer.Cloud> 類別的執行個體所表示。 使用對等的雲端群組是由可列舉 <xref:System.Net.PeerToPeer.CloudCollection> 類別的執行個體所表示。 呼叫靜態 <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> 方法，即可取得目前對等已知的 PNRP 雲端集合。  
  
 個別雲端具有唯一名稱，並以 256 個字元的 Unicode 字串呈現。 這些名稱以及上述範圍是用來建構 Cloud 類別的唯一執行個體。 這些執行個體可以序列化並重新建構以供持續使用。  
  
 建立或取得雲端執行個體之後，可以向它註冊對等名稱，以建立已知對等的網格。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Net.PeerToPeer.Cloud>  
 [對等名稱解析通訊協定](../../../docs/framework/network-programming/peer-name-resolution-protocol.md)

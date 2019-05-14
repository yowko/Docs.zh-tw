---
title: 對等名稱發佈和解析
ms.date: 03/30/2017
ms.assetid: f0370e08-9fa6-4ee5-ab78-9a58a20a7da2
ms.openlocfilehash: 4a0787972a61f5700d1e8728be96db8ef9ee749e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623193"
---
# <a name="peer-name-publication-and-resolution"></a>對等名稱發佈和解析

## <a name="publishing-a-peer-name"></a>發行對等名稱  

 為了發行新的 PNRP 識別碼，對等會執行下列動作：  
  
- 將 PNRP 發行訊息傳送至相鄰的快取 (在快取的最下層中註冊 PNRP 識別碼的對等)，讓其快取成為種子。  
  
- 在雲端中隨機選擇非相鄰的節點，並將其專屬 P2P 識別碼的 PNRP 名稱解析要求傳送至這些節點。 產生的端點判斷處理序會以發行對等的 PNRP 識別碼，作為雲端中隨機節點的快取種子。  
  
如果 PNRP 第 2 版僅解析其他 P2P 識別碼，則其節點不會發行 PNRP 識別碼。 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\PeerNet\PNRP\IPV6-Global\SearchOnly=1 登錄值 (REG_DWORD 類型) 指定對等節點只能使用 PNRP 進行名稱解析，而不進行名稱發行。 此登錄值也可以透過群組原則進行設定。  
  
## <a name="resolving-a-peer-name"></a>解析對等名稱

 在 PNRP 網路或雲端中尋找其他對等，是包含兩個階段的處理序：  
  
1. 端點判斷  
  
2. PNRP 識別碼解析  
  
 在端點判斷階段中，嘗試解析另一部電腦上服務之 PNRP 識別碼的對等會判斷該遠端對等的 IPv6 位址。  遠端對等是發行電腦或服務之 PNRP 識別碼的對等，或與之建立關聯的對等。  
  
 確認已將遠端端點註冊至 PNRP 雲端之後，PNRP 識別碼解析階段中發出要求的對等會將要求傳送至所需服務之 PNRP 識別碼的那個對等端點。 端點會傳送回覆，確認服務的 PNRP 識別碼、註解，以及最多 4 KB 的額外資訊，以供發出要求的對等未來進行通訊時使用。 例如，如果所需的端點是遊戲伺服器，則額外的對等名稱記錄資料可能會包含遊戲、參與遊戲等級和目前玩家人數的相關資訊。  
  
 在端點判斷階段中，PNRP 會使用互動的處理序尋找發佈 PNRP 識別碼的節點，其中執行解析的節點會負責連絡接近目標 PNRP 識別碼的後續節點。  
  
 為了在 PNRP 中執行名稱解析，對等節點會檢查本身的快取項目中是否有符合目標 PNRP 識別碼的項目。 如果找到相符項目，對等會將 PNRP 要求訊息傳送至對等，並等候回應。 如果找不到 PNRP 識別碼的項目，則對等會將 PNRP 要求訊息傳送至對應到最接近目標 PNRP 識別碼之 PNRP 識別碼的對等。 收到 PNRP 要求訊息的節點會檢查自己的快取，並執行下列動作：  
  
- 如果找到 PNRP 識別碼，則收到要求的對等會直接回覆發出要求的對等。  
  
- 如果找不到 PNRP 識別碼，而快取中有接近目標 PNRP 識別碼的 PNRP 識別碼，則收到要求的對等會將回應傳送至發出要求的對等，其中包含代表擁有較接近目標 PNRP 識別碼之 PNRP 識別碼的對等 IPv6 位址。 使用回應中的 IP 位址時，發出要求的節點會將另一個 PNRP 要求訊息傳送至 IPv6 位址來進行回應，或檢查其快取。  
  
- 如果找不到 PNRP 識別碼，而且快取中沒有接近目標 PNRP 識別碼的 PNRP 識別碼，則收到要求的對等會將指出此情況的回應傳送給發出要求的對等。 發出要求的對等接著會選擇下一個最接近的 PNRP 識別碼。  
  
發出要求的對等會繼續重複執行此處理序，直到最後找到登錄 PNRP 識別碼的節點。  
  
 在 <xref:System.Net.PeerToPeer> 命名空間內，包含端點以及在其中進行通訊之 PNRP 雲端或網格的 <xref:System.Net.PeerToPeer.PeerName> 記錄間有多對多關聯性。 如果有重複或過時項目，或多個具有相同對等名稱的節點，則 PNRP 節點可以使用 <xref:System.Net.PeerToPeer.PeerNameResolver> 類別來取得目前資訊。 <xref:System.Net.PeerToPeer.PeerNameResolver> 方法使用單一對等名稱，來簡化一個對等到多個對等名稱記錄以及相同的一個對等到許多雲端的觀點。 這類似於使用關聯式資料表聯結所執行的查詢。 成功完成時，解析程式物件會傳回所指定對等名稱的 <xref:System.Net.PeerToPeer.PeerNameRecordCollection>。  例如，對等名稱發生在集合的所有對等名稱記錄中，並依雲端進行排序。 這些是對等名稱的執行個體，而 PNRP 應用程式可以要求其支援資料。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Net.PeerToPeer>

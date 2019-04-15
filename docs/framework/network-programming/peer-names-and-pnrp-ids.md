---
title: 對等名稱和 PNRP 識別碼
ms.date: 03/30/2017
ms.assetid: afa538e8-948f-4a98-aa9f-305134004115
ms.openlocfilehash: e7e92519bede478a5e26a88a56236f987c93c441
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173104"
---
# <a name="peer-names-and-pnrp-ids"></a>對等名稱和 PNRP 識別碼
對等名稱代表通訊端點，可以是一部電腦、一位使用者、一個群組、一項服務，或是與可解析成 IPv6 位址之對等建立關聯的任何項目。 對等名稱解析通訊協定 (PNRP) 採用靜態上唯一的對等名稱來建立 PNRP 識別碼，以用來識別雲端成員。  
  
## <a name="peer-names"></a>對等名稱  
 對等名稱可以註冊為不安全或安全的名稱。 不安全的名稱是指單純為文字字串的名稱，容易受到詐騙，因為任何人都可以註冊重複的不安全名稱。 不安全的名稱最好用於私人或是受保護的網路中。 安全的名稱是使用憑證和數位簽章進行保護。 只有原始發行者才能證明安全名稱的擁有權。  
  
 雲端與範圍的組合提供參與 PNRP 活動的對等相當安全的環境。 不過，使用安全的對等名稱不保證網路應用程式的整體安全性。 應用程式的安全性是與實作相依。  
  
 安全的對等名稱只能由其擁有者註冊，並以公開金鑰加密進行保護。 安全的對等名稱是為由具有對應私密金鑰的對等實體所擁有。 擁有權可以透過使用私密金鑰簽署的認證對等位址 (CPA) 進行證明。 惡意使用者沒有對應的私密金鑰，就無法偽造對等名稱的擁有權。  
  
## <a name="pnrp-ids"></a>PNRP 識別碼  
 ![PNRP 識別碼](../../../docs/framework/network-programming/media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.gif "fdc9e8a0-4a1c-488d-a019-bc3a1973220c")  
  
 PNRP 識別碼由下列各項所組成：  
  
-   高序位 128 位元 (稱為對等 (P2P) 識別碼) 是指派給端點的對等名稱雜湊。 對等名稱的格式如下：*Authority.Classifier*。 安全名稱的 *Authority* 是以十六進位字元表示，是對等名稱公開金鑰的安全雜湊演算法 1 (SHA1) 雜湊。 不安全名稱的 *Authority* 則為單一字元 "0"。 *Classifier* 是識別應用程式的字串。 對等名稱分類器的長度不能超過 149 個字元 (包含 `null` 結束字元)。  
  
-   低序位 128 位元用於表示服務位置所產生的數字，用來識別相同雲端中同一個 P2P 識別碼的不同執行個體。  
  
 這個 P2P 識別碼與服務位置的組合可讓單一電腦登錄多個 PNRP 識別碼。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Net.PeerToPeer.PeerName>
- <xref:System.Net.PeerToPeer>

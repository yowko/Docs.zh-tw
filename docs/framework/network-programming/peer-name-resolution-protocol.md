---
title: 對等名稱解析通訊協定
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
author: mcleblanc
ms.author: markl
ms.openlocfilehash: f17c5e7e2fa7a5eba66f0b9dd8c950a7464eea8e
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196744"
---
# <a name="peer-name-resolution-protocol"></a>對等名稱解析通訊協定
在對等環境中，對等使用特定名稱解析系統，才能從名稱或其他類型的識別碼解析彼此的網路位置 (位址、通訊協定和連接埠)。 過去，網域名稱系統 (DNS) 內本來就是暫時性連線以及其他缺點，而讓對等名稱解析變得複雜。  
  
 Microsoft® Windows® 對等網路平台會利用對等名稱解析通訊協定 (PNRP) 解決此問題，此通訊協定最先是針對 Windows XP 所開發，之後於 Windows Vista™ 中升級，是一項安全、可調整的動態名稱登錄與名稱解析通訊協定。 PNRP 的運作方式與傳統的名稱解析系統十分不同，為應用程式開發人員開拓令人雀躍的嶄新視野。  
  
 使用 PNRP，可以將對等名稱套用至電腦，或是電腦上的個別應用程式或服務。 對等名稱解析包含位址、連接埠，以及可能的延伸承載。 此系統的優點包含容錯、無瓶頸，以及絕不會傳回過時位址的名稱解析；這樣讓通訊協定成為尋找行動使用者的最佳解決方案。  
  
 就安全性而言，可以將對等名稱發行為安全的 (受保護) 或不安全的 (未受保護)。 PNRP 使用公開金鑰加密來保護安全對等名稱防止詐騙；您可以使用 PNRP 來命名電腦和服務。  
  
-   對等名稱解析通訊協定會示範下列屬性：  
  
-   分散式且幾乎完全無伺服器。 只有啟動程序處理序才需要伺服器。  
  
-   沒有第三方的安全名稱發行。 與 DNS 名稱發行不同，PNRP 名稱發行是瞬間發生的，沒有財務成本。  
  
-   PNRP 會即時更新，以防止解析過時位址。  
  
-   透過 PNRP 的名稱解析同時允許服務的名稱解析，以擴充到不只限於電腦。  
  
-  
  
## <a name="the-systemnetpeertopeer-namespace"></a>System.Net.PeerToPeer 命名空間  
  
-   PNRP 功能是由 .NET Framework 3.5 版內的 <xref:System.Net.PeerToPeer> 命名空間所定義。 它提供的一組類型可用來向可用的 PNRP 服務註冊和解析對等名稱。  
  
-  
  
-   (PNRP 和自訂對等解析程式可以使用 <xref:System.ServiceModel.PeerResolvers> 命名空間中所提供的類型進行建立和具現化)。  
  
-  
  
-   用來向可用 PNRP 服務註冊和解析名稱的基本類型如下：  
  
-  
  
-   <xref:System.Net.PeerToPeer.Cloud>：定義描述可用 PNRP 雲端的資訊，包含其範圍。  
  
-   <xref:System.Net.PeerToPeer.PeerName>：定義可用來註冊並後續解析雲端內對等的對等名稱。  
  
-   <xref:System.Net.PeerToPeer.PeerNameRecord>：定義 PNRP 雲端中包含對等註冊資訊的記錄，而對等包含可連絡對等的網路端點。  
  
-   <xref:System.Net.PeerToPeer.PeerNameRegistration>：定義對等名稱的註冊處理序，包含啟動和停止對等名稱註冊的方法。  
  
-   <xref:System.Net.PeerToPeer.PeerNameResolver>：定義將對等名稱解析成其網路端點的處理序，同時包含解析的同步和非同步方法。  
  
-  
  
-  
  
## <a name="see-also"></a>請參閱  
 <xref:System.ServiceModel.PeerResolvers>  
 <xref:System.Net.PeerToPeer>  
 [網路程式設計範例](../../../docs/framework/network-programming/network-programming-samples.md)  
 [PeerToPeer 技術範例](https://go.microsoft.com/fwlink/?LinkID=179571)

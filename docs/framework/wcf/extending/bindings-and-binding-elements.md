---
title: 繫結和繫結項目
ms.date: 03/30/2017
helpviewer_keywords:
- binding elements [WCF]
ms.assetid: 765ff77b-7682-4ea3-90eb-e4d751e37379
ms.openlocfilehash: d4d69495c1ae19b6799fdb9981f6b332cc2580d3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795846"
---
# <a name="bindings-and-binding-elements"></a>繫結和繫結項目
系結是特殊設定專案的集合，稱為*綁定*項，會在每次建立用戶端或服務端點時由服務執行時間評估。 繫結項目在繫結內的型別與順序會決定端點通道堆疊中通訊協定與傳輸通道的選擇與堆疊順序。  
  
 繫結 (尤其是系統提供的繫結) 通常都會同時具備許多組態屬性，這些屬性會反映最常修改的封裝繫結項目屬性。  
  
 一個繫結必須剛好包含一個傳輸繫結項目。 每個傳輸繫結項目都意指預設的訊息編碼繫結項目，此項目可透過將最多一個訊息編碼繫結項目新增至繫結的方式來加以覆寫。 除了傳輸與編碼器繫結項目之外，繫結還可包含任何數量的通訊協定繫結項目，這些項目可一併實作服務所需的功能，並在各個端點之間傳送 SOAP 訊息。 如需詳細資訊，請參閱使用系結[來設定服務和用戶端](../using-bindings-to-configure-services-and-clients.md)。  
  
## <a name="extending-bindings-and-binding-elements"></a>延伸繫結與繫結項目  
 Windows Communication Foundation （WCF）包含系統提供的系結，涵蓋各種不同的案例。 （如需詳細資訊，請參閱[系統提供的](../system-provided-bindings.md)系結。）不過，有時候您需要建立並使用未包含在 WCF 中的系結。 下列案例需要建立新的繫結。  
  
- 若要使用新的繫結項目 (例如新的傳輸、編碼或通訊協定繫結項目)，您必須建立包含該繫結項目的新繫結。 例如，如果您為 UDP 傳輸新增自訂的 `UdpTransportBindingElement`，則需要建立新繫結才能使用它。 如需使用<xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>類型執行此行為的詳細資訊，請參閱[自訂](custom-bindings.md)系結。  
  
- 若要設定現有繫結項目，讓系統提供的繫結在公用的屬性上不公開。 例如，您必須建立新的繫結來變更簽署與加密作業的執行順序。 如需有關執行此行為的詳細[資訊，請參閱如何：自訂系統提供](how-to-customize-a-system-provided-binding.md)的系結。  
  
- 若要建立僅公開特定組態選項的企業標準繫結。 例如，要為公司建立 <xref:System.ServiceModel.WSHttpBinding> 變數，其中不得停用安全性，請建立具有類似 <xref:System.ServiceModel.WSHttpBinding> 行為的新繫結，但是一律啟用安全性。 如需詳細資訊，請參閱[建立使用者定義的](creating-user-defined-bindings.md)系結。  
  
- 若要執行中繼資料的某項自訂作業，通常 (不是一定) 會設定或使用某個自訂繫結項目。 如需為系結和繫結項目提供中繼資料支援的詳細資訊，請參閱設定[和中繼資料支援](configuration-and-metadata-support.md)。  

## <a name="channels-bindings-and-binding-elements"></a>通道、繫結與繫結項目  
 繫結與繫結項目都可用來連接應用程式的程式設計模型 (包含屬性與行為) 與通道模型 (包含處理站與接聽程式、訊息編碼器，以及傳輸和通訊協定實作)。 一般來說，實作繫結項目與繫結的目的是要啟用通道，以供應用程式層使用。  
  
 通道層會與服務層互相傳遞與接收訊息，並在端點之間傳輸這些訊息。 在用戶端，通道層是指建立網路端點通道的通道處理站堆疊。 在服務上，通道層則是指接受網路端點上所接收之通道的通道接聽程式堆疊。  
  
 一般的通道類型有兩種：通訊協定通道與傳輸通道。 傳輸通道負責將訊息從某個網路端點實際傳輸到另一個網路端點， 而且必須具備預設的訊息編碼器，同時也要能夠使用透過訊息編碼器繫結項目所提供的替代訊息編碼器。 訊息編碼器負責將 <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> 轉換為 Wire 表示法，反之亦然。 通訊協定通道負責實作 SOAP 層級的通訊協定 (例如，WS-Security 或 WS-ReliableMessaging)。  
  
 對於傳輸與通訊協定通道的主要要求，就是它們必須實作必要的通道介面。 若要建立可運作的通道層，它們必須具備相關的處理站與接聽程式等等。 若要使用 WCF 的通道實作為，每個通道都必須有一個衍生<xref:System.ServiceModel.Channels.BindingElement>自的相關繫結項目，而且必須要有相關的系結延伸模組元素，才能包含在衍生自<xref:System.ServiceModel.Configuration.BindingElementExtensionElement>的設定檔中.  
  
 如上所述，您可以堆疊訊息編碼器、通訊協定與傳輸通道實作的繫結項目來產生通道堆疊，而將這些項目依序組合起來的機制就是繫結。 繫結與繫結項目會將應用程式的程式設計模型連接至通道模型。 您可以直接使用程式碼中的通道實作，但是除非編碼器、傳輸與通訊協定都實作為繫結項目，否則您無法透過服務層程式設計模型來使用它們。  
  
 如需開發通道及其繫結項目的詳細資訊，請參閱[擴充通道層](extending-the-channel-layer.md)。

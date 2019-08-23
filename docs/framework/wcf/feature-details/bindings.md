---
title: Windows Communication Foundation 繫結
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], bindings
- Windows Communication Foundation [WCF], bindings
- bindings [WCF]
ms.assetid: 83639133-89f7-43f0-b4ef-8d9e57c08d25
ms.openlocfilehash: e7071d56c8dc4b953c4b6349660ca4a8a1b7d23e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952622"
---
# <a name="windows-communication-foundation-bindings"></a>Windows Communication Foundation 繫結
Windows Communication Foundation (WCF) 會分隔應用程式的軟體如何從與其他軟體通訊的方式撰寫。 繫結可用來指定必要的傳輸、編碼與通訊協定詳細資料，以供用戶端與服務彼此通訊。 WCF 會使用系結來產生端點的基礎連線標記法, 因此, 通訊的合作物件必須同意大部分的系結詳細資料。 要達到這個目的之最簡單方式，就是讓服務用戶端使用服務端點所使用的相同繫結。 如需如何執行此動作的詳細資訊, 請參閱使用系結[來設定服務和用戶端](../using-bindings-to-configure-services-and-clients.md)。  
  
 繫結是由繫結項目集合所組成。 每個項目負責針對端點與用戶端通訊的方式稍加描述。 繫結必須包含至少一個傳輸繫結項目、一個訊息編碼繫結項目 (根據預設，可由傳輸繫結項目來提供)，以及任意數量的其他通訊協定繫結項目。 由此描述來建立執行階段的處理序，可讓每個繫結項目將程式碼撰寫到該執行階段中。  
  
 WCF 提供系結, 其中包含繫結項目的一般選取專案。 您可以搭配預設設定來使用它們，或是根據使用者需求來修改這些預設值。 這些系統提供的繫結所包含的屬性可讓您直接控制繫結項目與其設定。 您也可以輕鬆地同時使用多個版本的繫結，只需為每個繫結版本提供屬於自己的名稱即可。 如需詳細資訊, 請參閱設定[系統提供的](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)系結。  
  
 如果您需要繫結項目的集合 (尚未由這些系統提供繫結之任意繫結所提供)，可以建立包含所需繫結項目集合的自訂繫結。 這些自訂繫結很容易建立，而且不需要新的類別，但是它們無法提供屬性讓您控制繫結項目或其設定。 您可以存取繫結項目並透過包含這些繫結項目的集合來修改其設定。 如需詳細資訊, 請參閱[自訂](../../../../docs/framework/wcf/extending/custom-bindings.md)系結。  
  
## <a name="in-this-section"></a>本節內容  
 [設定系統提供的繫結](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 描述如何使用和修改 WCF 提供的系結, 以支援常見的案例。  
  
 [使用繫結設定服務與用戶端](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 描述如何在程式碼中以命令方式定義服務和用戶端的 Windows Communication Foundation (WCF) 系結, 並使用設定進行宣告。  
  
 [自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 說明何謂 <xref:System.ServiceModel.Channels.CustomBinding> 與其使用時機。  
  
## <a name="reference"></a>參考資料  
 <xref:System.ServiceModel.Channels.Binding>  
  
 <xref:System.ServiceModel.Channels.BindingElement>  
  
 <xref:System.ServiceModel.Channels.CustomBinding>  
  
## <a name="related-sections"></a>相關章節  
 [擴充繫結](../../../../docs/framework/wcf/extending/extending-bindings.md)

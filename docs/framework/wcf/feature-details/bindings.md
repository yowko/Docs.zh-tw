---
title: Windows Communcation Foundation 繫結
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], bindings
- Windows Communication Foundation [WCF], bindings
- bindings [WCF]
ms.assetid: 83639133-89f7-43f0-b4ef-8d9e57c08d25
ms.openlocfilehash: 1930826cf51d67ceb789e20920ca42f04d1adc1b
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45587398"
---
# <a name="windows-communication-foundation-bindings"></a>Windows Communication Foundation 繫結
Windows Communication Foundation (WCF) 會分隔應用程式軟體從它如何與其他軟體通訊的撰寫方式。 繫結可用來指定必要的傳輸、編碼與通訊協定詳細資料，以供用戶端與服務彼此通訊。 WCF 會使用繫結來產生端點的基礎 wire 表示，因此大部分的繫結詳細資料必須同意所要通訊的合作對象。 要達到這個目的之最簡單方式，就是讓服務用戶端使用服務端點所使用的相同繫結。 如需如何執行這項操作的詳細資訊，請參閱[來設定 Windows Communication Foundation 服務和用戶端使用的繫結](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)。  
  
 繫結是由繫結項目集合所組成。 每個項目負責針對端點與用戶端通訊的方式稍加描述。 繫結程序必須包含至少一個傳輸繫結程序項目、一個訊息編碼繫結程序項目 (根據預設，可由傳輸繫結程序項目來提供)，以及任意數量的其他通訊協定繫結程序項目。 由此描述來建立執行階段的處理序，可讓每個繫結項目將程式碼撰寫到該執行階段中。  
  
 WCF 提供的繫結包含一般的選取項目繫結項目。 您可以搭配預設設定來使用它們，或是根據使用者需求來修改這些預設值。 這些系統提供的繫結所包含的屬性可讓您直接控制繫結項目與其設定。 您也可以輕鬆地同時使用多個版本的繫結，只需為每個繫結版本提供屬於自己的名稱即可。 如需詳細資訊，請參閱 < [Configuring System-Provided 繫結](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)。  
  
 如果您需要繫結項目的集合 (尚未由這些系統提供繫結之任意繫結所提供)，可以建立包含所需繫結項目集合的自訂繫結。 這些自訂繫結很容易建立，而且不需要新的類別，但是它們無法提供屬性讓您控制繫結項目或其設定。 您可以存取繫結項目並透過包含這些繫結項目的集合來修改其設定。 如需詳細資訊，請參閱 <<c0> [ 自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [設定系統提供的繫結](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 描述如何使用及修改 WCF 提供來支援常見案例的繫結。  
  
 [使用繫結來設定 Windows Communication Foundation 服務和用戶端](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 描述如何在程式碼和以宣告方式使用組態中以命令方式定義服務和用戶端的 Windows Communication Foundation (WCF) 繫結。  
  
 [自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 說明何謂 <xref:System.ServiceModel.Channels.CustomBinding> 與其使用時機。  
  
## <a name="reference"></a>參考資料  
 <xref:System.ServiceModel.Channels.Binding>  
  
 <xref:System.ServiceModel.Channels.BindingElement>  
  
 <xref:System.ServiceModel.Channels.CustomBinding>  
  
## <a name="related-sections"></a>相關章節  
 [擴充繫結](../../../../docs/framework/wcf/extending/extending-bindings.md)

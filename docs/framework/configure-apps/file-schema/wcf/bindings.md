---
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: 1292bc38ce1e542086edac5539c1b29e619e2a32
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926375"
---
# <a name="bindings"></a>\<bindings>

您可以使用`bindings`元素來設定 Windows Communication Foundation (WCF) 的標準和自訂系結集合。 每個項目都是 `binding` 項目，可由其唯一的 `name` 所識別。 服務會使用 `name` 來連結繫結，以便利用繫結。 從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。 如需預設設定和無相關系結和行為的詳細資訊, 請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。  
  
## <a name="system-provided-bindings"></a>系統提供的繫結
 
 系統提供的繫結會隱藏 WCF 訊息堆疊的複雜性。 使用系統提供之繫結的應用程式不需要對堆疊有完整控制權。 在每個系統提供之繫結上公開的屬性，最適合繫結所處理的使用案例。  
  
 每個系統提供之繫結的組態區段可定義用於設定繫結的多個組態。 每個組態是由唯一的名稱來識別。  
  
 您無法將元素或屬性加入至系統提供的系結。 若要這樣做, 您應該執行自訂系結, 如[自訂](#custom-bindings)系結一節中所述。 您可以定義自訂系結, 以完美模擬系統提供的系結, 並新增使用者應用程式想要控制的幾個設定。  
  
 如需系統提供之系結的清單, 請參閱[系統提供](../../../wcf/system-provided-bindings.md)的系結。  
  
## <a name="custom-bindings"></a>自訂系結

 自訂繫結會提供對於 WCF 訊息堆疊的完整控制權。 個別繫結定義訊息堆疊的方式，是依據堆疊項目在堆疊中的出現順序來指定其組態項目。 每個元素都會定義和設定堆疊的一個元素。 各個自訂繫結中一定要出現一個而且是唯一一個 `transport` 項目。 如果沒有這個項目，訊息堆疊就不完整。  
  
 項目在堆疊中的出現順序很重要，因為這是作業套用至訊息的順序。 建議的堆疊項目順序如下所示：  
  
1. 交易 (選擇性)  
  
2. 可靠的訊息處理 (選擇性)  
  
3. 安全性 (選擇性)  
  
4. 編碼器  
  
5. Transport  
  
 自訂繫結是由其 `name` 屬性所識別。 如需自訂系結的詳細資訊, 請參閱[自訂](../../../wcf/extending/custom-bindings.md)系結。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>  
- [繫結](../../../wcf/bindings.md)  
- [自訂繫結](../../../wcf/extending/custom-bindings.md)  
- [\<customBinding>](custombinding.md)  
- [\<binding>](../../../misc/binding.md)

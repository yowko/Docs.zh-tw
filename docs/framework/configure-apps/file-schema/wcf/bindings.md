---
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: 479941593b1abefe637525703140b02917c6692b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59316787"
---
# <a name="bindings"></a>\<bindings>

您可以使用`bindings`項目來設定標準和自訂繫結的 Windows Communication Foundation (WCF) 的集合。 每個項目都是 `binding` 項目，可由其唯一的 `name` 所識別。 服務會使用 `name` 來連結繫結，以便利用繫結。 從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。 如需有關預設組態和無名稱繫結和行為的詳細資訊，請參閱 < [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md)並[Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。  
  
## <a name="system-provided-bindings"></a>系統提供的繫結
 
 系統提供的繫結會隱藏 WCF 訊息堆疊的複雜性。 使用系統提供之繫結的應用程式不需要對堆疊有完整控制權。 在每個系統提供之繫結上公開的屬性，最適合繫結所處理的使用案例。  
  
 每個系統提供之繫結的組態區段可定義用於設定繫結的多個組態。 每個組態是由唯一的名稱來識別。  
  
 您無法將項目或屬性新增至系統提供繫結。 若要這樣做，您應該實作自訂繫結中所述[自訂繫結](#custom-bindings)一節。 可以定義自訂繫結會模擬系統提供繫結完美，並新增一些使用者應用程式想要控制的設定。  
  
 如需系統提供繫結的清單，請參閱 < [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md)。  
  
## <a name="custom-bindings"></a>自訂繫結

 自訂繫結會提供對於 WCF 訊息堆疊的完整控制權。 個別繫結定義訊息堆疊的方式，是依據堆疊項目在堆疊中的出現順序來指定其組態項目。 每個項目定義，及設定堆疊的一個項目。 各個自訂繫結中一定要出現一個而且是唯一一個 `transport` 項目。 如果沒有這個項目，訊息堆疊就不完整。  
  
 項目在堆疊中的出現順序很重要，因為這是作業套用至訊息的順序。 建議的堆疊項目順序如下所示：  
  
1. 交易 (選擇性)  
  
2. 可靠傳訊 （選擇性）  
  
3. 安全性 (選擇性)  
  
4. 編碼器  
  
5. Transport  
  
 自訂繫結是由其 `name` 屬性所識別。 如需有關自訂繫結的詳細資訊，請參閱 <<c0> [ 自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>  
- [繫結](../../../../../docs/framework/wcf/bindings.md)  
- [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
- [\<binding>](../../../../../docs/framework/misc/binding.md)

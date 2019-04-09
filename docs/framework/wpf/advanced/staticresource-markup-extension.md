---
title: StaticResource 標記延伸
ms.date: 03/30/2017
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
ms.openlocfilehash: 8319e451268152e95326c02027157db72df631b8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125142"
---
# <a name="staticresource-markup-extension"></a>StaticResource 標記延伸
提供值的任何[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]屬性，藉由查閱已定義之資源的參考。 該資源查閱行為相當於載入時間對應，它會尋找先前已載入，從目前標記的資源[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]其他應用程式來源，以及頁面上，且會產生做為該資源值在執行階段物件中的屬性值。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xml  
<object property="{StaticResource key}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>XAML 物件項目用法  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`key`|要求資源的金鑰。 此機碼一開始已由[X:key 指示詞](../../xaml-services/x-key-directive.md)如果資源在標記中，已建立，或已提供為`key`參數呼叫時<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>如果程式碼中所建立的資源。|  
  
## <a name="remarks"></a>備註  
  
> [!IMPORTANT]
>  A`StaticResource`不應嘗試要向前參考資源定義在語彙上進一步[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案。 不支援嘗試執行此作業，而且即使這類的參考不會失敗，嘗試向前參考將會產生載入時間效能產生負面影響時代表內部的雜湊表<xref:System.Windows.ResourceDictionary>會搜尋。 為了獲得最佳結果，調整資源字典的組合，使您可以避免向前參考。 如果您不能避免向前參考，請使用[DynamicResource 標記延伸](dynamicresource-markup-extension.md)改。  
  
 指定<xref:System.Windows.StaticResourceExtension.ResourceKey%2A>應該會對應至現有的資源，以識別[X:key 指示詞](../../xaml-services/x-key-directive.md)一些在您的頁面、 應用程式、 可用的控制項主題和外部資源或系統資源的層級。 依此順序，就會發生資源查閱。 如需靜態和動態資源的資源查閱行為的詳細資訊，請參閱[XAML 資源](xaml-resources.md)。  
  
 資源索引鍵可以是任何字串中定義[XamlName 文法](../../xaml-services/xamlname-grammar.md)。 資源索引鍵也可以是其他物件類型，例如<xref:System.Type>。 A<xref:System.Type>金鑰是透過隱含樣式索引鍵，如何可以由佈景主題，有樣式控制項的基礎。 如需詳細資訊，請參閱[控制項撰寫概觀](../controls/control-authoring-overview.md)。  
  
 豐富的宣告式方法的參考資源是以[DynamicResource 標記延伸](dynamicresource-markup-extension.md)。  
  
 屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。 `StaticResource` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 延伸類別的 <xref:System.Windows.StaticResourceExtension> 值。  
  
 `StaticResource` 可用於物件元素語法。 在此案例中，指定的值<xref:System.Windows.StaticResourceExtension.ResourceKey%2A>屬性是必要項。  
  
 `StaticResource` 也可以用於指定的詳細資訊的屬性使用方式<xref:System.Windows.StaticResourceExtension.ResourceKey%2A>屬性做為屬性 = 值組：  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 詳細使用方式通常是適用於具有一個以上可設定屬性或有些屬性為選擇性屬性的標記延伸。 因為 `StaticResource` 只有一個必要的可設定屬性，所以這種詳細使用方式並不常見。  
  
 在  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器實作中，這個標記延伸的處理由定義<xref:System.Windows.StaticResourceExtension>類別。  
  
 `StaticResource` 是標記延伸。 如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。 如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。  
  
## <a name="see-also"></a>另請參閱

- [樣式設定和範本化](../controls/styling-and-templating.md)
- [XAML 概觀 (WPF)](xaml-overview-wpf.md)
- [標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)
- [XAML 資源](xaml-resources.md)
- [資源和程式碼](resources-and-code.md)

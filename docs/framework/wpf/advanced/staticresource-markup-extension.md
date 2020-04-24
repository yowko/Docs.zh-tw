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
ms.openlocfilehash: 5c0bb247bae525658d89d53f1672e57b87aba7bc
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646218"
---
# <a name="staticresource-markup-extension"></a>StaticResource 標記延伸
通過查找對已定義的[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]資源的引用,為任何屬性屬性提供值。 該資源的查找行為類似於載入時間查找,它將查找以前從當前[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面標記和其他應用程式源載入的資源,並將該資源值生成為運行時物件中的屬性值。  
  
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
|`key`|要求資源的金鑰。 如果在標記中創建了資源,則[x:Key 指令](../../../desktop-wpf/xaml-services/xkey-directive.md)最初分配此密鑰,或者`key`<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>在調用 資源時作為參數提供, 則調用資源是在代碼中創建的。|  
  
## <a name="remarks"></a>備註  
  
> [!IMPORTANT]
> 不得`StaticResource`嘗試對[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]文件中進一步定義的資源進行轉發引用。 不支援嘗試執行此操作,即使此類引用未失敗,在搜索表示<xref:System.Windows.ResourceDictionary>a 的內部哈希表時,嘗試正向引用也會造成載入時間性能損失。 為獲得最佳效果,請調整資源字典的組成,以避免轉發引用。 如果無法避免正向參考,請改用[動態資源標記延伸](dynamicresource-markup-extension.md)。  
  
 指定的<xref:System.Windows.StaticResourceExtension.ResourceKey%2A>資源應對應於現有資源,該資源在頁面、應用程式、可用控制主題和外部資源或系統資源的某個級別使用[x:Key 指令](../../../desktop-wpf/xaml-services/xkey-directive.md)標識。 資源查找按該順序進行。 有關靜態和動態資源的資源查找行為的詳細資訊,請參閱[XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。  
  
 資源鍵可以是[XamlName 語法](../../../desktop-wpf/xaml-services/xamlname-grammar.md)中定義的任何字串。 資源金鑰也可以是其他物件類型,如<xref:System.Type>。 鍵<xref:System.Type>是如何通過隱式樣式鍵按主題設置控件樣式的基礎。 如需詳細資訊，請參閱[控制項撰寫概觀](../controls/control-authoring-overview.md)。  
  
 參考資源的替代方法宣告性方法是作為[動態資源標記延伸](dynamicresource-markup-extension.md)。  
  
 屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。 `StaticResource` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 延伸類別的 <xref:System.Windows.StaticResourceExtension> 值。  
  
 `StaticResource`可用於物件元素語法。 在這種情況下,需要指定<xref:System.Windows.StaticResourceExtension.ResourceKey%2A>屬性的值。  
  
 `StaticResource` 也可以用於會指定 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 屬性 (Property) 做為 property=value 配對組的詳細屬性 (Attribute) 使用方式中。  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 詳細使用方式通常是適用於具有一個以上可設定屬性或有些屬性為選擇性屬性的標記延伸。 因為 `StaticResource` 只有一個必要的可設定屬性，所以這種詳細使用方式並不常見。  
  
 在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器實現中,此標記擴展的處理由<xref:System.Windows.StaticResourceExtension>類定義。  
  
 `StaticResource` 是一種標記延伸。 如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。 如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。  
  
## <a name="see-also"></a>另請參閱

- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)
- [XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [資源和程式碼](resources-and-code.md)

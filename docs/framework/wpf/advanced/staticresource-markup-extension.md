---
title: "StaticResource 標記延伸"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 97b83feb9d19760208d9cc103290c5c6293c30c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="staticresource-markup-extension"></a>StaticResource 標記延伸
提供的任何值[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]property 屬性，查看已定義之資源的參考。 該資源的查閱行為相當於載入時查閱，從目前標記先前已載入的資源將會尋找[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面以及其他應用程式的來源，而且將會產生做為該資源值在執行階段物件的屬性值。  
  
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
|`key`|要求資源的金鑰。 此機碼一開始指派[X:key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)如果資源在標記中，建立或提供做為`key`參數呼叫時<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>如果此資源原先建立在程式碼中。|  
  
## <a name="remarks"></a>備註  
  
> [!IMPORTANT]
>  A`StaticResource`不得嘗試進行向前參考到資源定義在語彙上應進一步[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案。 不支援嘗試執行這項操作，，即使這類的參考不會失敗，嘗試向前參考將會產生載入時間效能損失時代表內部的雜湊表<xref:System.Windows.ResourceDictionary>會搜尋。 為獲得最佳結果，調整資源字典的組合，您可以避免向前參考。 如果您無法避免向前參考，請使用[DynamicResource 標記延伸](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)改為。  
  
 指定<xref:System.Windows.StaticResourceExtension.ResourceKey%2A>應該對應至現有的資源，以識別[X:key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)某個層級中頁面、 應用程式、 可用的控制項佈景主題和外部資源或系統資源。 依此順序，就會發生資源查閱。 如需靜態和動態資源的資源查閱行為的詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
 資源索引鍵可以是任何字串中定義[XamlName 文法](../../../../docs/framework/xaml-services/xamlname-grammar.md)。 資源索引鍵也可以是其他物件類型，例如<xref:System.Type>。 A<xref:System.Type>索引鍵是透過隱含樣式索引鍵，如何可由、 佈景主題樣式化控制項的基礎。 如需詳細資訊，請參閱[控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)。  
  
 其他的宣告式方法的參考的資源是為[DynamicResource 標記延伸](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)。  
  
 屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。 `StaticResource` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 延伸類別的 <xref:System.Windows.StaticResourceExtension> 值。  
  
 `StaticResource`可用於物件項目語法。 在此情況下，指定的值<xref:System.Windows.StaticResourceExtension.ResourceKey%2A>是必要屬性。  
  
 `StaticResource` 也可以用於會指定 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 屬性 (Property) 做為 property=value 配對組的詳細屬性 (Attribute) 使用方式中。  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 詳細使用方式通常是適用於具有一個以上可設定屬性或有些屬性為選擇性屬性的標記延伸。 因為 `StaticResource` 只有一個必要的可設定屬性，所以這種詳細使用方式並不常見。  
  
 在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器實作所定義的這個標記延伸處理<xref:System.Windows.StaticResourceExtension>類別。  
  
 `StaticResource` 是一種標記延伸。 如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。 如需詳細資訊，請參閱[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
## <a name="see-also"></a>請參閱  
 [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [資源和程式碼](../../../../docs/framework/wpf/advanced/resources-and-code.md)

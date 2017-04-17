---
title: "x:Uid Directive | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XAML [XAML Services], localizable content attribute"
  - "XAML [XAML Services], x:Uid attribute"
  - "x:Uid attribute [XAML Services]"
  - "Uid attribute [XAML Services]"
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
caps.latest.revision: 12
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 12
---
# x:Uid Directive
提供用於標記項目的唯一識別碼。  在許多案例中，這個唯一識別項都由 XAML 當地語系化處理序和工具使用。  
  
## XAML Attribute Usage  
  
```  
<object x:Uid="identifier"... />  
```  
  
## XAML 值  
  
|||  
|-|-|  
|`identifier`|手動建立或自動產生的字串，當`x:Uid`消費者解譯檔案時，該字串應該是檔案中唯一的字串。|  
  
## 備註  
 在 \[MS\-XAML\] 中，`x:Uid` 被定義為指示詞。  如需詳細資訊，請參閱 [\[MS\-XAML\] 5.3.6 章](http://go.microsoft.com/fwlink/?LinkId=114525)。  
  
 `x:Uid` 不同於 `x:Name`，這是因為所敘述的 XAML 當地語系化案例，所以當地語系化使用的識別項沒有 `x:Name` 之程式設計模型影響的相依性。  而且，`x:Name` 是由 XAML 名稱範圍管理，但 `x:Uid` 則是不由唯一性強制的任何 XAML 語言定義概念管理。  廣泛意義的 XAML 處理器 \(不是當地語系化處理序之一部分的處理器\) 不應該強制 `x:Uid` 值的唯一性。  該責任在概念上屬於值的建立者。  在單一 XAML 來源內 `x:Uid` 值之唯一性的預期，對於這些值的消費者是合理的，例如專用的全球化流程或工具。  一般唯一性模型是，`x:Uid` 值在表示 XAML 的 XML 編碼檔案中都是唯一的。  
  
 具有特定 XAML 結構描述之重要知識的工具，只能選擇對真正的可當地語系化字串套用 `x:Uid`，而不適用於在標記中遇到文字字串值的所有情況。  
  
 藉由將 <xref:System.Windows.Markup.UidPropertyAttribute> 屬性套用至定義的型別，架構可以將其專案模型中的特定屬性指定為 `x:Uid` 的別名。  如果框架指定一個特定的屬性，則在相同的物件上指定`x:Uid`和別名成員就無效。  如果指定 `x:Uid` 和別名成員，.NET Framework XAML Services API 通常會擲回此案例的 <xref:System.Xaml.XamlDuplicateMemberException>。  
  
## WPF 使用注意事項  
 如需 WPF 當地語系化流程中和 XAML 之 BAML 形式中 `x:Uid` 之角色的詳細資訊，請參閱 [WPF 的全球化](../../../ocs/framework/wpf/advanced/globalization-for-wpf.md) 或 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>。  
  
## 請參閱  
 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>   
 <xref:Microsoft.Build.Tasks.Windows.UidManager>   
 [WPF 的全球化](../../../ocs/framework/wpf/advanced/globalization-for-wpf.md)
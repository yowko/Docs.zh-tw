---
title: "x:ClassModifier Directive | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "xClassModifier"
  - "x:ClassModifier"
  - "ClassModifier"
helpviewer_keywords: 
  - "XAML [XAML Services], x:ClassModifier attribute"
  - "x:ClassModifier attribute [XAML Services]"
  - "ClassModifier attribute in XAML [XAML Services]"
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
caps.latest.revision: 22
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 21
---
# x:ClassModifier Directive
修改同時提供 `x:Class` 時的 XAML 編譯行為。  具體而言，不建立部分 `class` \(具有`Public`存取級別 （預設值）\)，而是以 `NotPublic` 存取級別建立提供的 `x:Class`。  這個行為影響產生組件中的類別存取層級。  
  
## XAML Attribute Usage  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## XAML 值  
  
|||  
|-|-|  
|*NotPublic*|依據使用的程式碼後置程式設計語言而定，用於指定 <xref:System.Reflection.TypeAttributes?displayProperty=fullName> 與 <xref:System.Reflection.TypeAttributes?displayProperty=fullName> 的確切傳遞字串都會有所不同。  請參閱＜備註＞。|  
  
## 相依性  
 在相同項目上也必須提供 [x:Class](../../../docs/framework/xaml-services/x-class-directive.md)，而且該項目必須是頁面的根項目。  如需詳細資訊，請參閱 [\[MS\-XAML\] 4.3.1.8 章](http://go.microsoft.com/fwlink/?LinkId=114525) \(英文\)。  
  
## 備註  
 .NET Framework XAML 服務使用方式中的 `x:ClassModifier` 值會隨程式設計語言而改變。  每個語言實作其 <xref:System.CodeDom.Compiler.CodeDomProvider> 的方式、它所傳回用來定義 <xref:System.Reflection.TypeAttributes?displayProperty=fullName> 和 <xref:System.Reflection.TypeAttributes?displayProperty=fullName> 意義的型別轉換子，以及該語言是否區分大小寫，都會決定所要使用的字串。  
  
-   對於 [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)]，用於指定 <xref:System.Reflection.TypeAttributes?displayProperty=fullName> 的傳遞字串是 `internal`。  
  
-   對於 [!INCLUDE[TLA2#tla_visualbnet](../../../includes/tla2sharptla-visualbnet-md.md)]，用於指定 <xref:System.Reflection.TypeAttributes?displayProperty=fullName> 的傳遞字串是 `Friend`。  
  
-   針對 [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)]，沒有支援編譯 XAML 的目標存在；因此未指定要傳遞的值。  
  
 您也可以指定 <xref:System.Reflection.TypeAttributes?displayProperty=fullName> \([!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)] 中的 `public`、[!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)] 中的 `Public`\)，但是指定 <xref:System.Reflection.TypeAttributes?displayProperty=fullName> 並不常見，因為 <xref:System.Reflection.TypeAttributes?displayProperty=fullName> 已經是預設的行為。  
  
 其他具有對等使用者程式碼存取層級限制 \(例如，[!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)] 中的 `private`\) 與 `x:ClassModifier` 並不相關，因為 XAML 中並不支援巢狀類別參考，因此 <xref:System.Reflection.TypeAttributes?displayProperty=fullName> 修飾詞具有相同的作用。  
  
## 安全性提示  
 在 `x:ClassModifier` 中所宣告的存取層級，依然取決於特定架構的解譯及其功能。  如果是透過 pack URI 從 WPF 資源參考該類別，WPF 就包括載入和執行個體化其 `x:ClassModifier` 為 `internal` 之型別的能力。  因為此情況與其他框架實作之相似情況的緣故，請勿僅只依靠 `x:ClassModifier` 來封鎖所有可能的執行個體化嘗試。  
  
## 請參閱  
 [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md)   
 [WPF 中的程式碼後置和 XAML](../../../ocs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)   
 [x:FieldModifier Directive](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md)   
 [安全性 \(WPF\)](../../../ocs/framework/wpf/security-wpf.md)   
 [Types Migrated from WPF to System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
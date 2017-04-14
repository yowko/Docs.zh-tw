---
title: "x:FieldModifier Directive | Microsoft Docs"
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
  - "FieldModifier attribute in XAML [XAML Services]"
  - "x:FieldModifier attribute [XAML Services]"
  - "XAML [XAML Services], x:FieldModifier attribute"
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
caps.latest.revision: 15
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 14
---
# x:FieldModifier Directive
修改 XAML 編譯行為，讓具名物件的欄位以 <xref:System.Reflection.TypeAttributes?displayProperty=fullName> 存取定義，而不是以 <xref:System.Reflection.TypeAttributes?displayProperty=fullName> 預設行為定義。  
  
## XAML Attribute Usage  
  
```  
<object x:FieldModifier="Public".../>  
```  
  
## XAML 值  
  
|||  
|-|-|  
|*Public*|依據使用的程式碼後置程式設計語言而定，用於指定 <xref:System.Reflection.TypeAttributes?displayProperty=fullName> 與 <xref:System.Reflection.TypeAttributes?displayProperty=fullName> 的確切傳遞字串都會有所不同。  請參閱＜備註＞。|  
  
## 相依性  
 如果 XAML 產物在任何位置使用 `x:FieldModifier`，該 XAML 產物的根項目就必須宣告 [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md)。  
  
## 備註  
 `x:FieldModifier` 與宣告類別和其成員的一般存取層級無關。  只有在處理做為 XAML 產物之部分的特別 XAML 物件時，它才會與 XAML 處理行為有關，並會成為可在應用程式的物件圖形中存取的物件。  根據預設，這類物件的欄位參考會保持為私用，這樣可以防止控制項消費者直接修改物件圖形。  而是預期控制項消費者使用程式設計模型所啟用的標準模式，例如取得配置根、子項目集合、專用的公用屬性等，來修改物件圖形。  
  
 `x:FieldModifier` 屬性的值會因為程式設計語言而有所不同，其用途也會在特定的架構中變動。  每個語言實作其 <xref:System.CodeDom.Compiler.CodeDomProvider> 的方式、它所傳回用來定義 <xref:System.Reflection.TypeAttributes?displayProperty=fullName> 和 <xref:System.Reflection.TypeAttributes?displayProperty=fullName> 意義的型別轉換子，以及該語言是否區分大小寫，都會決定所要使用的字串。  
  
-   對於 [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)]，用於指定 <xref:System.Reflection.TypeAttributes?displayProperty=fullName> 的傳遞字串是 `public`。  
  
-   對於 [!INCLUDE[TLA2#tla_visualbnet](../../../includes/tla2sharptla-visualbnet-md.md)]，用於指定 <xref:System.Reflection.TypeAttributes?displayProperty=fullName> 的傳遞字串是 `Public`。  
  
-   對於 [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)]，目前沒有 XAML 的目標存在；因此未定義要傳遞的字串。  
  
 您也可以指定 <xref:System.Reflection.TypeAttributes?displayProperty=fullName> \([!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)] 中的 `internal`，[!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)] 中的 `Friend`\)，但是指定 <xref:System.Reflection.TypeAttributes?displayProperty=fullName> 並不常用，因為 `NotPublic` 已經是預設的行為。  
  
 <xref:System.Reflection.TypeAttributes?displayProperty=fullName>是預設行為，因為編譯 XAML 之組譯碼外的程式碼幾乎不需存取 XAML建立的項目。  WPF 安全性架構與 XAML 編譯行為搭配，不會將存放項目執行個體的欄位宣告為公用，除非您特地設定 `x:FieldModifier` 以允許公用存取。  
  
 對於具有 [x:Name Directive](../../../docs/framework/xaml-services/x-name-directive.md)的項目而言，`x:FieldModifier` 是唯一有意義的，因為在欄位成為公用欄位之後，就會使用該名稱參考欄位。  
  
 根項目的部分類別預設是公用的，但可以使用 [x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md)設定為非公用。  [x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md)也會影響根項目類別執行個體的存取層級。  您可以同時在根項目上放置 `x:Name` 和 `x:FieldModifier`，但這只會建立根項目的公用欄位複本，而真正的根項目類別存取層級仍然是由 [x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md)所控制。  
  
## 請參閱  
 [WPF 的 XAML 和自訂類別](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)   
 [WPF 中的程式碼後置和 XAML](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)   
 [x:Name Directive](../../../docs/framework/xaml-services/x-name-directive.md)   
 [建置 WPF 應用程式 \(WPF\)](../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)   
 [x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md)
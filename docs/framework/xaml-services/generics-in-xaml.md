---
title: "Generics in XAML | Microsoft Docs"
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
  - "generics [XAML Services]"
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
caps.latest.revision: 8
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 8
---
# Generics in XAML
.NET Framework XAML 服務實作於 System.Xaml 時，可提供泛型 CLR 型別的使用支援。  此支援包括將泛型條件約束指定為型別引數，以及為泛型集合案例呼叫適當的 `Add` 方法，以強制執行條件約束。  本主題說明 XAML 中的泛型型別在使用及參考上的各個層面。  
  
## x:TypeArguments  
 `x:TypeArguments` 是 XAML 語言所定義的指示詞。  做為泛型型別所支援的 XAML 型別成員時，`x:TypeArguments` 會將泛型的限制型別引數傳遞至支援建構函式。  對於 `x:TypeArguments` 的 .NET Framework XAML 服務用法，如需相關的參考語法，請參閱 [x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md)。  
  
 由於 `x:TypeArguments` 會採用字串，並具有型別轉換子支援，因此在 XAML 用法中通常會宣告為屬性。  
  
 在 XAML 節點資料流中，`x:TypeArguments` 所宣告的資訊可在節點資料流中的 `StartObject` 位置上，從 <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=fullName> 取得。  <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=fullName> 的傳回值是 <xref:System.Xaml.XamlType> 值的清單。  XAML 型別是否代表泛型型別，可藉由呼叫 <xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=fullName> 來判斷。  
  
## XAML 泛型的規則與語法慣例  
 在 XAML 中，泛型型別必須一律以受限制泛型表示；不受限制的泛型一律不會存在於 XAML 型別系統或 XAML 節點資料流中，並且無法以 XAML 標記表示。  當泛型是要由 `x:TypeArguments` 參考的巢狀型別條件約束時，或是在 `x:Type` 為泛型型別提供 CLR 型別參考時，可在 XAML 屬性語法內參考泛型。  此作法可透過 .NET Framework XAML 服務所定義的 <xref:System.Xaml.Schema.XamlTypeTypeConverter> 類別受到支援。  
  
 <xref:System.Xaml.Schema.XamlTypeTypeConverter> 所啟用的 XAML 屬性語法格式改變了一般對泛型的型別與條件約束使用角括號的 MSIL \/ CLR 語法慣例，而改以括號 \(parenthese\) 做為條件約束容器。  如需範例，請參閱 [x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md)。  
  
## 泛型與 XAML 2009 功能  
 使用 XAML 2009 時，除了可對應 CLR 基底型別以取得一般語言基礎型別的 XAML 型別以外，您也可以使用 [XAML 2009 內建型別](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)做為 `x:TypeArguments` 中的資訊項目。  例如，您可以宣告下列項目 \(不會顯示前置詞對應，但 `x` 是 XAML 2009 的 XAML 語言 XAML 命名空間\)：  
  
```  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
## WPF 與其他 v3.5 Frameworks 中的泛型支援  
 在使用 XAML 2006 時若明確地以 WPF 為目標，則必須在相同的項目上提供 [x:Class](../../../docs/framework/xaml-services/x-class-directive.md) 做為 `x:TypeArguments`，且該項目必須是 XAML 文件中的根項目。  根項目必須對應至最少有一個型別引數的泛型型別。  <xref:System.Windows.Navigation.PageFunction%601> 即為一個範例。  
  
 若要支援泛型用法，可行的因應措施包括定義可傳回泛型型別的自訂標記延伸，或提供衍生自泛型型別、但將泛型條件約束簡化到其本身之類別定義中的包覆式類別定義。  
  
 在 WPF 與目標 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 中，您可以搭配使用 XAML 2009 功能與 `x:TypeArguments`，但是只適用於鬆散 XAML \(未進行標記編譯的 XAML\)。  WPF 的標記編譯 XAML 以及 XAML 的 BAML 表單目前不支援 XAML 2009 關鍵字和功能。  
  
 [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] for [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 中的自訂工作流程不支援泛型 XAML 用法。  
  
## 請參閱  
 [x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md)   
 [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md)   
 [Built\-in Types for Common XAML Language Primitives](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)
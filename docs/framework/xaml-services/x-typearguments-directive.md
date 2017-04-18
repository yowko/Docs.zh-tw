---
title: "x:TypeArguments Directive | Microsoft Docs"
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
  - "x:TypeArguments"
  - "xTypeArguments"
  - "TypeArguments"
helpviewer_keywords: 
  - "x:TypeArguments attribute [XAML Services]"
  - "TypeArguments attribute in XAML [XAML Services]"
  - "XAML [XAML Services], x:TypeArguments attribute"
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
caps.latest.revision: 18
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 18
---
# x:TypeArguments Directive
將泛型型別的條件約束型別引數傳遞至泛型型別的建構函式。  
  
## XAML Attribute Usage  
  
```  
<object x:TypeArguments="typeString" .../>  
```  
  
## XAML 值  
  
|||  
|-|-|  
|`object`|XAML 型別的物件項目宣告，由 CLR 泛型型別所支援。  如果`object` 參考不是來自預設 XAML 命名空間的 XAML 類型，`object` 會需要前置詞來指出 `object`存在的 XAML 命名空間。|  
|`typeString`|字串，將一個或多個 XAML 型別名稱宣告為字串，可提供 CLR 泛型型別的型別引數。  如需其他語法附註，請參閱＜備註＞。|  
  
## 備註  
 在大多數情況下，用來做為 `typeString` 字串中的資訊項目的 XAML 型別都會加上前置詞。  CLR 泛型條件約束的一般型別 \(例如，<xref:System.Int32> 和 <xref:System.String>\) 來自於 CLR 基底類別程式庫。  這些程式庫不對應至一般架構特定預設 XAML 命名空間，因此需要 XAML 使用方式的前置詞對應。  
  
 您可以使用逗號分隔符號指定多個 XAML 型別名稱。  
  
 如果泛型條件約束本身使用泛型型別，巢狀的條件約束型別引數可以由括號 \(\) 包含。  
  
 請注意，`x:TypeArguments` 的這個定義特定於 .NET Framework XAML Services 並使用 CLR 支援。  在 [\[MS XAML\] 5.3.11 節中](http://go.microsoft.com/fwlink/?LinkId=114525) \(英語\) 可找到語言層級定義。  
  
## 使用範例  
 對於這些範例，請假設已宣告下列 XAML 命名空間定義：  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### List\<String\>  
 `<scg:List x:TypeArguments="sys:String" ...>` 會以 <xref:System.String> 型別引數來執行個體化新的 <xref:System.Collections.Generic.List%601>。  
  
### Dictionary\<String,String\>  
 `<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` 會以兩個 <xref:System.String> 型別引數，來執行個體化新的 <xref:System.Collections.Generic.Dictionary%602>。  
  
### Queue\<KeyValuePair\<String,String\>\>  
 `<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` 會用內部條件約束型別引數 <xref:System.String> 和 <xref:System.String>，具現化具有 <xref:System.Collections.Generic.KeyValuePair%602> 之條件約束的新 <xref:System.Collections.Generic.Queue%601>。  
  
## XAML 2006 和 WPF 泛型 XAML 使用方式  
 對於 XAML 2006 使用方式，以及 WPF 應用程式的 XAML，一般都在 `x:TypeArguments` 和 XAML 的泛型型別使用方式存在下列限制：  
  
-   只有 XAML 檔案的根項目能夠支援參考泛型型別的泛型 XAML 使用方式。  
  
-   根項目必須對應至最少有一個型別引數的泛型型別。  <xref:System.Windows.Navigation.PageFunction%601> 即為一個範例。  頁面函式是 WPF 中 XAML 一般使用方式支援的主要案例。  
  
-   泛型型別的根項目 XAML 物件項目也必須使用 `x:Class` 來宣告部分類別。  即使定義了 WPF 建置動作，這點依然成立。  
  
-   `x:TypeArguments` 無法參考巢狀的泛型條件約束。  
  
## XAML 2009 或 XAML 2006 沒有 WPF 3.0 或 WPF 3.5 相依性  
 在 XAML 2006 或 XAML 2009 的 .NET Framework XAML 服務中，泛型 XAML 使用方式的 WPF 相關限制較為寬鬆。  您可以在支援型別系統及物件模型所能支援的 XAML 標記中的任何位置執行個體化泛型物件項目。  
  
 如果您使用 XAML 2009 而不是對應 CLR 基底類型以取得通用語言基本的 XAML 型別，可以使用[通用 XAML 語言基本型別的內建型別](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)為`typeString`中的資訊項目。  例如，您可以宣告下列項目 \(不會顯示前置詞對應，但 x 是 XAML 2009 的 XAML 語言 XAML 命名空間\)：  
  
```  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 在 WPF 中以 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 為目標時，您可以使用 XAML 2009 功能搭配 `x:TypeArguments`，但只能用於鬆散 XAML （不經過標記編譯的 XAML）。  WPF 的標記編譯 XAML 以及 XAML 的 BAML 表單目前不支援 XAML 2009 關鍵字和功能。  如果您需要以標記編譯 XAML，就必須在＜XAML 2006 和 WPF 一般 XAML 使用方式＞章節所示的限制下操作。  
  
## 請參閱  
 [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md)   
 [x:Type Markup Extension](../../../docs/framework/xaml-services/x-type-markup-extension.md)   
 [通用 XAML 語言基本型別的內建型別](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)   
 [Generics in XAML](../../../docs/framework/xaml-services/generics-in-xaml.md)
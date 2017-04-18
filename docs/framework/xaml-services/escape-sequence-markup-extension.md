---
title: "{} Escape Sequence / Markup Extension | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "{}"
helpviewer_keywords: 
  - "XAML [XAML Services], quotation mark (")"
  - "{} escape sequence [XAML Services]"
  - "XAML [XAML Services], {} escape sequence"
  - "XAML [XAML Services], escape sequence"
  - "quotation mark (") [XAML Services]"
  - "escape sequence [XAML Services]"
ms.assetid: 3ce3e2ad-a868-43f9-9c98-b29561cb146e
caps.latest.revision: 21
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
---
# {} Escape Sequence / Markup Extension
提供屬性值的 XAML 逸出序列。  逸出序列可讓屬性中的後續值解譯為常值。  
  
## XAML Attribute Usage  
  
```  
<object property="{} literalValue" .../>  
```  
  
## XAML 屬性項目用法  
  
```  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## XAML 值  
  
|||  
|-|-|  
|*literalValue*|逸出序列後面跟隨的常值字串。  這個字串通常包含左邊或右邊大括號 \({ 或 }\)。|  
  
## 備註  
 使用逸出序列 \({}\) 是要讓左邊大括號 \({\) 當做 XAML 中的常值字元使用。  
  
 XAML 讀取器通常會使用左大括號 \({\) 表示標記擴充的進入點，但是這些讀取器首先會檢查下一個字元以判斷其是否為右大括號 \(}\)。  只有當兩個大括弧 \({}\) 相鄰時，才會被視為逸出序列。  
  
 如果遇到逸出序列，XAML 讀取器應會將剩下的字串視為字串處理。  但是，如果逸出序列套用於含有類型轉換器的成員，字串依然有可能在由 XAML 寫入器解譯時，進行型別轉換子轉換。  
  
 逸出序列不是標記延伸，類別並不支援這個用法。  但是，遵從 xaml 讀取器 \(包括自訂的 XAML 讀取器\) 是慣例。  
  
 引號 \("\) 不可以這種方式作為逸出序列。  如果需要將引號設定為非內容屬性的屬性值，請使用屬性項目語法，並將引號當做字串放入屬性項目中，或者使用 XML 字元實體。  若為內容屬性，引號可當做整個內容。  
  
 當指定 XML 型別，而此型別必須在 XAML 標記延伸可能會出現的位置包含命名空間限定詞時，就經常需要使用逸出序列 \({}\)。  這包括 XAML 屬性值的開頭，以及標記延伸內緊接在等號 \(\=\) 後面的位置。  下列範例顯示出現在 XAML 屬性值開頭之 XML 命名空間的逸出序列。  
  
 [!code-xml[XLINQExample#StackPanelResources](../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## 請參閱  
 [Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)   
 [XML Character Entities and XAML](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)
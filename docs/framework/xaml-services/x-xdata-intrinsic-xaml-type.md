---
title: "x:XData Intrinsic XAML Type | Microsoft Docs"
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
  - "x:XData"
  - "XData"
  - "xXData"
helpviewer_keywords: 
  - "XAML [XAML Services], x:XData directive element"
  - "XData in XAML [XAML Services]"
  - "x:XData XAML directive element [XAML Services]"
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
caps.latest.revision: 17
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 17
---
# x:XData Intrinsic XAML Type
允許將 XML 資料島放置於 XAML 生產中。  XAML 處理器不應將 `x:XData` 中的 XML 項目作用中預設 XAML 命名空間或其他任何 XAML 命名空間的一部分。  `x:XData` 可以包含任意格式的語式正確 XML。  
  
## XAML 物件項目用法  
  
```  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## XAML 值  
  
|||  
|-|-|  
|`elementDataRoot`|封入資料島的單一根項目 \(Root Element\)。  對於大多數的最終消費者，沒有單一根的 XML 都會被視為無效。  如果 `x:XData` 適用於 WPF 的 XML 資料來源或許多其他使用 XML 來源進行資料繫結的技術，則尤其需要單一根目錄。|  
|`[elementData]`|選擇項。  代表 XML 資料的 XML。  包含的項目資料沒有數目的限制，並且巢狀項目可以包含在其他項目中，無論如何都適用 XML 的一般規則。|  
  
## 備註  
 `x:XData` 物件內的 XML 項目可以重新宣告所有可能的命名空間，以及資料內所包含 XMLDOM 的前置詞。  
  
 透過 <xref:System.Windows.Markup.XData> 類別，就可能在 .NET Framework XAML Services 中對 XML 資料和 `x:XData` 內建 XAML 型別進行程式設計的存取。  
  
## WPF 使用注意事項  
 `x:XData` 物件主要用來當做 <xref:System.Windows.Data.XmlDataProvider> 的子物件，或是當做 <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=fullName> 屬性 \(在 XAML 中，這通常會以屬性項目語法表示\) 的子物件。  
  
 資料通常會將資料島內的基底 XML 命名空間重新定義成新的預設 XML 命名空間 \(設定為空字串\)。  這是處理簡單資料島最容易的方法，因為用來參考和繫結至資料的 <xref:System.Windows.Data.Binding.XPath%2A> 運算式可以避免包含前置字元。  較為複雜的資料島可能為資料定義多個前置字元，並在根項目中使用 XML 命名空間的特定前置字元。  在這種情況下，所有的 <xref:System.Windows.Data.Binding.XPath%2A> 運算式參考都應該包含適當的命名空間對應前置字元。  如需詳細資訊，請參閱[資料繫結概觀](../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
 技術上來說，`x:XData` 可以當做型別為 <xref:System.Xml.Serialization.IXmlSerializable> 之任何屬性的內容。  然而，<xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=fullName> 是唯一的重要實作。  
  
## 請參閱  
 <xref:System.Windows.Data.XmlDataProvider>   
 [資料繫結概觀](../../../docs/framework/wpf/data/data-binding-overview.md)   
 [繫結標記延伸](../../../docs/framework/wpf/advanced/binding-markup-extension.md)
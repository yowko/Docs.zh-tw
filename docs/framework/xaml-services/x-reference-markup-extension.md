---
title: "x:Reference Markup Extension | Microsoft Docs"
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
  - "x:Reference markup extension [XAML Services]"
  - "XAML [XAML Services], x:Reference Markup Extension"
  - "Reference markup extension [XAML Services]"
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
caps.latest.revision: 8
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 8
---
# x:Reference Markup Extension
參考在 XAML 其他位置宣告的執行個體。  參考是指項目的 `x:Name`。  
  
## XAML Attribute Usage  
  
```  
<object property="{x:Reference instancexName}" .../>  
```  
  
## XAML 物件項目用法  
  
```  
<object>  
  <object.property>  
    <x:Reference Name="instancexName"/>  
  </object.property>  
</object>  
```  
  
## XAML 值  
  
|||  
|-|-|  
|`instancexName`|參考執行個體的 `x:Name`值 \(或 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 所識別之屬性的值\)。|  
  
## 備註  
 `x:Reference` 提供項目參考概念的 XAML 語言層級支援，否則這個項目參考概念就會在特定架構 \(例如 WPF\) 中實作。  
  
## x:參考和 WPF  
 在 WPF 和 XAML 2006 中，項目參考會以 <xref:System.Windows.Data.Binding.ElementName%2A> 繫結的架構層級功能定址。  針對大部分的 WPF 應用程式和案例，仍應使用 <xref:System.Windows.Data.Binding.ElementName%2A> 繫結。  這個一般指引的例外狀況可能包括下列情況：資料內容或其他範圍考量使得資料繫結不實用，以及標記編譯不相關。  
  
 `x:Reference` 是 XAML 2009 中定義的建構。  在 WPF 中，您可以使用 XAML 2009 功能，但是只能針對未進行 WPF 標記編譯的 XAML。  標記編譯 XAML 及 XAML 的 BAML 表單目前不支援 XAML 2009 語言關鍵字和功能。
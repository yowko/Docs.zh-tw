---
title: "x:Reference 標記延伸"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03b63cb40e57223d5c66c03fb60780689cd6c925
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="xreference-markup-extension"></a>x:Reference 標記延伸
會參考其他地方在 XAML 標記中宣告執行個體。 參考所參考的項目`x:Name`。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object property="{x:Reference instancexName}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>XAML 物件項目用法  
  
```xaml  
<object>  
  <object.property>  
    <x:Reference Name="instancexName"/>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`instancexName`|`x:Name`值 (或值<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-識別屬性) 的參考執行個體。|  
  
## <a name="remarks"></a>備註  
 `x:Reference`提供的項目參考概念否則實作中特定的架構，例如 WPF XAML 語言層級支援。  
  
## <a name="xreference-and-wpf"></a>X:reference 和 WPF  
 在 WPF 和 XAML 2006 中，項目參考期刊的架構層級功能<xref:System.Windows.Data.Binding.ElementName%2A>繫結。 大部分的 WPF 應用程式和案例，<xref:System.Windows.Data.Binding.ElementName%2A>仍應使用的繫結。 這個一般指引的例外狀況可能包含案例，其中有資料內容或其他範圍考量資料繫結變得不可行，而且不進行標記編譯。  
  
 `x:Reference`在 XAML 2009 中定義的建構。 在 WPF 中，您可以使用 XAML 2009 功能，但只能針對未編譯 WPF 標記的 XAML。 編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 語言關鍵字和功能。

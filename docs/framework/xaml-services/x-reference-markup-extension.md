---
title: x:Reference 標記延伸
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: 960f5c0e4192df72090c1a571dfc2fc5e3fd8ba3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938875"
---
# <a name="xreference-markup-extension"></a>x:Reference 標記延伸
在 XAML 標記中其他位置宣告的執行個體的參考。 參考所參考的項目`x:Name`。  
  
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
|`instancexName`|`x:Name`值 (或值<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-識別屬性) 的參考的執行個體。|  
  
## <a name="remarks"></a>備註  
 `x:Reference` 否則在特定的架構，例如 WPF 中實作的項目參考概念提供 XAML 語言層級支援。  
  
## <a name="xreference-and-wpf"></a>x： 參考和 WPF  
 在 WPF 和 XAML 2006 中，項目參考會定址的架構層級功能<xref:System.Windows.Data.Binding.ElementName%2A>繫結。 大部分的 WPF 應用程式和案例，<xref:System.Windows.Data.Binding.ElementName%2A>仍應使用繫結。 這個一般的指導方針的例外狀況可能包含的情況下，有資料內容或其他範圍的考量，讓資料繫結並不實用，而且不進行標記編譯。  
  
 `x:Reference` XAML 2009 中定義的建構。 在 WPF 中，您可以使用 XAML 2009 功能，但只能針對未編譯 WPF 標記的 XAML。 編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 語言關鍵字和功能。

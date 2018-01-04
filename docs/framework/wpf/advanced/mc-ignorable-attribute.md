---
title: "mc:Ignorable 屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mc XML namespace prefix [WPF]
- mc:Ignorable attribute
- XML [WPF], mc namespace prefix
- XAML [WPF], mc:Ignorable attribute
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: acd9a6ef-b7ca-4146-abb6-60f3b366e9ec
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9767b721321b34030a2f276a90c618c658645207
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="mcignorable-attribute"></a>mc:Ignorable 屬性
指定哪一個[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]標記檔案中遇到的命名空間前置詞可能會略過[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器。 `mc:Ignorable`屬性支援標記相容性，適用於自訂的命名空間對應和[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]版本控制。  
  
## <a name="xaml-attribute-usage-single-prefix"></a>XAML 屬性使用方式 （單一前置詞）  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a>XAML 屬性使用方式 （兩個前置詞）  
  
```  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|*ignorablePrefix ignorablePrefix1、 等等。*|任何有效的前置詞字串，根據 XML 1.0 規格。|  
|*ignorableUri*|指定命名空間，根據 XML 1.0 規格的任何有效的 URI。|  
|*ThisElementCanBeIgnored*|項目，可以忽略[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]處理器實作中，如果無法解析的基礎類型。|  
  
## <a name="remarks"></a>備註  
 `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]命名空間前置詞是用來對應時的建議前置詞慣例[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]相容性命名空間[!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)]。  
  
 項目或屬性的項目名稱的前置詞部分會識別為`mc:Ignorable`將不會引發錯誤時處理[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器。 如果該屬性無法解析至基礎類型或程式設計建構，則會忽略該元素。 不過請注意略過的項目仍可能會產生副作用的未處理該元素的其他項目需求的其他剖析錯誤。 比方說，特定項目內容的模型可能需要一個子元素，但如果指定的子項目已在`mc:Ignorable`前置詞和指定的子項目無法解析型別，則[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器可能引發錯誤。  
  
 `mc:Ignorable`僅適用於命名空間對應的識別碼字串。 `mc:Ignorable`不適用於命名空間的對應為組件，指定[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]命名空間和組件 （或在目前的組件的可執行檔的預設值）。  
  
 如果您實作[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器，處理器實作必須不會引發剖析或處理的任何元素或屬性的識別做為前置詞限定的型別解析錯誤`mc:Ignorable`。 但您的處理器實作仍然可以引發是項目無法載入或處理，例如稍早指定的其中一個子元素範例的第二個結果的例外狀況。  
  
 根據預設，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器將會忽略忽略項目內的內容。 不過，您可以指定一個額外的屬性[mc:ProcessContent 屬性](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md)、 為需要繼續的處理的下一個可用的父元素所忽略項目內的內容。  
  
 中的屬性，做為分隔符號，例如使用一或多個空格字元，可以指定多個前置詞： `mc:Ignorable="ignore1 ignore2"`。  
  
 [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)]命名空間會定義其他的項目和屬性的這個區域中未記載之[!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]。 如需詳細資訊，請參閱[XML 標記相容性規格](http://go.microsoft.com/fwlink/?LinkId=73824)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Markup.XamlReader>  
 [PresentationOptions:Freeze 屬性](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)  
 [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)

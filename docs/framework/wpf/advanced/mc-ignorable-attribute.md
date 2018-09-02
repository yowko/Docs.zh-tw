---
title: mc:Ignorable 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- mc XML namespace prefix [WPF]
- mc:Ignorable attribute
- XML [WPF], mc namespace prefix
- XAML [WPF], mc:Ignorable attribute
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: acd9a6ef-b7ca-4146-abb6-60f3b366e9ec
ms.openlocfilehash: e8fa4c084ae9c775a18de06c344b2c0b439c2b1b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467811"
---
# <a name="mcignorable-attribute"></a>mc:Ignorable 屬性
指定哪些[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]標記檔案中遇到的命名空間前置詞可能會忽略[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器。 `mc:Ignorable`屬性支援標記相容性，以及自訂的命名空間對應性[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]版本控制。  
  
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
|*ignorableUri*|對指定的命名空間，根據 XML 1.0 規格任何有效的 URI。|  
|*ThisElementCanBeIgnored*|項目，可以忽略[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]處理器實作中，如果無法解析的基礎類型。|  
  
## <a name="remarks"></a>備註  
 `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]命名空間前置詞會使用對應時的建議前置詞慣例[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]相容性命名空間[!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)]。  
  
 項目或屬性的項目名稱的前置詞部分會識別為`mc:Ignorable`將不會引發錯誤時由處理[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器。 如果該屬性不可以解析為基礎的型別或程式設計建構，則會忽略該元素。 不過請注意，已忽略的項目可能還是會產生副作用不處理該項目的的其他項目需求的其他剖析錯誤。 例如，特定項目內容的模型可能需要只有一個子項目，但指定的子項目是否在`mc:Ignorable`前置詞和指定的子項目無法解析型別，則[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器可能引發錯誤。  
  
 `mc:Ignorable` 僅適用於命名空間對應到識別項字串。 `mc:Ignorable` 不會套用到命名空間對應至組件，指定[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]命名空間和組件 （或與組件的目前可執行檔的預設值）。  
  
 如果您要實作[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器，處理器實作必須引發剖析或處理的任何項目或屬性，以識別為前置詞來限定的型別解析錯誤`mc:Ignorable`。 但您的處理器實作仍會引發例外狀況是次要的項目，無法載入或處理，如稍早指定的其中一個子元素範例的結果。  
  
 根據預設，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器將會忽略已忽略的項目內的內容。 不過，您可以指定一個額外的屬性[mc: processcontent 屬性](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md)，需要繼續的處理下一個可用的父元素所忽略的元素內的內容。  
  
 可以指定多個前置詞，在屬性中，使用一或多個空格字元作為分隔符號，例如： `mc:Ignorable="ignore1 ignore2"`。  

 [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)]命名空間會定義其他項目和屬性的這個區域中未記載之[!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]。 如需詳細資訊，請參閱 < [XML 標記相容性規格](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Markup.XamlReader>  
 [PresentationOptions:Freeze 屬性](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)  
 [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)

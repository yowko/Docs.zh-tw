---
title: mc:ProcessContent 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: f7db71c065a04fb14216ffd08ca3b7c9d7cdf5af
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54673955"
---
# <a name="mcprocesscontent-attribute"></a>mc:ProcessContent 屬性
指定哪些[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]項目仍有其內容相關的父項目處理，即使的直屬父項目可能會忽略[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]因為指定的處理器[mc: Ignorable 屬性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md). `mc:ProcessContent`屬性支援標記相容性，以及自訂的命名空間對應性[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]版本控制。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...  
  mc:ProcessContent="ignorablePrefix:ThisElementCanBeIgnored"  
>  
    <ignorablePrefix:ThisElementCanBeIgnored>  
        [content]  
    </ignorablePrefix:ThisElementCanBeIgnored>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|*ignorablePrefix*|任何有效的前置詞字串，根據 XML 1.0 規格。|  
|*ignorableUri*|對指定的命名空間，根據 XML 1.0 規格任何有效的 URI。|  
|*ThisElementCanBeIgnored*|項目，可以忽略[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]處理器實作中，如果無法解析的基礎類型。|  
|*[content]*|*ThisElementCanBeIgnored*標示為可忽略。 如果處理器就會忽略該元素， *[內容]* 處理*物件*。|  
  
## <a name="remarks"></a>備註  
 根據預設，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器將會忽略已忽略的項目內的內容。 您可以指定特定的項目依`mc:ProcessContent`，和[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器會繼續處理忽略的元素內的內容。 此外，這通常會用如果內容巢狀內至少其中之一就是可忽略和至少一個不是可忽略的數個標記。  
  
 多個前置詞可指定在屬性中，以空格分隔符號，例如： `mc:ProcessContent="ignore:Element1 ignore:Element2"`。  
  
 [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)]命名空間會定義其他項目和屬性的這個區域中未記載之[!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]。 如需詳細資訊，請參閱 < [XML 標記相容性規格](https://go.microsoft.com/fwlink/?LinkId=73824)。  
  
## <a name="see-also"></a>另請參閱
- [mc:Ignorable 屬性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)
- [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)

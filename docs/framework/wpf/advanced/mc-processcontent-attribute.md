---
title: mc:ProcessContent 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: 619c3ffbc68c8c72ea9dd6545ab8da536380483b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206178"
---
# <a name="mcprocesscontent-attribute"></a>mc:ProcessContent 屬性
指定即使[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]因為指定[mc:](mc-ignorable-attribute.md)可忽略的屬性, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器可能會忽略直屬父項目, 哪些專案仍應具有相關的父元素所處理的內容。 屬性支援自訂命名空間對應[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]和版本設定的標記相容性。 `mc:ProcessContent`  
  
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
|*ignorablePrefix*|任何有效的前置字串, 依據 XML 1.0 規格。|  
|*ignorableUri*|根據 XML 1.0 規格, 指定命名空間的任何有效 URI。|  
|*ThisElementCanBeIgnored*|如果無法解析基礎類型, 則[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]處理器執行可以忽略的元素。|  
|*[content]*|*ThisElementCanBeIgnored*會標示為可忽略。 如果處理器忽略該元素, *[content]* 就會由*物件*處理。|  
  
## <a name="remarks"></a>備註  
 根據預設, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器會忽略忽略之元素內的內容。 您可以藉由`mc:ProcessContent`指定特定元素, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]而處理器會繼續處理忽略專案中的內容。 如果內容是在數個標記中嵌套, 通常會使用此方法, 其中至少有一個是可忽略的, 而且至少有一個無法忽略。  
  
 在屬性中, 您可以使用空格分隔符號來指定多個前置詞, 例如`mc:ProcessContent="ignore:Element1 ignore:Element2"`:。  
  
 `http://schemas.openxmlformats.org/markup-compatibility/2006`命名空間會定義在 SDK 的這個區域中未記載的其他元素和屬性。 如需詳細資訊, 請參閱[XML 標記相容性規格](https://go.microsoft.com/fwlink/?LinkId=73824)。  
  
## <a name="see-also"></a>另請參閱

- [mc:Ignorable 屬性](mc-ignorable-attribute.md)
- [XAML 概觀 (WPF)](xaml-overview-wpf.md)

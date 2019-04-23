---
title: PresentationOptions:Freeze 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
ms.openlocfilehash: e60c4a505db42936f188354f52edd7832fb9632b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074653"
---
# <a name="presentationoptionsfreeze-attribute"></a>PresentationOptions:Freeze 屬性
設定組<xref:System.Windows.Freezable.IsFrozen%2A>狀態`true`上包含<xref:System.Windows.Freezable>項目。 預設行為<xref:System.Windows.Freezable>而不需要`PresentationOptions:Freeze`指定的屬性是<xref:System.Windows.Freezable.IsFrozen%2A>是`false`在載入時間和在一般的相依<xref:System.Windows.Freezable>在執行階段的行為。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```  
<object  
  xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="PresentationOptions">  
    <freezableElement PresentationOptions:Freeze="true"/>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`PresentationOptions`|XML 命名空間前置詞，它可以是任何有效的前置詞字串，根據 XML 1.0 規格。 前置詞`PresentationOptions`用做為識別用途，此文件中。|  
|`freezableElement`|具現化任何項目衍生的類別<xref:System.Windows.Freezable>。|  
  
## <a name="remarks"></a>備註  
 `Freeze`屬性是唯一的屬性或其他程式設計項目定義在`http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`XML 命名空間。 `Freeze`屬性存在這個特殊的命名空間中，好讓它可以為忽略，使用指定特別[mc: Ignorable 屬性](mc-ignorable-attribute.md)做為根項目宣告的一部分。 原因，`Freeze`必須是能夠忽略因為不是所有[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器實作都能 freeze<xref:System.Windows.Freezable>在載入時，這項功能不屬於[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]規格。  
  
 處理能力`Freeze`屬性特別是內建[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器處理[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]編譯的應用程式。 任何類別中，不支援的屬性和屬性語法不是可延伸或修改。 如果您要實作您自己[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]您可以選擇平行的凍結行為的處理器[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器在處理時`Freeze`屬性<xref:System.Windows.Freezable>在載入時間的項目。  
  
 任何值`Freeze`以外的其他屬性`true`（不區分大小寫） 會產生載入時間錯誤。 (指定`Freeze`屬性為`false`不是錯誤，但這已經預設值，因此將設定為`false`不執行任何動作)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Freezable>
- [Freezable 物件概觀](freezable-objects-overview.md)
- [mc:Ignorable 屬性](mc-ignorable-attribute.md)

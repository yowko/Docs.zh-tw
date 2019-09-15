---
title: PresentationOptions:Freeze 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
ms.openlocfilehash: d3e0cee293a9585b972b0145da953976ed94b74c
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991432"
---
# <a name="presentationoptionsfreeze-attribute"></a>PresentationOptions:Freeze 屬性
將狀態設定為`true`包含<xref:System.Windows.Freezable>專案上的。 <xref:System.Windows.Freezable.IsFrozen%2A> 未指定<xref:System.Windows.Freezable> `PresentationOptions:Freeze` 屬性之<xref:System.Windows.Freezable.IsFrozen%2A>的預設行為是<xref:System.Windows.Freezable>在載入時，並取決於執行時間的一般行為。 `false`  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
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
|`PresentationOptions`|XML 命名空間前置詞，可以是任何有效的前置字串，依據 XML 1.0 規格。 在本`PresentationOptions`檔中，此前置詞是用於識別用途。|  
|`freezableElement`|具現化之<xref:System.Windows.Freezable>任何衍生類別的元素。|  
  
## <a name="remarks"></a>備註  
 屬性是`http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` XML 命名空間中定義的唯一屬性或其他程式設計項目。 `Freeze` 屬性會特別存在於這個特殊的命名空間中，以便將其指定為可忽略，並使用[mc：可忽略的屬性](mc-ignorable-attribute.md)做為根項目宣告的一部分。 `Freeze` `Freeze`必須能夠忽略的原因是因為並非所有[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器的執行<xref:System.Windows.Freezable>都能夠在載入時凍結，這項[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]功能不是規格的一部分。  
  
 處理`Freeze`屬性的能力，特別是內建[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]于處理[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]已編譯應用程式的處理器。 任何類別都不支援屬性，而且屬性語法不可延伸或可修改。 如果您要執行[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]自己的處理器，您可以在載入時，選擇平行處理[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] `Freeze`專案的屬性[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] （attribute <xref:System.Windows.Freezable> ）。  
  
 除了`true` （不區分`Freeze`大小寫）以外的任何屬性值，都會產生載入時間錯誤。 （將`Freeze`屬性指定為`false`不是錯誤，但已是預設值，因此設定為`false`不執行任何動作）。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Freezable>
- [Freezable 物件概觀](freezable-objects-overview.md)
- [mc:Ignorable 屬性](mc-ignorable-attribute.md)

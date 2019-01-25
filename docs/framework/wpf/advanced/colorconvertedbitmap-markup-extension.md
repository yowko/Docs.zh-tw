---
title: ColorConvertedBitmap 標記延伸
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
ms.openlocfilehash: 4f71b90fa00d1aaee0ec5ad43e5a19be03c79c50
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54647643"
---
# <a name="colorconvertedbitmap-markup-extension"></a>ColorConvertedBitmap 標記延伸
提供方法來指定沒有內嵌設定檔的點陣圖來源。 色彩內容 / 設定檔由[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]，因為映像來源[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" .../>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`imageSource`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]藉點陣圖。|  
|`sourceIIC`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]來源的設定檔設定。|  
|`destinationIIC`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]的目的地設定檔設定|  
  
## <a name="remarks"></a>備註  
 這個標記延伸要填入一組相關的映像來源的屬性值，例如<xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>。  
  
 屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。 `ColorConvertedBitmap` (或`ColorConvertedBitmapExtension`) 不能在屬性項目語法中，因為值只能做為值設定初始建構函式，也就是字串後面的延伸模組識別碼。  
  
 `ColorConvertedBitmap` 是一種標記延伸。 如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。 如需詳細資訊，請參閱[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>
- [標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [影像處理概觀](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)

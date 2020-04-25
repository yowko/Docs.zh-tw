---
title: ColorConvertedBitmap 標記延伸
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
ms.openlocfilehash: a5b491723a036c1b1fd0bb61736e6f2ee53fbcd3
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141219"
---
# <a name="colorconvertedbitmap-markup-extension"></a>ColorConvertedBitmap 標記延伸
提供方法來指定沒有內嵌設定檔的點陣圖來源。 色彩內容/設定檔是由 URI 指定，如同映射來源 URI。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" ... />
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`imageSource`|Nonprofiled 點陣圖的 URI。|  
|`sourceIIC`|來源設定檔設定的 URI。|  
|`destinationIIC`|目的地設定檔設定的 URI|  
  
## <a name="remarks"></a>備註  
 此標記延伸的目的是要填入一組相關的影像來源屬性值，例如<xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>。  
  
 屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。 `ColorConvertedBitmap`（或`ColorConvertedBitmapExtension`）無法在屬性專案語法中使用，因為這些值只能設定為初始函式上的值，這是延伸模組識別碼後面的字串。  
  
 `ColorConvertedBitmap` 是一種標記延伸。 如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。 如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>
- [標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)
- [影像處理概觀](../graphics-multimedia/imaging-overview.md)

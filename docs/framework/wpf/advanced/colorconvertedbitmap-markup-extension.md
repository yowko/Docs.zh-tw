---
title: ColorConvertedBitmap 標記延伸
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
ms.openlocfilehash: 9b39e30cbe4e0bedc88c859f013b4d7175f7eb1a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538906"
---
# <a name="colorconvertedbitmap-markup-extension"></a><span data-ttu-id="75bbd-102">ColorConvertedBitmap 標記延伸</span><span class="sxs-lookup"><span data-stu-id="75bbd-102">ColorConvertedBitmap Markup Extension</span></span>
<span data-ttu-id="75bbd-103">提供方法來指定沒有內嵌的設定檔的點陣圖來源。</span><span class="sxs-lookup"><span data-stu-id="75bbd-103">Provides a way to specify a bitmap source that does not have an embedded profile.</span></span> <span data-ttu-id="75bbd-104">色彩內容所指定設定檔 / [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]，如映像來源[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="75bbd-104">Color contexts / profiles are specified by [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], as is the image source [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="75bbd-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="75bbd-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="75bbd-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="75bbd-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`imageSource`|<span data-ttu-id="75bbd-107">[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Nonprofiled 點陣圖。</span><span class="sxs-lookup"><span data-stu-id="75bbd-107">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] of the nonprofiled bitmap.</span></span>|  
|`sourceIIC`|<span data-ttu-id="75bbd-108">[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]來源的設定檔設定。</span><span class="sxs-lookup"><span data-stu-id="75bbd-108">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] of the source profile configuration.</span></span>|  
|`destinationIIC`|<span data-ttu-id="75bbd-109">[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]的目的地設定檔設定</span><span class="sxs-lookup"><span data-stu-id="75bbd-109">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] of the destination profile configuration</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75bbd-110">備註</span><span class="sxs-lookup"><span data-stu-id="75bbd-110">Remarks</span></span>  
 <span data-ttu-id="75bbd-111">這個標記延伸要填滿一組相關的映像來源 」 屬性值時，例如<xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>。</span><span class="sxs-lookup"><span data-stu-id="75bbd-111">This markup extension is intended to fill a related set of image-source property values such as <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.</span></span>  
  
 <span data-ttu-id="75bbd-112">屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。</span><span class="sxs-lookup"><span data-stu-id="75bbd-112">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="75bbd-113">`ColorConvertedBitmap` (或`ColorConvertedBitmapExtension`) 不能在屬性項目語法，因為這些值只能做為值設定在初始建構函式，也就是字串下列延伸模組識別項。</span><span class="sxs-lookup"><span data-stu-id="75bbd-113">`ColorConvertedBitmap` (or `ColorConvertedBitmapExtension`) cannot be used in property element syntax, because the values can only be set as values on the initial constructor, which is the string following the extension identifier.</span></span>  
  
 <span data-ttu-id="75bbd-114">`ColorConvertedBitmap` 是一種標記延伸。</span><span class="sxs-lookup"><span data-stu-id="75bbd-114">`ColorConvertedBitmap` is a markup extension.</span></span> <span data-ttu-id="75bbd-115">如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。</span><span class="sxs-lookup"><span data-stu-id="75bbd-115">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="75bbd-116">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。</span><span class="sxs-lookup"><span data-stu-id="75bbd-116">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="75bbd-117">如需詳細資訊，請參閱[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="75bbd-117">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75bbd-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75bbd-118">See Also</span></span>  
 <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>  
 [<span data-ttu-id="75bbd-119">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="75bbd-119">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="75bbd-120">影像處理概觀</span><span class="sxs-lookup"><span data-stu-id="75bbd-120">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)

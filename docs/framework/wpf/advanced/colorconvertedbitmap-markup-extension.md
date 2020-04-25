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
# <a name="colorconvertedbitmap-markup-extension"></a><span data-ttu-id="42bc7-102">ColorConvertedBitmap 標記延伸</span><span class="sxs-lookup"><span data-stu-id="42bc7-102">ColorConvertedBitmap Markup Extension</span></span>
<span data-ttu-id="42bc7-103">提供方法來指定沒有內嵌設定檔的點陣圖來源。</span><span class="sxs-lookup"><span data-stu-id="42bc7-103">Provides a way to specify a bitmap source that does not have an embedded profile.</span></span> <span data-ttu-id="42bc7-104">色彩內容/設定檔是由 URI 指定，如同映射來源 URI。</span><span class="sxs-lookup"><span data-stu-id="42bc7-104">Color contexts / profiles are specified by URI, as is the image source URI.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="42bc7-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="42bc7-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" ... />
```  
  
## <a name="xaml-values"></a><span data-ttu-id="42bc7-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="42bc7-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`imageSource`|<span data-ttu-id="42bc7-107">Nonprofiled 點陣圖的 URI。</span><span class="sxs-lookup"><span data-stu-id="42bc7-107">The URI of the nonprofiled bitmap.</span></span>|  
|`sourceIIC`|<span data-ttu-id="42bc7-108">來源設定檔設定的 URI。</span><span class="sxs-lookup"><span data-stu-id="42bc7-108">The URI of the source profile configuration.</span></span>|  
|`destinationIIC`|<span data-ttu-id="42bc7-109">目的地設定檔設定的 URI</span><span class="sxs-lookup"><span data-stu-id="42bc7-109">The URI of the destination profile configuration</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42bc7-110">備註</span><span class="sxs-lookup"><span data-stu-id="42bc7-110">Remarks</span></span>  
 <span data-ttu-id="42bc7-111">此標記延伸的目的是要填入一組相關的影像來源屬性值，例如<xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>。</span><span class="sxs-lookup"><span data-stu-id="42bc7-111">This markup extension is intended to fill a related set of image-source property values such as <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.</span></span>  
  
 <span data-ttu-id="42bc7-112">屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。</span><span class="sxs-lookup"><span data-stu-id="42bc7-112">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="42bc7-113">`ColorConvertedBitmap`（或`ColorConvertedBitmapExtension`）無法在屬性專案語法中使用，因為這些值只能設定為初始函式上的值，這是延伸模組識別碼後面的字串。</span><span class="sxs-lookup"><span data-stu-id="42bc7-113">`ColorConvertedBitmap` (or `ColorConvertedBitmapExtension`) cannot be used in property element syntax, because the values can only be set as values on the initial constructor, which is the string following the extension identifier.</span></span>  
  
 <span data-ttu-id="42bc7-114">`ColorConvertedBitmap` 是一種標記延伸。</span><span class="sxs-lookup"><span data-stu-id="42bc7-114">`ColorConvertedBitmap` is a markup extension.</span></span> <span data-ttu-id="42bc7-115">如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。</span><span class="sxs-lookup"><span data-stu-id="42bc7-115">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="42bc7-116">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。</span><span class="sxs-lookup"><span data-stu-id="42bc7-116">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="42bc7-117">如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="42bc7-117">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42bc7-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42bc7-118">See also</span></span>

- <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>
- [<span data-ttu-id="42bc7-119">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="42bc7-119">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="42bc7-120">影像處理概觀</span><span class="sxs-lookup"><span data-stu-id="42bc7-120">Imaging Overview</span></span>](../graphics-multimedia/imaging-overview.md)

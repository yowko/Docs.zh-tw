---
title: HOW TO：使用 SystemFonts
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- system fonts [WPF]
- fonts [WPF], system fonts
- classes [WPF], SystemFonts
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
ms.openlocfilehash: 7438705a82faee464649b5f6f577627a379e9a8c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918355"
---
# <a name="how-to-use-systemfonts"></a><span data-ttu-id="cca7c-102">作法：使用 SystemFonts</span><span class="sxs-lookup"><span data-stu-id="cca7c-102">How to: Use SystemFonts</span></span>
<span data-ttu-id="cca7c-103">這個範例示範如何使用<xref:System.Windows.SystemFonts>類別的靜態資源, 以樣式或自訂按鈕。</span><span class="sxs-lookup"><span data-stu-id="cca7c-103">This example shows how to use the static resources of the <xref:System.Windows.SystemFonts> class in order to style or customize a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cca7c-104">範例</span><span class="sxs-lookup"><span data-stu-id="cca7c-104">Example</span></span>  
 <span data-ttu-id="cca7c-105">系統資源會將數個系統判斷的值同時公開為資源和屬性，協助您建立與系統設定一致的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="cca7c-105">System resources expose several system-determined values as both resources and properties in order to help you create visuals that are consistent with system settings.</span></span> <span data-ttu-id="cca7c-106"><xref:System.Windows.SystemFonts>是一個類別, 其中同時包含系統字型值做為靜態屬性, 以及參考資源索引鍵的屬性, 可在執行時間以動態方式存取這些值。</span><span class="sxs-lookup"><span data-stu-id="cca7c-106"><xref:System.Windows.SystemFonts> is a class that contains both system font values as static properties, and properties that reference resource keys that can be used to access those values dynamically at run time.</span></span> <span data-ttu-id="cca7c-107">例如, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> <xref:System.Windows.SystemFonts>是值, 而<xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>是對應的資源索引鍵。</span><span class="sxs-lookup"><span data-stu-id="cca7c-107">For example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> is a <xref:System.Windows.SystemFonts> value, and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> is a corresponding resource key.</span></span>  
  
 <span data-ttu-id="cca7c-108">在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中, 您可以使用的<xref:System.Windows.SystemFonts>成員做為靜態屬性或動態資源參考 (具有靜態屬性值做為索引鍵)。</span><span class="sxs-lookup"><span data-stu-id="cca7c-108">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can use the members of <xref:System.Windows.SystemFonts> as either static properties or dynamic resource references (with the static property value as the key).</span></span> <span data-ttu-id="cca7c-109">如果您想要在應用程式執行時自動更新字型度量資訊，請使用動態資源參考；否則請使用靜態值參考。</span><span class="sxs-lookup"><span data-stu-id="cca7c-109">Use a dynamic resource reference if you want the font metric to automatically update while the application runs; otherwise, use a static value reference.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cca7c-110">資源索引鍵會將後置字元 "Key" 附加至屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="cca7c-110">The resource keys have the suffix "Key" appended to the property name.</span></span>  
  
 <span data-ttu-id="cca7c-111">下列範例示範如何存取和使用的屬性<xref:System.Windows.SystemFonts>做為靜態值, 以進行樣式或自訂按鈕。</span><span class="sxs-lookup"><span data-stu-id="cca7c-111">The following example shows how to access and use the properties of <xref:System.Windows.SystemFonts> as static values in order to style or customize a button.</span></span> <span data-ttu-id="cca7c-112">此標記範例會<xref:System.Windows.SystemFonts>將值指派給按鈕。</span><span class="sxs-lookup"><span data-stu-id="cca7c-112">This markup example assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 <span data-ttu-id="cca7c-113">若要<xref:System.Windows.SystemFonts>在程式碼中使用的值, 您不需要使用靜態值或動態資源參考。</span><span class="sxs-lookup"><span data-stu-id="cca7c-113">To use the values of <xref:System.Windows.SystemFonts> in code, you do not have to use either a static value or a dynamic resource reference.</span></span> <span data-ttu-id="cca7c-114">相反地, 請使用<xref:System.Windows.SystemFonts>類別的非索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="cca7c-114">Instead, use the non-key properties of the <xref:System.Windows.SystemFonts> class.</span></span> <span data-ttu-id="cca7c-115">雖然非索引鍵屬性已明顯定義為靜態屬性, 但由系統裝載之[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的執行時間行為會即時重新評估屬性, 並適當地將使用者驅動的系統值變更加以考慮。</span><span class="sxs-lookup"><span data-stu-id="cca7c-115">Although the non-key properties are apparently defined as static properties, the run-time behavior of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as hosted by the system will reevaluate the properties in real time and will properly account for user-driven changes to system values.</span></span> <span data-ttu-id="cca7c-116">下列範例示範如何指定按鈕的字型設定。</span><span class="sxs-lookup"><span data-stu-id="cca7c-116">The following example shows how to specify the font settings of a button.</span></span>  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a><span data-ttu-id="cca7c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cca7c-117">See also</span></span>

- <xref:System.Windows.SystemFonts>
- [<span data-ttu-id="cca7c-118">使用系統筆刷繪製區域</span><span class="sxs-lookup"><span data-stu-id="cca7c-118">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="cca7c-119">使用 SystemParameters</span><span class="sxs-lookup"><span data-stu-id="cca7c-119">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
- [<span data-ttu-id="cca7c-120">使用系統字型索引鍵</span><span class="sxs-lookup"><span data-stu-id="cca7c-120">Use System Fonts Keys</span></span>](how-to-use-system-fonts-keys.md)
- [<span data-ttu-id="cca7c-121">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="cca7c-121">How-to Topics</span></span>](resources-how-to-topics.md)
- [<span data-ttu-id="cca7c-122">x:Static 標記延伸</span><span class="sxs-lookup"><span data-stu-id="cca7c-122">x:Static Markup Extension</span></span>](../../xaml-services/x-static-markup-extension.md)
- [<span data-ttu-id="cca7c-123">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="cca7c-123">XAML Resources</span></span>](xaml-resources.md)
- [<span data-ttu-id="cca7c-124">DynamicResource 標記延伸</span><span class="sxs-lookup"><span data-stu-id="cca7c-124">DynamicResource Markup Extension</span></span>](dynamicresource-markup-extension.md)

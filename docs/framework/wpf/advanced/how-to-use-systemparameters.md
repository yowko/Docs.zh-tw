---
title: 如何：使用 SystemParameters
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], SystemParameters
ms.assetid: 02e7a5de-94eb-4953-b91c-52e6c872ad5b
ms.openlocfilehash: 07b73d78a022e508f9ed8ca2e80b71bc2ab89910
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544631"
---
# <a name="how-to-use-systemparameters"></a><span data-ttu-id="5e591-102">如何：使用 SystemParameters</span><span class="sxs-lookup"><span data-stu-id="5e591-102">How to: Use SystemParameters</span></span>
<span data-ttu-id="5e591-103">這個範例示範如何存取和使用的屬性<xref:System.Windows.SystemParameters>才能設定或自訂按鈕的樣式。</span><span class="sxs-lookup"><span data-stu-id="5e591-103">This example shows how to access and use the properties of <xref:System.Windows.SystemParameters> in order to style or customize a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e591-104">範例</span><span class="sxs-lookup"><span data-stu-id="5e591-104">Example</span></span>  
 <span data-ttu-id="5e591-105">系統資源會將數個系統設定公開為資源，協助您建立與系統設定一致的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="5e591-105">System resources expose several system based settings as resources in order to help you create visuals that are consistent with system settings.</span></span> <span data-ttu-id="5e591-106"><xref:System.Windows.SystemParameters> 是類別，其中包含系統參數值的屬性，並繫結到值的資源索引鍵。</span><span class="sxs-lookup"><span data-stu-id="5e591-106"><xref:System.Windows.SystemParameters> is a class that contains both system parameter value properties, and resource keys that bind to the values.</span></span> <span data-ttu-id="5e591-107">例如，<xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A>是<xref:System.Windows.SystemParameters>屬性值和<xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>是對應的資源索引鍵。</span><span class="sxs-lookup"><span data-stu-id="5e591-107">For example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> is a <xref:System.Windows.SystemParameters> property value and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> is the corresponding resource key.</span></span>  
  
 <span data-ttu-id="5e591-108">在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您可以使用的成員<xref:System.Windows.SystemParameters>為靜態屬性使用方式或動態資源參考 （具有靜態屬性的值，做為索引鍵）。</span><span class="sxs-lookup"><span data-stu-id="5e591-108">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can use the members of <xref:System.Windows.SystemParameters> as either a static property usage, or a dynamic resource references (with the static property value as the key).</span></span> <span data-ttu-id="5e591-109">如果您想要在應用程式執行時自動更新系統值，請使用動態資源參考；否則請使用靜態參考。</span><span class="sxs-lookup"><span data-stu-id="5e591-109">Use a dynamic resource reference if you want the system based value to update automatically while the application runs; otherwise, use a static reference.</span></span> <span data-ttu-id="5e591-110">資源的索引鍵具有後置詞`Key`附加至屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="5e591-110">Resource keys have the suffix `Key` appended to the property name.</span></span>  
  
 <span data-ttu-id="5e591-111">下列範例示範如何存取和使用的靜態值<xref:System.Windows.SystemParameters>以設定或自訂按鈕的樣式。</span><span class="sxs-lookup"><span data-stu-id="5e591-111">The following example shows how to access and use the static values of <xref:System.Windows.SystemParameters> to style or customize a button.</span></span> <span data-ttu-id="5e591-112">此標記範例藉由套用大小按鈕<xref:System.Windows.SystemParameters>按鈕的值。</span><span class="sxs-lookup"><span data-stu-id="5e591-112">This markup example sizes a button by applying <xref:System.Windows.SystemParameters> values to a button.</span></span>  
  
 [!code-xaml[SystemRes_snip#ParameterStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#parameterstaticresources)]  
  
 <span data-ttu-id="5e591-113">若要使用的值<xref:System.Windows.SystemParameters>程式碼中，您不需要使用靜態參考或動態資源參考。</span><span class="sxs-lookup"><span data-stu-id="5e591-113">To use the values of <xref:System.Windows.SystemParameters> in code, you do not have to use either static references or dynamic resource references.</span></span> <span data-ttu-id="5e591-114">相反地，使用的值<xref:System.Windows.SystemParameters>類別。</span><span class="sxs-lookup"><span data-stu-id="5e591-114">Instead, use the values of the <xref:System.Windows.SystemParameters> class.</span></span> <span data-ttu-id="5e591-115">雖然非索引鍵屬性明顯定義為靜態屬性的執行階段行為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]裝載系統將會重新評估屬性即時，並會適當地將使用者導向的系統值變更。</span><span class="sxs-lookup"><span data-stu-id="5e591-115">Although the non-key properties are apparently defined as static properties, the runtime behavior of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as hosted by the system will reevaluate the properties in realtime, and will properly account for user-driven changes to system values.</span></span> <span data-ttu-id="5e591-116">下列範例示範如何使用設定按鈕的高度與寬度<xref:System.Windows.SystemParameters>值。</span><span class="sxs-lookup"><span data-stu-id="5e591-116">The following example shows how to set the width and height of a button by using <xref:System.Windows.SystemParameters> values.</span></span>  
  
 [!code-csharp[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#parameterresourcescode)]
 [!code-vb[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#parameterresourcescode)]  
  
## <a name="see-also"></a><span data-ttu-id="5e591-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e591-117">See Also</span></span>  
 <xref:System.Windows.SystemParameters>  
 [<span data-ttu-id="5e591-118">使用系統筆刷繪製區域</span><span class="sxs-lookup"><span data-stu-id="5e591-118">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="5e591-119">使用 SystemFonts</span><span class="sxs-lookup"><span data-stu-id="5e591-119">Use SystemFonts</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [<span data-ttu-id="5e591-120">使用系統參數索引鍵</span><span class="sxs-lookup"><span data-stu-id="5e591-120">Use System Parameters Keys</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-system-parameters-keys.md)  
 [<span data-ttu-id="5e591-121">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="5e591-121">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)

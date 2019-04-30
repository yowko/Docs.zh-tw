---
title: HOW TO：使用系統參數索引鍵
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
ms.openlocfilehash: 147f65b4bb214c12317309081c345251d7426cd6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001438"
---
# <a name="how-to-use-system-parameters-keys"></a><span data-ttu-id="fc5cd-102">HOW TO：使用系統參數索引鍵</span><span class="sxs-lookup"><span data-stu-id="fc5cd-102">How to: Use System Parameters Keys</span></span>
<span data-ttu-id="fc5cd-103">系統資源會將數個系統度量資訊公開為資源，協助開發人員建立與系統設定一致的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="fc5cd-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="fc5cd-104"><xref:System.Windows.SystemParameters> 是包含系統參數值以及繫結至值的資源索引鍵的類別，例如<xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A>和<xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>。</span><span class="sxs-lookup"><span data-stu-id="fc5cd-104"><xref:System.Windows.SystemParameters> is a class that contains both system parameter values and resource keys that bind to the values—for example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span></span> <span data-ttu-id="fc5cd-105">系統參數度量資訊可以當成靜態或動態資源使用。</span><span class="sxs-lookup"><span data-stu-id="fc5cd-105">System parameter metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="fc5cd-106">如果您想要在應用程式執行時自動更新參數度量資訊，請使用動態資源；否則請使用靜態資源。</span><span class="sxs-lookup"><span data-stu-id="fc5cd-106">Use a dynamic resource if you want the parameter metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc5cd-107">動態資源具有關鍵字*金鑰*附加至屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="fc5cd-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="fc5cd-108">下列範例示範如何存取及使用系統參數動態資源，以設定或自訂按鈕的樣式。</span><span class="sxs-lookup"><span data-stu-id="fc5cd-108">The following example shows how to access and use system parameter dynamic resources to style or customize a button.</span></span> <span data-ttu-id="fc5cd-109">這[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]範例按鈕大小指派<xref:System.Windows.SystemParameters>按鈕的寬度和高度的值。</span><span class="sxs-lookup"><span data-stu-id="fc5cd-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example sizes a button by assigning <xref:System.Windows.SystemParameters> values to the button's width and height.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc5cd-110">範例</span><span class="sxs-lookup"><span data-stu-id="fc5cd-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="fc5cd-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc5cd-111">See also</span></span>

- [<span data-ttu-id="fc5cd-112">使用系統筆刷繪製區域</span><span class="sxs-lookup"><span data-stu-id="fc5cd-112">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="fc5cd-113">使用 SystemFonts</span><span class="sxs-lookup"><span data-stu-id="fc5cd-113">Use SystemFonts</span></span>](how-to-use-systemfonts.md)
- [<span data-ttu-id="fc5cd-114">使用 SystemParameters</span><span class="sxs-lookup"><span data-stu-id="fc5cd-114">Use SystemParameters</span></span>](how-to-use-systemparameters.md)

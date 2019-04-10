---
title: HOW TO：使用系統字型索引鍵
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: e924f4c14d98380d9f4c0defe27d9f98c3293114
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148924"
---
# <a name="how-to-use-system-fonts-keys"></a><span data-ttu-id="ca3e8-102">HOW TO：使用系統字型索引鍵</span><span class="sxs-lookup"><span data-stu-id="ca3e8-102">How to: Use System Fonts Keys</span></span>
<span data-ttu-id="ca3e8-103">系統資源會將數個系統度量資訊公開為資源，協助開發人員建立與系統設定一致的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="ca3e8-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <xref:System.Windows.SystemFonts> <span data-ttu-id="ca3e8-104">是包含系統字型值以及繫結至值的系統字型資源的類別，例如<xref:System.Windows.SystemFonts.CaptionFontFamily%2A>和<xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>。</span><span class="sxs-lookup"><span data-stu-id="ca3e8-104">is a class that contains both system font values and system font resources that bind to the values—for example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span></span>  
  
 <span data-ttu-id="ca3e8-105">系統字型度量資訊可以當成靜態或動態資源使用。</span><span class="sxs-lookup"><span data-stu-id="ca3e8-105">System font metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="ca3e8-106">如果您想要在應用程式執行時自動更新字型度量資訊，請使用動態資源；否則請使用靜態資源。</span><span class="sxs-lookup"><span data-stu-id="ca3e8-106">Use a dynamic resource if you want the font metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca3e8-107">動態資源具有關鍵字*金鑰*附加至屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="ca3e8-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="ca3e8-108">下列範例示範如何存取及使用系統字型動態資源，以設定或自訂按鈕的樣式。</span><span class="sxs-lookup"><span data-stu-id="ca3e8-108">The following example shows how to access and use system font dynamic resources to style or customize a button.</span></span> <span data-ttu-id="ca3e8-109">這[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]範例會建立將指派的按鈕樣式<xref:System.Windows.SystemFonts>至按鈕的值。</span><span class="sxs-lookup"><span data-stu-id="ca3e8-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example creates a button style that assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca3e8-110">範例</span><span class="sxs-lookup"><span data-stu-id="ca3e8-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#FontDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="ca3e8-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca3e8-111">See also</span></span>

- [<span data-ttu-id="ca3e8-112">使用系統筆刷繪製區域</span><span class="sxs-lookup"><span data-stu-id="ca3e8-112">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="ca3e8-113">使用 SystemParameters</span><span class="sxs-lookup"><span data-stu-id="ca3e8-113">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
- [<span data-ttu-id="ca3e8-114">使用 SystemFonts</span><span class="sxs-lookup"><span data-stu-id="ca3e8-114">Use SystemFonts</span></span>](how-to-use-systemfonts.md)

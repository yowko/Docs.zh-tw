---
title: 作法：使用系統字型索引鍵
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: 7283e4225b75909322fa312583e9f1a0679762e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918391"
---
# <a name="how-to-use-system-fonts-keys"></a><span data-ttu-id="65e08-102">HOW TO：使用系統字型索引鍵</span><span class="sxs-lookup"><span data-stu-id="65e08-102">How to: Use System Fonts Keys</span></span>
<span data-ttu-id="65e08-103">系統資源會將數個系統度量資訊公開為資源，協助開發人員建立與系統設定一致的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="65e08-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="65e08-104"><xref:System.Windows.SystemFonts>是一個類別, 其中同時包含系統字型值和系結至值的系統字型資源 (例如和<xref:System.Windows.SystemFonts.CaptionFontFamily%2A> <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>)。</span><span class="sxs-lookup"><span data-stu-id="65e08-104"><xref:System.Windows.SystemFonts> is a class that contains both system font values and system font resources that bind to the values—for example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span></span>  
  
 <span data-ttu-id="65e08-105">系統字型度量資訊可以當成靜態或動態資源使用。</span><span class="sxs-lookup"><span data-stu-id="65e08-105">System font metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="65e08-106">如果您想要在應用程式執行時自動更新字型度量資訊，請使用動態資源；否則請使用靜態資源。</span><span class="sxs-lookup"><span data-stu-id="65e08-106">Use a dynamic resource if you want the font metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="65e08-107">動態資源會在屬性名稱後面附加關鍵字索引*鍵*。</span><span class="sxs-lookup"><span data-stu-id="65e08-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="65e08-108">下列範例示範如何存取及使用系統字型動態資源，以設定或自訂按鈕的樣式。</span><span class="sxs-lookup"><span data-stu-id="65e08-108">The following example shows how to access and use system font dynamic resources to style or customize a button.</span></span> <span data-ttu-id="65e08-109">這個[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]範例會建立按鈕樣式, 將<xref:System.Windows.SystemFonts>值指派給按鈕。</span><span class="sxs-lookup"><span data-stu-id="65e08-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example creates a button style that assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65e08-110">範例</span><span class="sxs-lookup"><span data-stu-id="65e08-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#FontDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="65e08-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65e08-111">See also</span></span>

- [<span data-ttu-id="65e08-112">使用系統筆刷繪製區域</span><span class="sxs-lookup"><span data-stu-id="65e08-112">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="65e08-113">使用 SystemParameters</span><span class="sxs-lookup"><span data-stu-id="65e08-113">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
- [<span data-ttu-id="65e08-114">使用 SystemFonts</span><span class="sxs-lookup"><span data-stu-id="65e08-114">Use SystemFonts</span></span>](how-to-use-systemfonts.md)

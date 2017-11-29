---
title: "如何：使用系統字型索引鍵"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18781e3d71b9b30352323081e6d938350c6e53d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-system-fonts-keys"></a><span data-ttu-id="19e15-102">如何：使用系統字型索引鍵</span><span class="sxs-lookup"><span data-stu-id="19e15-102">How to: Use System Fonts Keys</span></span>
<span data-ttu-id="19e15-103">系統資源會將數個系統度量資訊公開為資源，協助開發人員建立與系統設定一致的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="19e15-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="19e15-104"><xref:System.Windows.SystemFonts>是包含系統字型值和系統字型資源的值繫結的類別，例如<xref:System.Windows.SystemFonts.CaptionFontFamily%2A>和<xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>。</span><span class="sxs-lookup"><span data-stu-id="19e15-104"><xref:System.Windows.SystemFonts> is a class that contains both system font values and system font resources that bind to the values—for example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span></span>  
  
 <span data-ttu-id="19e15-105">系統字型度量資訊可以當成靜態或動態資源使用。</span><span class="sxs-lookup"><span data-stu-id="19e15-105">System font metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="19e15-106">如果您想要在應用程式執行時自動更新字型度量資訊，請使用動態資源；否則請使用靜態資源。</span><span class="sxs-lookup"><span data-stu-id="19e15-106">Use a dynamic resource if you want the font metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19e15-107">動態資源有關鍵字*金鑰*附加至屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="19e15-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="19e15-108">下列範例示範如何存取及使用系統字型動態資源，以設定或自訂按鈕的樣式。</span><span class="sxs-lookup"><span data-stu-id="19e15-108">The following example shows how to access and use system font dynamic resources to style or customize a button.</span></span> <span data-ttu-id="19e15-109">這[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]範例會建立指派按鈕樣式<xref:System.Windows.SystemFonts>按鈕的值。</span><span class="sxs-lookup"><span data-stu-id="19e15-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example creates a button style that assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19e15-110">範例</span><span class="sxs-lookup"><span data-stu-id="19e15-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#FontDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="19e15-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19e15-111">See Also</span></span>  
 [<span data-ttu-id="19e15-112">使用系統筆刷繪製區域</span><span class="sxs-lookup"><span data-stu-id="19e15-112">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="19e15-113">使用 SystemParameters</span><span class="sxs-lookup"><span data-stu-id="19e15-113">Use SystemParameters</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)  
 [<span data-ttu-id="19e15-114">使用 SystemFonts</span><span class="sxs-lookup"><span data-stu-id="19e15-114">Use SystemFonts</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)

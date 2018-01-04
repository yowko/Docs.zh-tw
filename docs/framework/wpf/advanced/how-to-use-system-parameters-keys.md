---
title: "如何：使用系統參數索引鍵"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b2a7352540456b459428dd87f6c60be0b8bc08b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-system-parameters-keys"></a><span data-ttu-id="268bb-102">如何：使用系統參數索引鍵</span><span class="sxs-lookup"><span data-stu-id="268bb-102">How to: Use System Parameters Keys</span></span>
<span data-ttu-id="268bb-103">系統資源會將數個系統度量資訊公開為資源，協助開發人員建立與系統設定一致的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="268bb-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="268bb-104"><xref:System.Windows.SystemParameters>是類別，其中包含系統參數值和繫結到值的資源索引鍵 — 比方說，<xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A>和<xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>。</span><span class="sxs-lookup"><span data-stu-id="268bb-104"><xref:System.Windows.SystemParameters> is a class that contains both system parameter values and resource keys that bind to the values—for example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span></span> <span data-ttu-id="268bb-105">系統參數度量資訊可以當成靜態或動態資源使用。</span><span class="sxs-lookup"><span data-stu-id="268bb-105">System parameter metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="268bb-106">如果您想要在應用程式執行時自動更新參數度量資訊，請使用動態資源；否則請使用靜態資源。</span><span class="sxs-lookup"><span data-stu-id="268bb-106">Use a dynamic resource if you want the parameter metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="268bb-107">動態資源有關鍵字*金鑰*附加至屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="268bb-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="268bb-108">下列範例示範如何存取及使用系統參數動態資源，以設定或自訂按鈕的樣式。</span><span class="sxs-lookup"><span data-stu-id="268bb-108">The following example shows how to access and use system parameter dynamic resources to style or customize a button.</span></span> <span data-ttu-id="268bb-109">這[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]範例藉由指定大小的按鈕<xref:System.Windows.SystemParameters>按鈕的寬度和高度的值。</span><span class="sxs-lookup"><span data-stu-id="268bb-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example sizes a button by assigning <xref:System.Windows.SystemParameters> values to the button's width and height.</span></span>  
  
## <a name="example"></a><span data-ttu-id="268bb-110">範例</span><span class="sxs-lookup"><span data-stu-id="268bb-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="268bb-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="268bb-111">See Also</span></span>  
 [<span data-ttu-id="268bb-112">使用系統筆刷繪製區域</span><span class="sxs-lookup"><span data-stu-id="268bb-112">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="268bb-113">使用 SystemFonts</span><span class="sxs-lookup"><span data-stu-id="268bb-113">Use SystemFonts</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [<span data-ttu-id="268bb-114">使用 SystemParameters</span><span class="sxs-lookup"><span data-stu-id="268bb-114">Use SystemParameters</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)

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
ms.openlocfilehash: 2b5f45f386c58b0577a2716c6fe1396f4c44f4ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-system-parameters-keys"></a><span data-ttu-id="16efc-102">如何：使用系統參數索引鍵</span><span class="sxs-lookup"><span data-stu-id="16efc-102">How to: Use System Parameters Keys</span></span>
<span data-ttu-id="16efc-103">系統資源會將數個系統度量資訊公開為資源，協助開發人員建立與系統設定一致的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="16efc-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="16efc-104"><xref:System.Windows.SystemParameters>是類別，其中包含系統參數值和繫結到值的資源索引鍵 — 比方說，<xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A>和<xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>。</span><span class="sxs-lookup"><span data-stu-id="16efc-104"><xref:System.Windows.SystemParameters> is a class that contains both system parameter values and resource keys that bind to the values—for example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span></span> <span data-ttu-id="16efc-105">系統參數度量資訊可以當成靜態或動態資源使用。</span><span class="sxs-lookup"><span data-stu-id="16efc-105">System parameter metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="16efc-106">如果您想要在應用程式執行時自動更新參數度量資訊，請使用動態資源；否則請使用靜態資源。</span><span class="sxs-lookup"><span data-stu-id="16efc-106">Use a dynamic resource if you want the parameter metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16efc-107">動態資源有關鍵字*金鑰*附加至屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="16efc-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="16efc-108">下列範例示範如何存取及使用系統參數動態資源，以設定或自訂按鈕的樣式。</span><span class="sxs-lookup"><span data-stu-id="16efc-108">The following example shows how to access and use system parameter dynamic resources to style or customize a button.</span></span> <span data-ttu-id="16efc-109">這[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]範例藉由指定大小的按鈕<xref:System.Windows.SystemParameters>按鈕的寬度和高度的值。</span><span class="sxs-lookup"><span data-stu-id="16efc-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example sizes a button by assigning <xref:System.Windows.SystemParameters> values to the button's width and height.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16efc-110">範例</span><span class="sxs-lookup"><span data-stu-id="16efc-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="16efc-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16efc-111">See Also</span></span>  
 [<span data-ttu-id="16efc-112">使用系統筆刷繪製區域</span><span class="sxs-lookup"><span data-stu-id="16efc-112">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="16efc-113">使用 SystemFonts</span><span class="sxs-lookup"><span data-stu-id="16efc-113">Use SystemFonts</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [<span data-ttu-id="16efc-114">使用 SystemParameters</span><span class="sxs-lookup"><span data-stu-id="16efc-114">Use SystemParameters</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)

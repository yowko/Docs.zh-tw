---
title: "如何：變更游標類型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 41cd8c9cd647c7efbc4e6cf13517ed638245e51c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-change-the-cursor-type"></a><span data-ttu-id="5491f-102">如何：變更游標類型</span><span class="sxs-lookup"><span data-stu-id="5491f-102">How to: Change the Cursor Type</span></span>
<span data-ttu-id="5491f-103">這個範例示範如何變更<xref:System.Windows.Input.Cursor>滑鼠指標特定的項目和應用程式。</span><span class="sxs-lookup"><span data-stu-id="5491f-103">This example shows how to change the <xref:System.Windows.Input.Cursor> of the mouse pointer for a specific element and for the application.</span></span>  
  
 <span data-ttu-id="5491f-104">這個範例包含[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案和程式碼後置檔案。</span><span class="sxs-lookup"><span data-stu-id="5491f-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5491f-105">範例</span><span class="sxs-lookup"><span data-stu-id="5491f-105">Example</span></span>  
 <span data-ttu-id="5491f-106">建立使用者介面，其中包含的<xref:System.Windows.Controls.ComboBox>來選取所需<xref:System.Windows.Input.Cursor>，一組<xref:System.Windows.Controls.RadioButton>物件來判斷是否資料指標變更套用至單一項目，或套用至整個應用程式，以及<xref:System.Windows.Controls.Border>這是新的資料指標會套用至的項目。</span><span class="sxs-lookup"><span data-stu-id="5491f-106">The user interface is created, which consists of a <xref:System.Windows.Controls.ComboBox> to select the desired <xref:System.Windows.Input.Cursor>, a pair of <xref:System.Windows.Controls.RadioButton> objects to determine if the cursor change applies to only a single element or applies to the entire application, and a <xref:System.Windows.Controls.Border> which is the element that the new cursor is applied to.</span></span>  
  
 [!code-xaml[cursors#ChangeCursorsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 <span data-ttu-id="5491f-107">下列程式碼後置建立<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>中變更的資料指標類型，就會呼叫事件處理常式<xref:System.Windows.Controls.ComboBox>。</span><span class="sxs-lookup"><span data-stu-id="5491f-107">The following code behind creates a <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event handler which is called when the cursor type is changed in the <xref:System.Windows.Controls.ComboBox>.</span></span>  <span data-ttu-id="5491f-108">Switch 陳述式的篩選集與資料指標名稱<xref:System.Windows.FrameworkElement.Cursor%2A>屬性<xref:System.Windows.Controls.Border>這名為*DisplayArea*。</span><span class="sxs-lookup"><span data-stu-id="5491f-108">A switch statement filters on the cursor name and sets the <xref:System.Windows.FrameworkElement.Cursor%2A> property on the <xref:System.Windows.Controls.Border> which is named *DisplayArea*.</span></span>  
  
 <span data-ttu-id="5491f-109">如果資料指標變更設定為 「 整個應用程式 」<xref:System.Windows.Input.Mouse.OverrideCursor%2A>屬性設定為<xref:System.Windows.FrameworkElement.Cursor%2A>屬性<xref:System.Windows.Controls.Border>控制項。</span><span class="sxs-lookup"><span data-stu-id="5491f-109">If the cursor change is set to "Entire Application", the <xref:System.Windows.Input.Mouse.OverrideCursor%2A> property is set to the <xref:System.Windows.FrameworkElement.Cursor%2A> property of the <xref:System.Windows.Controls.Border> control.</span></span>  <span data-ttu-id="5491f-110">這會強制變更整個應用程式的游標。</span><span class="sxs-lookup"><span data-stu-id="5491f-110">This forces the cursor to change for the whole application.</span></span>  
  
 [!code-csharp[cursors#ChangeCursorsSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a><span data-ttu-id="5491f-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5491f-111">See Also</span></span>  
 [<span data-ttu-id="5491f-112">輸入概觀</span><span class="sxs-lookup"><span data-stu-id="5491f-112">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)

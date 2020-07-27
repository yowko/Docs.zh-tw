---
title: 如何：變更游標類型
description: 變更專案的滑鼠指標游標以及 Windows Presentation Foundation 中的應用程式。 這個範例包含 XAML 和程式碼後置檔案。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
ms.openlocfilehash: ce0bc290948a0e52e85f76ceb62a330b49fd87ea
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165959"
---
# <a name="how-to-change-the-cursor-type"></a><span data-ttu-id="470bb-104">如何：變更游標類型</span><span class="sxs-lookup"><span data-stu-id="470bb-104">How to: Change the Cursor Type</span></span>
<span data-ttu-id="470bb-105">這個範例會示範如何變更特定專案的 <xref:System.Windows.Input.Cursor> 滑鼠指標，以及應用程式的。</span><span class="sxs-lookup"><span data-stu-id="470bb-105">This example shows how to change the <xref:System.Windows.Input.Cursor> of the mouse pointer for a specific element and for the application.</span></span>  
  
 <span data-ttu-id="470bb-106">這個範例包含檔案 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 和程式碼後置檔案。</span><span class="sxs-lookup"><span data-stu-id="470bb-106">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="470bb-107">範例</span><span class="sxs-lookup"><span data-stu-id="470bb-107">Example</span></span>  
 <span data-ttu-id="470bb-108">使用者介面是由所建立，其中包含 <xref:System.Windows.Controls.ComboBox> 要選取所需的 <xref:System.Windows.Input.Cursor> 、一組 <xref:System.Windows.Controls.RadioButton> 物件，以判斷游標變更僅適用于單一專案，還是套用至整個應用程式，而是新資料 <xref:System.Windows.Controls.Border> 指標套用的元素。</span><span class="sxs-lookup"><span data-stu-id="470bb-108">The user interface is created, which consists of a <xref:System.Windows.Controls.ComboBox> to select the desired <xref:System.Windows.Input.Cursor>, a pair of <xref:System.Windows.Controls.RadioButton> objects to determine if the cursor change applies to only a single element or applies to the entire application, and a <xref:System.Windows.Controls.Border> which is the element that the new cursor is applied to.</span></span>  
  
 [!code-xaml[cursors#ChangeCursorsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 <span data-ttu-id="470bb-109">下列程式碼後置會建立一個 <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> 事件處理常式，當中的資料指標類型變更時，就會呼叫它 <xref:System.Windows.Controls.ComboBox> 。</span><span class="sxs-lookup"><span data-stu-id="470bb-109">The following code behind creates a <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event handler which is called when the cursor type is changed in the <xref:System.Windows.Controls.ComboBox>.</span></span>  <span data-ttu-id="470bb-110">Switch 語句會篩選游標名稱，並在 <xref:System.Windows.FrameworkElement.Cursor%2A> <xref:System.Windows.Controls.Border> 名為*DisplayArea*的上設定屬性。</span><span class="sxs-lookup"><span data-stu-id="470bb-110">A switch statement filters on the cursor name and sets the <xref:System.Windows.FrameworkElement.Cursor%2A> property on the <xref:System.Windows.Controls.Border> which is named *DisplayArea*.</span></span>  
  
 <span data-ttu-id="470bb-111">如果資料指標變更設定為「整個應用程式」，則 <xref:System.Windows.Input.Mouse.OverrideCursor%2A> 屬性會設定為 <xref:System.Windows.FrameworkElement.Cursor%2A> 控制項的屬性 <xref:System.Windows.Controls.Border> 。</span><span class="sxs-lookup"><span data-stu-id="470bb-111">If the cursor change is set to "Entire Application", the <xref:System.Windows.Input.Mouse.OverrideCursor%2A> property is set to the <xref:System.Windows.FrameworkElement.Cursor%2A> property of the <xref:System.Windows.Controls.Border> control.</span></span>  <span data-ttu-id="470bb-112">這會強制變更整個應用程式的游標。</span><span class="sxs-lookup"><span data-stu-id="470bb-112">This forces the cursor to change for the whole application.</span></span>  
  
 [!code-csharp[cursors#ChangeCursorsSample](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a><span data-ttu-id="470bb-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="470bb-113">See also</span></span>

- [<span data-ttu-id="470bb-114">輸入概觀</span><span class="sxs-lookup"><span data-stu-id="470bb-114">Input Overview</span></span>](input-overview.md)

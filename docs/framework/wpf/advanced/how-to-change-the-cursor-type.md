---
title: HOW TO：變更游標類型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
ms.openlocfilehash: 5c9e6931f6addb62a51e44b06a159d4e7b1e5f8a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141202"
---
# <a name="how-to-change-the-cursor-type"></a><span data-ttu-id="0b72a-102">HOW TO：變更游標類型</span><span class="sxs-lookup"><span data-stu-id="0b72a-102">How to: Change the Cursor Type</span></span>
<span data-ttu-id="0b72a-103">此範例示範如何變更<xref:System.Windows.Input.Cursor>滑鼠指標的特定項目以及應用程式。</span><span class="sxs-lookup"><span data-stu-id="0b72a-103">This example shows how to change the <xref:System.Windows.Input.Cursor> of the mouse pointer for a specific element and for the application.</span></span>  
  
 <span data-ttu-id="0b72a-104">此範例中組成[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案和程式碼後置檔案。</span><span class="sxs-lookup"><span data-stu-id="0b72a-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b72a-105">範例</span><span class="sxs-lookup"><span data-stu-id="0b72a-105">Example</span></span>  
 <span data-ttu-id="0b72a-106">已建立使用者介面，其中包含<xref:System.Windows.Controls.ComboBox>若要選取所需<xref:System.Windows.Input.Cursor>，一組<xref:System.Windows.Controls.RadioButton>物件來判斷是否資料指標變更套用至單一項目，或適用於整個應用程式，和<xref:System.Windows.Controls.Border>這是新的資料指標會套用至的項目。</span><span class="sxs-lookup"><span data-stu-id="0b72a-106">The user interface is created, which consists of a <xref:System.Windows.Controls.ComboBox> to select the desired <xref:System.Windows.Input.Cursor>, a pair of <xref:System.Windows.Controls.RadioButton> objects to determine if the cursor change applies to only a single element or applies to the entire application, and a <xref:System.Windows.Controls.Border> which is the element that the new cursor is applied to.</span></span>  
  
 [!code-xaml[cursors#ChangeCursorsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 <span data-ttu-id="0b72a-107">建立下列的程式碼後置<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>事件處理常式中變更的資料指標類型時，會呼叫<xref:System.Windows.Controls.ComboBox>。</span><span class="sxs-lookup"><span data-stu-id="0b72a-107">The following code behind creates a <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event handler which is called when the cursor type is changed in the <xref:System.Windows.Controls.ComboBox>.</span></span>  <span data-ttu-id="0b72a-108">Switch 陳述式會篩選的資料指標名稱和集合<xref:System.Windows.FrameworkElement.Cursor%2A>上的屬性<xref:System.Windows.Controls.Border>哪些具名*DisplayArea*。</span><span class="sxs-lookup"><span data-stu-id="0b72a-108">A switch statement filters on the cursor name and sets the <xref:System.Windows.FrameworkElement.Cursor%2A> property on the <xref:System.Windows.Controls.Border> which is named *DisplayArea*.</span></span>  
  
 <span data-ttu-id="0b72a-109">如果資料指標變更設定為 「 整個應用程式 」<xref:System.Windows.Input.Mouse.OverrideCursor%2A>屬性設定為<xref:System.Windows.FrameworkElement.Cursor%2A>屬性<xref:System.Windows.Controls.Border>控制項。</span><span class="sxs-lookup"><span data-stu-id="0b72a-109">If the cursor change is set to "Entire Application", the <xref:System.Windows.Input.Mouse.OverrideCursor%2A> property is set to the <xref:System.Windows.FrameworkElement.Cursor%2A> property of the <xref:System.Windows.Controls.Border> control.</span></span>  <span data-ttu-id="0b72a-110">這會強制變更整個應用程式的游標。</span><span class="sxs-lookup"><span data-stu-id="0b72a-110">This forces the cursor to change for the whole application.</span></span>  
  
 [!code-csharp[cursors#ChangeCursorsSample](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a><span data-ttu-id="0b72a-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b72a-111">See also</span></span>

- [<span data-ttu-id="0b72a-112">輸入概觀</span><span class="sxs-lookup"><span data-stu-id="0b72a-112">Input Overview</span></span>](input-overview.md)

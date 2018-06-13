---
title: 如何：取得或設定 Canvas 定位屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Canvas control [WPF], setting positioning properties
ms.assetid: 1636b950-2b5a-4507-8a10-c5034cc58b1c
ms.openlocfilehash: 294b49d427a67da849ce930cf29a48f1735bf135
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551976"
---
# <a name="how-to-get-or-set-canvas-positioning-properties"></a><span data-ttu-id="36163-102">如何：取得或設定 Canvas 定位屬性</span><span class="sxs-lookup"><span data-stu-id="36163-102">How to: Get or Set Canvas Positioning Properties</span></span>
<span data-ttu-id="36163-103">這個範例示範如何使用定位方法<xref:System.Windows.Controls.Canvas>，將子內容項目。</span><span class="sxs-lookup"><span data-stu-id="36163-103">This example shows how to use the positioning methods of the <xref:System.Windows.Controls.Canvas> element to position child content.</span></span> <span data-ttu-id="36163-104">這個範例會使用中的內容<xref:System.Windows.Controls.ListBoxItem>來代表定位值，並將值的執行個體轉換為<xref:System.Double>，這是必要的引數的位置。</span><span class="sxs-lookup"><span data-stu-id="36163-104">This example uses content in a <xref:System.Windows.Controls.ListBoxItem> to represent positioning values and converts the values into instances of <xref:System.Double>, which is a required argument for positioning.</span></span> <span data-ttu-id="36163-105">值是再轉換回字串，並且顯示為文字中<xref:System.Windows.Controls.TextBlock>所使用的項目<xref:System.Windows.Controls.Canvas.GetLeft%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="36163-105">The values are then converted back into strings and displayed as text in a <xref:System.Windows.Controls.TextBlock> element by using the <xref:System.Windows.Controls.Canvas.GetLeft%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36163-106">範例</span><span class="sxs-lookup"><span data-stu-id="36163-106">Example</span></span>  
 <span data-ttu-id="36163-107">下列範例會建立<xref:System.Windows.Controls.ListBox>擁有十一個可選取的項目<xref:System.Windows.Controls.ListBoxItem>項目。</span><span class="sxs-lookup"><span data-stu-id="36163-107">The following example creates a <xref:System.Windows.Controls.ListBox> element that has eleven selectable <xref:System.Windows.Controls.ListBoxItem> elements.</span></span> <span data-ttu-id="36163-108"><xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>事件觸發程序`ChangeLeft`後續程式碼區塊會定義中的自訂方法。</span><span class="sxs-lookup"><span data-stu-id="36163-108">The <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event triggers the `ChangeLeft` custom method, which the subsequent code block defines.</span></span>  
  
 <span data-ttu-id="36163-109">每個<xref:System.Windows.Controls.ListBoxItem>代表<xref:System.Double>值，這是其中一個引數，<xref:System.Windows.Controls.Canvas.SetLeft%2A>方法<xref:System.Windows.Controls.Canvas>接受。</span><span class="sxs-lookup"><span data-stu-id="36163-109">Each <xref:System.Windows.Controls.ListBoxItem> represents a <xref:System.Double> value, which is one of the arguments that the <xref:System.Windows.Controls.Canvas.SetLeft%2A> method of <xref:System.Windows.Controls.Canvas> accepts.</span></span> <span data-ttu-id="36163-110">若要使用<xref:System.Windows.Controls.ListBoxItem>來代表的執行個體<xref:System.Double>，您必須先轉換<xref:System.Windows.Controls.ListBoxItem>到正確的資料類型。</span><span class="sxs-lookup"><span data-stu-id="36163-110">In order to use a <xref:System.Windows.Controls.ListBoxItem> to represent an instance of <xref:System.Double>, you must first convert the <xref:System.Windows.Controls.ListBoxItem> to the correct data type.</span></span>  
  
 [!code-xaml[CanvasPositioningProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="36163-111">當使用者變更<xref:System.Windows.Controls.ListBox>選取項目，它會叫用`ChangeLeft`自訂方法。</span><span class="sxs-lookup"><span data-stu-id="36163-111">When a user changes the <xref:System.Windows.Controls.ListBox> selection, it invokes the `ChangeLeft` custom method.</span></span> <span data-ttu-id="36163-112">這個方法會傳遞<xref:System.Windows.Controls.ListBoxItem>至<xref:System.Windows.LengthConverter>物件，然後將轉換<xref:System.Windows.Controls.ContentControl.Content%2A>的<xref:System.Windows.Controls.ListBoxItem>的執行個體<xref:System.Double>(請注意，這個值已轉換成<xref:System.String>使用<xref:System.Windows.Controls.Control.ToString%2A>方法）。</span><span class="sxs-lookup"><span data-stu-id="36163-112">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.LengthConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Double> (notice that this value has already been converted to a <xref:System.String> by using the <xref:System.Windows.Controls.Control.ToString%2A> method).</span></span> <span data-ttu-id="36163-113">此值接著會傳遞回<xref:System.Windows.Controls.Canvas.SetLeft%2A>和<xref:System.Windows.Controls.Canvas.GetLeft%2A>方法<xref:System.Windows.Controls.Canvas>若要變更的位置`text1`物件。</span><span class="sxs-lookup"><span data-stu-id="36163-113">This value is then passed back to the <xref:System.Windows.Controls.Canvas.SetLeft%2A> and <xref:System.Windows.Controls.Canvas.GetLeft%2A> methods of <xref:System.Windows.Controls.Canvas> in order to change the position of the `text1` object.</span></span>  
  
 [!code-csharp[CanvasPositioningProperties#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml.cs#2)]
 [!code-vb[CanvasPositioningProperties#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasPositioningProperties/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="36163-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36163-114">See Also</span></span>  
 <xref:System.Windows.Controls.Canvas>  
 <xref:System.Windows.Controls.ListBoxItem>  
 <xref:System.Windows.LengthConverter>  
 [<span data-ttu-id="36163-115">面板概觀</span><span class="sxs-lookup"><span data-stu-id="36163-115">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)

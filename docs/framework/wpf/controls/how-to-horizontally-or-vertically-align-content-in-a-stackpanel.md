---
title: HOW TO：水平或垂直對齊 StackPanel 中的內容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
ms.openlocfilehash: 6605a6a56fba587678227f5826982ec3266b153c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356286"
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a><span data-ttu-id="de451-102">HOW TO：水平或垂直對齊 StackPanel 中的內容</span><span class="sxs-lookup"><span data-stu-id="de451-102">How to: Horizontally or Vertically Align Content in a StackPanel</span></span>
<span data-ttu-id="de451-103">此範例示範如何調整<xref:System.Windows.Controls.StackPanel.Orientation%2A>內的內容<xref:System.Windows.Controls.StackPanel>項目，以及如何調整<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>和<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>子內容。</span><span class="sxs-lookup"><span data-stu-id="de451-103">This example shows how to adjust the <xref:System.Windows.Controls.StackPanel.Orientation%2A> of content within a <xref:System.Windows.Controls.StackPanel> element, and also how to adjust the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> of child content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de451-104">範例</span><span class="sxs-lookup"><span data-stu-id="de451-104">Example</span></span>  
 <span data-ttu-id="de451-105">下列範例會建立三個<xref:System.Windows.Controls.ListBox>中的項目[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="de451-105">The following example creates three <xref:System.Windows.Controls.ListBox> elements in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="de451-106">每個<xref:System.Windows.Controls.ListBox>代表的可能值<xref:System.Windows.Controls.StackPanel.Orientation%2A>， <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>，以及<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>的屬性<xref:System.Windows.Controls.StackPanel>。</span><span class="sxs-lookup"><span data-stu-id="de451-106">Each <xref:System.Windows.Controls.ListBox> represents the possible values of the <xref:System.Windows.Controls.StackPanel.Orientation%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> properties of a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="de451-107">當使用者選取的值中的任何<xref:System.Windows.Controls.ListBox>項目、 相關聯的屬性<xref:System.Windows.Controls.StackPanel>及其子<xref:System.Windows.Controls.Button>項目變更。</span><span class="sxs-lookup"><span data-stu-id="de451-107">When a user selects a value in any of the <xref:System.Windows.Controls.ListBox> elements, the associated property of the <xref:System.Windows.Controls.StackPanel> and its child <xref:System.Windows.Controls.Button> elements change.</span></span>  
  
 [!code-xaml[StackPanelIntroSamp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="de451-108">下列程式碼後置檔案會定義所做的變更相關聯的事件<xref:System.Windows.Controls.ListBox>選擇項目的變更。</span><span class="sxs-lookup"><span data-stu-id="de451-108">The following code-behind file defines the changes to the events that are associated with the <xref:System.Windows.Controls.ListBox> selection changes.</span></span> <span data-ttu-id="de451-109"><xref:System.Windows.Controls.StackPanel> 由<xref:System.Windows.FrameworkElement.Name%2A> `sp1`。</span><span class="sxs-lookup"><span data-stu-id="de451-109"><xref:System.Windows.Controls.StackPanel> is identified by the <xref:System.Windows.FrameworkElement.Name%2A> `sp1`.</span></span>  
  
 [!code-csharp[StackPanelIntroSamp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="de451-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de451-110">See also</span></span>
- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- [<span data-ttu-id="de451-111">面板概觀</span><span class="sxs-lookup"><span data-stu-id="de451-111">Panels Overview</span></span>](panels-overview.md)

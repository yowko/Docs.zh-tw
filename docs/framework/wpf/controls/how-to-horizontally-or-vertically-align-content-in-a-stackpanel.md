---
title: 如何：水平或垂直對齊 StackPanel 中的內容
description: 瞭解如何在 Windows Presentation Foundation StackPanel 中調整內容方向以及子內容的 HorizontalAlignment 和 VerticalAlignment。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
ms.openlocfilehash: d3c7215d8193d1d8a72597c44cf265f5bd400ea1
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167623"
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a><span data-ttu-id="8707c-103">如何：水平或垂直對齊 StackPanel 中的內容</span><span class="sxs-lookup"><span data-stu-id="8707c-103">How to: Horizontally or Vertically Align Content in a StackPanel</span></span>
<span data-ttu-id="8707c-104">這個範例示範如何調整專案 <xref:System.Windows.Controls.StackPanel.Orientation%2A> 內的內容 <xref:System.Windows.Controls.StackPanel> ，以及如何調整 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 子內容的和。</span><span class="sxs-lookup"><span data-stu-id="8707c-104">This example shows how to adjust the <xref:System.Windows.Controls.StackPanel.Orientation%2A> of content within a <xref:System.Windows.Controls.StackPanel> element, and also how to adjust the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> of child content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8707c-105">範例</span><span class="sxs-lookup"><span data-stu-id="8707c-105">Example</span></span>  
 <span data-ttu-id="8707c-106">下列範例會在中建立三個 <xref:System.Windows.Controls.ListBox> 元素 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8707c-106">The following example creates three <xref:System.Windows.Controls.ListBox> elements in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="8707c-107">每個都 <xref:System.Windows.Controls.ListBox> 代表的 <xref:System.Windows.Controls.StackPanel.Orientation%2A> 、 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 和屬性的可能值 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> <xref:System.Windows.Controls.StackPanel> 。</span><span class="sxs-lookup"><span data-stu-id="8707c-107">Each <xref:System.Windows.Controls.ListBox> represents the possible values of the <xref:System.Windows.Controls.StackPanel.Orientation%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> properties of a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="8707c-108">當使用者在任何專案中選取值時 <xref:System.Windows.Controls.ListBox> ，和其子專案的相關聯屬性就會 <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.Button> 變更。</span><span class="sxs-lookup"><span data-stu-id="8707c-108">When a user selects a value in any of the <xref:System.Windows.Controls.ListBox> elements, the associated property of the <xref:System.Windows.Controls.StackPanel> and its child <xref:System.Windows.Controls.Button> elements change.</span></span>  
  
 [!code-xaml[StackPanelIntroSamp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="8707c-109">下列程式碼後置檔案會定義與選取範圍變更相關聯之事件的變更 <xref:System.Windows.Controls.ListBox> 。</span><span class="sxs-lookup"><span data-stu-id="8707c-109">The following code-behind file defines the changes to the events that are associated with the <xref:System.Windows.Controls.ListBox> selection changes.</span></span> <span data-ttu-id="8707c-110"><xref:System.Windows.Controls.StackPanel>是由所識別 <xref:System.Windows.FrameworkElement.Name%2A> `sp1` 。</span><span class="sxs-lookup"><span data-stu-id="8707c-110"><xref:System.Windows.Controls.StackPanel> is identified by the <xref:System.Windows.FrameworkElement.Name%2A> `sp1`.</span></span>  
  
 [!code-csharp[StackPanelIntroSamp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="8707c-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8707c-111">See also</span></span>

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- [<span data-ttu-id="8707c-112">面板概觀</span><span class="sxs-lookup"><span data-stu-id="8707c-112">Panels Overview</span></span>](panels-overview.md)

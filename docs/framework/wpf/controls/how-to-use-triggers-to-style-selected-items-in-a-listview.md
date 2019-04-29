---
title: HOW TO：使用觸發程序為 ListView 中的選取項目設定樣式
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 1e2bdce0-afe8-4507-9b18-f33de43de25a
ms.openlocfilehash: ad64382b871bae9114a1e63257de3f8595376923
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696186"
---
# <a name="how-to-use-triggers-to-style-selected-items-in-a-listview"></a><span data-ttu-id="12d11-102">HOW TO：使用觸發程序為 ListView 中的選取項目設定樣式</span><span class="sxs-lookup"><span data-stu-id="12d11-102">How to: Use Triggers to Style Selected Items in a ListView</span></span>
<span data-ttu-id="12d11-103">此範例示範如何定義<xref:System.Windows.Style.Triggers%2A>for<xref:System.Windows.Controls.ListViewItem>控制項，讓屬性值時<xref:System.Windows.Controls.ListViewItem>變更，<xref:System.Windows.Style>的<xref:System.Windows.Controls.ListViewItem>回應中的變更。</span><span class="sxs-lookup"><span data-stu-id="12d11-103">This example shows how to define <xref:System.Windows.Style.Triggers%2A> for a <xref:System.Windows.Controls.ListViewItem> control so that when a property value of a <xref:System.Windows.Controls.ListViewItem> changes, the <xref:System.Windows.Style> of the <xref:System.Windows.Controls.ListViewItem> changes in response.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12d11-104">範例</span><span class="sxs-lookup"><span data-stu-id="12d11-104">Example</span></span>  
 <span data-ttu-id="12d11-105">如果您想<xref:System.Windows.Style>的<xref:System.Windows.Controls.ListViewItem>若要變更以回應變更屬性，定義<xref:System.Windows.Style.Triggers%2A>如<xref:System.Windows.Style>變更。</span><span class="sxs-lookup"><span data-stu-id="12d11-105">If you want the <xref:System.Windows.Style> of a <xref:System.Windows.Controls.ListViewItem> to change in response to property changes, define <xref:System.Windows.Style.Triggers%2A> for the <xref:System.Windows.Style> change.</span></span>  
  
 <span data-ttu-id="12d11-106">下列範例會定義<xref:System.Windows.Trigger>，設定<xref:System.Windows.Controls.Control.Foreground%2A>屬性設<xref:System.Windows.Media.Brushes.Blue%2A>，並變更<xref:System.Windows.FrameworkElement.Cursor%2A>以顯示<xref:System.Windows.Input.CursorType.Hand>當<xref:System.Windows.UIElement.IsMouseOver%2A>屬性變更為`true`。</span><span class="sxs-lookup"><span data-stu-id="12d11-106">The following example defines a <xref:System.Windows.Trigger> that sets the <xref:System.Windows.Controls.Control.Foreground%2A> property to <xref:System.Windows.Media.Brushes.Blue%2A> and changes the <xref:System.Windows.FrameworkElement.Cursor%2A> to display a <xref:System.Windows.Input.CursorType.Hand> when the <xref:System.Windows.UIElement.IsMouseOver%2A> property changes to `true`.</span></span>  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#Trigger](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#trigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
 <span data-ttu-id="12d11-107">下列範例會定義<xref:System.Windows.MultiTrigger>，設定<xref:System.Windows.Controls.Control.Foreground%2A>屬性<xref:System.Windows.Controls.ListViewItem>要<xref:System.Windows.Media.Brushes.Yellow%2A>當<xref:System.Windows.Controls.ListViewItem>是選取的項目，並具有鍵盤焦點。</span><span class="sxs-lookup"><span data-stu-id="12d11-107">The following example defines a <xref:System.Windows.MultiTrigger> that sets the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.ListViewItem> to <xref:System.Windows.Media.Brushes.Yellow%2A> when the <xref:System.Windows.Controls.ListViewItem> is the selected item and has keyboard focus.</span></span>  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#MultiTrigger](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#multitrigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
## <a name="see-also"></a><span data-ttu-id="12d11-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12d11-108">See also</span></span>

- <xref:System.Windows.Controls.Control>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="12d11-109">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="12d11-109">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="12d11-110">ListView 概觀</span><span class="sxs-lookup"><span data-stu-id="12d11-110">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="12d11-111">GridView 概觀</span><span class="sxs-lookup"><span data-stu-id="12d11-111">GridView Overview</span></span>](gridview-overview.md)

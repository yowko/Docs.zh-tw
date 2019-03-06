---
title: HOW TO：改善 ListBox 的捲動效能
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListBox control [WPF], reusing item containers
- ListBox control [WPF], improving scrolling performance
ms.assetid: 1e2bf8f3-c8ce-47f7-a400-a7fe11d1a848
ms.openlocfilehash: a9d1ca1d8ac2ef830984408f3052eb0ed0987c5d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364550"
---
# <a name="how-to-improve-the-scrolling-performance-of-a-listbox"></a><span data-ttu-id="71414-102">HOW TO：改善 ListBox 的捲動效能</span><span class="sxs-lookup"><span data-stu-id="71414-102">How to: Improve the Scrolling Performance of a ListBox</span></span>
<span data-ttu-id="71414-103">如果<xref:System.Windows.Controls.ListBox>包含許多項目，當使用者捲動時，使用者介面回應可能會很慢<xref:System.Windows.Controls.ListBox>藉由使用滑鼠滾輪，或拖曳捲軸捲動方塊。</span><span class="sxs-lookup"><span data-stu-id="71414-103">If a <xref:System.Windows.Controls.ListBox> contains many items, the user interface response can be slow when a user scrolls the <xref:System.Windows.Controls.ListBox> by using the mouse wheel or dragging the thumb of a scrollbar.</span></span> <span data-ttu-id="71414-104">您可以改善效能<xref:System.Windows.Controls.ListBox>當使用者捲動藉由設定`VirtualizingStackPanel.VirtualizationMode`; 附加屬性<xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="71414-104">You can improve the performance of the <xref:System.Windows.Controls.ListBox> when the user scrolls by setting the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71414-105">範例</span><span class="sxs-lookup"><span data-stu-id="71414-105">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="71414-106">描述</span><span class="sxs-lookup"><span data-stu-id="71414-106">Description</span></span>  
<span data-ttu-id="71414-107">下列範例會建立<xref:System.Windows.Controls.ListBox>，並設定`VirtualizingStackPanel.VirtualizationMode`; 附加屬性<xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>改善捲動期間的效能。</span><span class="sxs-lookup"><span data-stu-id="71414-107">The following example creates a <xref:System.Windows.Controls.ListBox> and sets the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> to improve performance during scrolling.</span></span>  
  
## <a name="code"></a><span data-ttu-id="71414-108">程式碼</span><span class="sxs-lookup"><span data-stu-id="71414-108">Code</span></span>  
 [!code-xaml[RecycleItemContainerShippets#VirtualizationMode](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizationmode)]  
  
 <span data-ttu-id="71414-109">下列範例會顯示先前的範例使用的資料。</span><span class="sxs-lookup"><span data-stu-id="71414-109">The following example shows the data that the previous example uses.</span></span>  
  
 [!code-csharp[RecycleItemContainerShippets#ListBoxData](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#listboxdata)]
 [!code-vb[RecycleItemContainerShippets#ListBoxData](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#listboxdata)]

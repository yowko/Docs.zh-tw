---
title: "如何：改善 ListBox 的捲動效能"
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
- ListBox control [WPF], reusing item containers
- ListBox control [WPF], improving scrolling performance
ms.assetid: 1e2bf8f3-c8ce-47f7-a400-a7fe11d1a848
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58435948a3ddd8042b95b30b8d6cbdba984f34d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-improve-the-scrolling-performance-of-a-listbox"></a><span data-ttu-id="c3fc8-102">如何：改善 ListBox 的捲動效能</span><span class="sxs-lookup"><span data-stu-id="c3fc8-102">How to: Improve the Scrolling Performance of a ListBox</span></span>
<span data-ttu-id="c3fc8-103">如果<xref:System.Windows.Controls.ListBox>包含許多項目，使用者捲動時，使用者介面回應可能會很慢<xref:System.Windows.Controls.ListBox>藉由使用滑鼠滾輪，或拖曳捲軸的捲動方塊。</span><span class="sxs-lookup"><span data-stu-id="c3fc8-103">If a <xref:System.Windows.Controls.ListBox> contains many items, the user interface response can be slow when a user scrolls the <xref:System.Windows.Controls.ListBox> by using the mouse wheel or dragging the thumb of a scrollbar.</span></span> <span data-ttu-id="c3fc8-104">您可以改善效能<xref:System.Windows.Controls.ListBox>當使用者捲動藉由設定`VirtualizingStackPanel.VirtualizationMode`附加屬性<xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="c3fc8-104">You can improve the performance of the <xref:System.Windows.Controls.ListBox> when the user scrolls by setting the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3fc8-105">範例</span><span class="sxs-lookup"><span data-stu-id="c3fc8-105">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="c3fc8-106">描述</span><span class="sxs-lookup"><span data-stu-id="c3fc8-106">Description</span></span>  
<span data-ttu-id="c3fc8-107">下列範例會建立<xref:System.Windows.Controls.ListBox>並設定`VirtualizingStackPanel.VirtualizationMode`附加屬性<xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>若要在捲動時提高效能。</span><span class="sxs-lookup"><span data-stu-id="c3fc8-107">The following example creates a <xref:System.Windows.Controls.ListBox> and sets the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> to improve performance during scrolling.</span></span>  
  
## <a name="code"></a><span data-ttu-id="c3fc8-108">程式碼</span><span class="sxs-lookup"><span data-stu-id="c3fc8-108">Code</span></span>  
 [!code-xaml[RecycleItemContainerShippets#VirtualizationMode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizationmode)]  
  
 <span data-ttu-id="c3fc8-109">下列範例會顯示先前的範例使用的資料。</span><span class="sxs-lookup"><span data-stu-id="c3fc8-109">The following example shows the data that the previous example uses.</span></span>  
  
 [!code-csharp[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#listboxdata)]
 [!code-vb[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#listboxdata)]

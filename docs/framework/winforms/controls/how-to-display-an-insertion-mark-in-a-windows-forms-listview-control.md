---
title: 如何：在 Windows Form ListView 控制項中顯示插入標記
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ListView control [Windows Forms], drag operations
- graphics [Windows Forms], insertion marks
- drop and drag [Windows Forms], insertion marks
- insertion marks
ms.assetid: 88d0a15b-25fd-4dc3-a685-297351311940
ms.openlocfilehash: 62d105dc3c0b9aabc3699c12259e1624ac31a3a0
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960435"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a><span data-ttu-id="6a97a-102">如何：在 Windows Form ListView 控制項中顯示插入標記</span><span class="sxs-lookup"><span data-stu-id="6a97a-102">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>
<span data-ttu-id="6a97a-103"><xref:System.Windows.Forms.ListView> 控制項中的插入標記會向使用者顯示將會插入拖曳項目的點。</span><span class="sxs-lookup"><span data-stu-id="6a97a-103">The insertion mark in the <xref:System.Windows.Forms.ListView> control shows users the point where dragged items will be inserted.</span></span> <span data-ttu-id="6a97a-104">當使用者將項目拖曳至另外兩個項目之間的某個點時，插入標記會顯示該項目的預期新位置。</span><span class="sxs-lookup"><span data-stu-id="6a97a-104">When a user drags an item to a point between two other items, the insertion mark shows the item's expected new location.</span></span>  
  
 <span data-ttu-id="6a97a-105">下圖顯示插入標記：</span><span class="sxs-lookup"><span data-stu-id="6a97a-105">The following image shows an insertion mark:</span></span>  
  
 <span data-ttu-id="6a97a-106">![顯示 ListView 插入標記的螢幕擷取畫面。](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span><span class="sxs-lookup"><span data-stu-id="6a97a-106">![Screenshot that shows a ListView insertion mark.](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span></span>  
  
 <span data-ttu-id="6a97a-107">下列程式碼範例示範如何使用這項功能。</span><span class="sxs-lookup"><span data-stu-id="6a97a-107">The following code example demonstrates how to use this feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a97a-108">範例</span><span class="sxs-lookup"><span data-stu-id="6a97a-108">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6a97a-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="6a97a-109">Compiling the Code</span></span>  
 <span data-ttu-id="6a97a-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="6a97a-110">This example requires:</span></span>  
  
- <span data-ttu-id="6a97a-111">本系統和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="6a97a-111">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a97a-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="6a97a-112">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewInsertionMark>
- [<span data-ttu-id="6a97a-113">ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="6a97a-113">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="6a97a-114">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="6a97a-114">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="6a97a-115">逐步解說：在 Windows Forms 中執行拖放作業</span><span class="sxs-lookup"><span data-stu-id="6a97a-115">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)

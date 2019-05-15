---
title: 作法：管理 Windows Forms DataGridView 控制項中的資料行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DataGridView control [Windows Forms], manipulating columns
- columns [Windows Forms], manipulating
- data grids [Windows Forms], manipulating columns
ms.assetid: d8cfe6b3-bbab-4182-bec2-0517d9f1eaf6
ms.openlocfilehash: 1f964314b9fe2f4b1ca235f9e74ca80391a58105
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592340"
---
# <a name="how-to-manipulate-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="689e6-102">作法：管理 Windows Forms DataGridView 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="689e6-102">How to: Manipulate Columns in the Windows Forms DataGridView Control</span></span>

<span data-ttu-id="689e6-103">下列程式碼範例顯示使用 <xref:System.Windows.Forms.DataGridViewColumn> 類別屬性操作 <xref:System.Windows.Forms.DataGridView> 資料行的各種方式。</span><span class="sxs-lookup"><span data-stu-id="689e6-103">The following code example shows the various ways to manipulate <xref:System.Windows.Forms.DataGridView> columns using properties of the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>

## <a name="example"></a><span data-ttu-id="689e6-104">範例</span><span class="sxs-lookup"><span data-stu-id="689e6-104">Example</span></span>

[!code-cpp[System.Windows.Forms.DataGridView.ButtonDemos#100](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/CPP/DataGridViewColumnDemo.cpp#100)]
[!code-csharp[System.Windows.Forms.DataGridView.ButtonDemos#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/CS/DataGridViewColumnDemo.cs#100)]
[!code-vb[System.Windows.Forms.DataGridView.ButtonDemos#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/VB/datagridviewcolumndemo.vb#100)]

## <a name="compiling-the-code"></a><span data-ttu-id="689e6-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="689e6-105">Compiling the Code</span></span>

<span data-ttu-id="689e6-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="689e6-106">This example requires:</span></span>

- <span data-ttu-id="689e6-107">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="689e6-107">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="689e6-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="689e6-108">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewBand>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [<span data-ttu-id="689e6-109">在 Windows Forms DataGridView 控制項中利用儲存格、資料列和資料行進行程式設計</span><span class="sxs-lookup"><span data-stu-id="689e6-109">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)

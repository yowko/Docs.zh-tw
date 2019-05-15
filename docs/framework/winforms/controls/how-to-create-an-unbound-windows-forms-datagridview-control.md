---
title: 作法：建立未繫結的 Windows Forms DataGridView 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], unbound data
- DataGridView control [Windows Forms], displaying data without binding to a data source
- data [Windows Forms], unbound
ms.assetid: b5d4b47d-9a28-4d88-9dba-0a3c90fba71d
ms.openlocfilehash: c488d0221080454a82e4c80f89964df0ee62f068
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591644"
---
# <a name="how-to-create-an-unbound-windows-forms-datagridview-control"></a><span data-ttu-id="fd6ee-102">作法：建立未繫結的 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="fd6ee-102">How to: Create an Unbound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="fd6ee-103">下列程式碼範例示範如何以程式設計方式填入 <xref:System.Windows.Forms.DataGridView> 控制項，而不用將這個控制項繫結至資料來源。</span><span class="sxs-lookup"><span data-stu-id="fd6ee-103">The following code example demonstrates how to populate a <xref:System.Windows.Forms.DataGridView> control programmatically without binding it to a data source.</span></span> <span data-ttu-id="fd6ee-104">當您擁有想以資料表格式來顯示的少量資料時，這將會非常有用。</span><span class="sxs-lookup"><span data-stu-id="fd6ee-104">This is useful when you have a small amount of data that you want to display in a table format.</span></span>  
  
 <span data-ttu-id="fd6ee-105">如需這個程式碼範例的完整說明，請參閱[逐步解說：建立未繫結的 Windows Form DataGridView 控制項](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="fd6ee-105">For a complete explanation of this code example, see [Walkthrough: Creating an Unbound Windows Forms DataGridView Control](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd6ee-106">範例</span><span class="sxs-lookup"><span data-stu-id="fd6ee-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fd6ee-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="fd6ee-107">Compiling the Code</span></span>  
 <span data-ttu-id="fd6ee-108">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="fd6ee-108">This example requires:</span></span>  
  
- <span data-ttu-id="fd6ee-109">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="fd6ee-109">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd6ee-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd6ee-110">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="fd6ee-111">逐步解說：建立未繫結的 Windows Form DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="fd6ee-111">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)
- [<span data-ttu-id="fd6ee-112">在 Windows Forms DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="fd6ee-112">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="fd6ee-113">Windows Forms DataGridView 控制項的資料顯示模式</span><span class="sxs-lookup"><span data-stu-id="fd6ee-113">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)

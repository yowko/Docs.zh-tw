---
title: 存取繫結至 DataGridView 資料列的物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
ms.openlocfilehash: 0b9a4becb78ae817141728467c1e9ea5b693476d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743173"
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a><span data-ttu-id="195a3-102">如何：存取物件繫結至 Windows Form DataGridView 資料列</span><span class="sxs-lookup"><span data-stu-id="195a3-102">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>
<span data-ttu-id="195a3-103">有時候顯示儲存在商務物件集合中之資料表的資訊會很有用。</span><span class="sxs-lookup"><span data-stu-id="195a3-103">Sometimes it is useful to display a table of information stored in a collection of business objects.</span></span> <span data-ttu-id="195a3-104">當您繫結 <xref:System.Windows.Forms.DataGridView> 控制項至這類集合，則每個公用屬性會顯示在自己的資料行中​​，除非屬性已標示為不可由 <xref:System.ComponentModel.BrowsableAttribute> 瀏覽。</span><span class="sxs-lookup"><span data-stu-id="195a3-104">When you bind a <xref:System.Windows.Forms.DataGridView> control to such a collection, each public property is displayed in its own column unless the property has been marked non-browsable with a <xref:System.ComponentModel.BrowsableAttribute>.</span></span> <span data-ttu-id="195a3-105">例如，`Customer` 物件的集合可能有 [名稱] 和 [位址] 等資料行。</span><span class="sxs-lookup"><span data-stu-id="195a3-105">For example, a collection of `Customer` objects would have columns such as **Name** and **Address**.</span></span>  
  
 <span data-ttu-id="195a3-106">如果這些物件包含其他資訊和您想要存取的程式碼，您可透過資料列物件取得。</span><span class="sxs-lookup"><span data-stu-id="195a3-106">If these objects contain additional information and code that you want to access, you can reach it through row objects.</span></span> <span data-ttu-id="195a3-107">在下列程式碼範例中，使用者可以選取多個資料列，然後按一下按鈕將發票傳送至每個對應的客戶。</span><span class="sxs-lookup"><span data-stu-id="195a3-107">In the following code example, users can select multiple rows and click a button to send an invoice to each of the corresponding customers.</span></span>  
  
### <a name="to-access-row-bound-objects"></a><span data-ttu-id="195a3-108">若要存取資料列繫結物件</span><span class="sxs-lookup"><span data-stu-id="195a3-108">To access row-bound objects</span></span>  
  
- <span data-ttu-id="195a3-109">請使用 <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="195a3-109">Use the <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="195a3-110">範例</span><span class="sxs-lookup"><span data-stu-id="195a3-110">Example</span></span>  
 <span data-ttu-id="195a3-111">完整的程式碼範例包含簡單的 `Customer` 實作以及繫結 <xref:System.Windows.Forms.DataGridView> 至包含幾個 `Customer` 物件的 <xref:System.Collections.ArrayList>。</span><span class="sxs-lookup"><span data-stu-id="195a3-111">The complete code example includes a simple `Customer` implementation and binds the <xref:System.Windows.Forms.DataGridView> to an <xref:System.Collections.ArrayList> containing a few `Customer` objects.</span></span> <span data-ttu-id="195a3-112"><xref:System.Windows.Forms.Button?displayProperty=nameWithType> 的 <xref:System.Windows.Forms.Control.Click> 事件處理常式必須透過資料列存取 `Customer` 物件，因為客戶集合並不能從 <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> 事件處理常式的外部存取。</span><span class="sxs-lookup"><span data-stu-id="195a3-112">The <xref:System.Windows.Forms.Control.Click> event handler of the <xref:System.Windows.Forms.Button?displayProperty=nameWithType> must access the `Customer` objects through the rows, because the customer collection is not accessible outside the <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> event handler.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="195a3-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="195a3-113">Compiling the Code</span></span>  
 <span data-ttu-id="195a3-114">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="195a3-114">This example requires:</span></span>  
  
- <span data-ttu-id="195a3-115">本系統和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="195a3-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="195a3-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="195a3-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>
- [<span data-ttu-id="195a3-117">在 Windows Forms DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="195a3-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="195a3-118">操作說明：將物件繫結至 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="195a3-118">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)

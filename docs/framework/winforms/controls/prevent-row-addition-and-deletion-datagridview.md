---
title: 如何：防止在 Windows Form DataGridView 控制項中新增和刪除資料列
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], disabling data entry
- data entry [Windows Forms], disabling in grids
- data grids [Windows Forms], disabling data entry
ms.assetid: ef9539ce-539b-404e-84b6-ac282b64b88c
ms.openlocfilehash: 6263c92e6a981983c19e9d7f2357c581bee5ec07
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "45969349"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="8168d-102">如何：防止在 Windows Form DataGridView 控制項中新增和刪除資料列</span><span class="sxs-lookup"><span data-stu-id="8168d-102">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="8168d-103">有時候您會想要防止使用者在您的 <xref:System.Windows.Forms.DataGridView> 控制項中輸入新的資料列或刪除現有的資料列。</span><span class="sxs-lookup"><span data-stu-id="8168d-103">Sometimes you will want to prevent users from entering new rows of data or deleting existing rows in your <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="8168d-104"><xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> 屬性會指出新記錄的資料列是否出現在控制項的底部，而 <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> 屬性會指出是否可以移除資料列。</span><span class="sxs-lookup"><span data-stu-id="8168d-104">The <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property indicates whether the row for new records is present at the bottom of the control, while the <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> property indicates whether rows can be removed.</span></span> <span data-ttu-id="8168d-105">下列程式碼範例會使用這些屬性，也將會設定 <xref:System.Windows.Forms.DataGridView.ReadOnly%2A> 屬性使控制項為完全唯讀。</span><span class="sxs-lookup"><span data-stu-id="8168d-105">The following code example uses these properties and also sets the <xref:System.Windows.Forms.DataGridView.ReadOnly%2A> property to make the control entirely read-only.</span></span>  
  
 <span data-ttu-id="8168d-106">在 Visual Studio 中會支援這項工作。</span><span class="sxs-lookup"><span data-stu-id="8168d-106">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="8168d-107">另請參閱[如何： 避免資料列新增和刪除 Windows Form DataGridView 控制項使用設計工具](https://msdn.microsoft.com/library/k5c88sw3\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="8168d-107">Also see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer](https://msdn.microsoft.com/library/k5c88sw3\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8168d-108">範例</span><span class="sxs-lookup"><span data-stu-id="8168d-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#090](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#090)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#090](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#090)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8168d-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="8168d-109">Compiling the Code</span></span>  
 <span data-ttu-id="8168d-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="8168d-110">This example requires:</span></span>  
  
-   <span data-ttu-id="8168d-111">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="8168d-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="8168d-112"><xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="8168d-112">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8168d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8168d-113">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ReadOnly%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="8168d-114">Windows Forms DataGridView 控制項中的基本資料行、資料列和儲存格功能</span><span class="sxs-lookup"><span data-stu-id="8168d-114">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)

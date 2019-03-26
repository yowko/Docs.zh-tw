---
title: HOW TO：停用在 Windows Form DataGridView 控制項按鈕資料行中的按鈕
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], disabling buttons
- buttons [Windows Forms], disabling in button columns
- DataGridView control [Windows Forms], disabling button cells
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
ms.openlocfilehash: 7ce363b74ee4551e3af00169c1d2edaffe3dbd52
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711361"
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="4fa00-102">HOW TO：停用在 Windows Form DataGridView 控制項按鈕資料行中的按鈕</span><span class="sxs-lookup"><span data-stu-id="4fa00-102">How to: Disable Buttons in a Button Column in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="4fa00-103"><xref:System.Windows.Forms.DataGridView> 控制項包含 <xref:System.Windows.Forms.DataGridViewButtonCell> 類別，可使用按鈕等使用者介面 (UI) 來顯示儲存格。</span><span class="sxs-lookup"><span data-stu-id="4fa00-103">The <xref:System.Windows.Forms.DataGridView> control includes the <xref:System.Windows.Forms.DataGridViewButtonCell> class for displaying cells with a user interface (UI) like a button.</span></span> <span data-ttu-id="4fa00-104">但是，<xref:System.Windows.Forms.DataGridViewButtonCell> 未提供任何方法，來停用儲存格所顯示的按鈕外觀。</span><span class="sxs-lookup"><span data-stu-id="4fa00-104">However, <xref:System.Windows.Forms.DataGridViewButtonCell> does not provide a way to disable the appearance of the button displayed by the cell.</span></span>  
  
 <span data-ttu-id="4fa00-105">下列程式碼範例示範如何自訂 <xref:System.Windows.Forms.DataGridViewButtonCell> 類別，來顯示可呈現為停用狀態的按鈕。</span><span class="sxs-lookup"><span data-stu-id="4fa00-105">The following code example demonstrates how to customize the <xref:System.Windows.Forms.DataGridViewButtonCell> class to display buttons that can appear disabled.</span></span> <span data-ttu-id="4fa00-106">這個範例會定義新的儲存格類型 `DataGridViewDisableButtonCell`，這個類型衍生自 <xref:System.Windows.Forms.DataGridViewButtonCell>。</span><span class="sxs-lookup"><span data-stu-id="4fa00-106">The example defines a new cell type, `DataGridViewDisableButtonCell`, that derives from <xref:System.Windows.Forms.DataGridViewButtonCell>.</span></span> <span data-ttu-id="4fa00-107">這個儲存格類型提供了新的 `Enabled` 屬性，可設定為 `false`，以便在儲存格中繪製停用的按鈕。</span><span class="sxs-lookup"><span data-stu-id="4fa00-107">This cell type provides a new `Enabled` property that can be set to `false` to draw a disabled button in the cell.</span></span> <span data-ttu-id="4fa00-108">這個範例也會定義新的資料行類型 `DataGridViewDisableButtonColumn`，以顯示 `DataGridViewDisableButtonCell` 物件。</span><span class="sxs-lookup"><span data-stu-id="4fa00-108">The example also defines a new column type, `DataGridViewDisableButtonColumn`, that displays `DataGridViewDisableButtonCell` objects.</span></span> <span data-ttu-id="4fa00-109">為了示範這個新的儲存格和資料行類型，在父 <xref:System.Windows.Forms.DataGridView> 中每個 <xref:System.Windows.Forms.DataGridViewCheckBoxCell> 的目前值會決定同一個資料列中 `DataGridViewDisableButtonCell` 的 `Enabled` 屬性是 `true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="4fa00-109">To demonstrate this new cell and column type, the current value of each <xref:System.Windows.Forms.DataGridViewCheckBoxCell> in the parent <xref:System.Windows.Forms.DataGridView> determines whether the `Enabled` property of the `DataGridViewDisableButtonCell` in the same row is `true` or `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4fa00-110">當您自 <xref:System.Windows.Forms.DataGridViewCell> 或 <xref:System.Windows.Forms.DataGridViewColumn> 中衍生時，以及在衍生類別中加入新的屬性時，請務必覆寫 `Clone` 方法，在複製作業期間複製新的屬性。</span><span class="sxs-lookup"><span data-stu-id="4fa00-110">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="4fa00-111">您也應該呼叫基底類別的 `Clone` 方法，以便將基底類別的屬性複製到新的儲存格或資料行。</span><span class="sxs-lookup"><span data-stu-id="4fa00-111">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fa00-112">範例</span><span class="sxs-lookup"><span data-stu-id="4fa00-112">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4fa00-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="4fa00-113">Compiling the Code</span></span>  
 <span data-ttu-id="4fa00-114">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="4fa00-114">This example requires:</span></span>  
  
-   <span data-ttu-id="4fa00-115">System、System.Drawing、System.Windows.Forms 和 System.Windows.Forms.VisualStyles 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="4fa00-115">References to the System, System.Drawing, System.Windows.Forms and System.Windows.Forms.VisualStyles assemblies.</span></span>  
  
 <span data-ttu-id="4fa00-116">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="4fa00-116">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="4fa00-117">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="4fa00-117">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fa00-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fa00-118">See also</span></span>
- [<span data-ttu-id="4fa00-119">自訂 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="4fa00-119">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="4fa00-120">DataGridView 控制項架構</span><span class="sxs-lookup"><span data-stu-id="4fa00-120">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
- [<span data-ttu-id="4fa00-121">Windows Forms DataGridView 控制項中的資料行類型</span><span class="sxs-lookup"><span data-stu-id="4fa00-121">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)

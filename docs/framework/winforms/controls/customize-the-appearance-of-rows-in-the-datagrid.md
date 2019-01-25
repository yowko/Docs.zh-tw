---
title: HOW TO：自訂 Windows Form DataGridView 控制項中的資料列的外觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- rows [Windows Forms], customizing in DataGridView control
- DataGridView control [Windows Forms], customizing rows
ms.assetid: d40b53d2-7e7c-48c5-8570-6e79d15c3bbb
ms.openlocfilehash: 6ec3765eb667f8a249afa815400eb7f1edbec3dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632942"
---
# <a name="how-to-customize-the-appearance-of-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="ff365-102">HOW TO：自訂 Windows Form DataGridView 控制項中的資料列的外觀</span><span class="sxs-lookup"><span data-stu-id="ff365-102">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="ff365-103">您可以藉由處理一個或兩個 <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> 和 <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> 事件，來控制 <xref:System.Windows.Forms.DataGridView> 資料列的外觀 。</span><span class="sxs-lookup"><span data-stu-id="ff365-103">You can control the appearance of <xref:System.Windows.Forms.DataGridView> rows by handling one or both of the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> and <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> events.</span></span> <span data-ttu-id="ff365-104">這些事件經過設計，以便您可以在 <xref:System.Windows.Forms.DataGridView> 控制項繪製其餘部分的時候只繪製您想要的部分。</span><span class="sxs-lookup"><span data-stu-id="ff365-104">These events are designed so that you can paint only what you want to while letting the <xref:System.Windows.Forms.DataGridView> control paint the rest.</span></span> <span data-ttu-id="ff365-105">例如，如果您想要繪製自訂背景，您可以處理 <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> 事件，然後讓個別儲存格繪製自己的前景內容。</span><span class="sxs-lookup"><span data-stu-id="ff365-105">For example, if you want to paint a custom background, you can handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event and let the individual cells paint their own foreground content.</span></span> <span data-ttu-id="ff365-106">或者，您可以讓儲存格繪製自己，並加入自訂前景內容到 <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> 事件的處理常式。</span><span class="sxs-lookup"><span data-stu-id="ff365-106">Alternately, you can let the cells paint themselves and add custom foreground content in a handler for the <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="ff365-107">您也可以停用儲存格繪製，自行在 <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> 事件處理常式中繪製全部內容。</span><span class="sxs-lookup"><span data-stu-id="ff365-107">You can also disable cell painting and paint everything yourself in a <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event handler.</span></span>  
  
 <span data-ttu-id="ff365-108">下列程式碼範例會實作兩個事件的處理常式，以提供漸層選取背景和某些跨越多個資料行的自訂前景內容。</span><span class="sxs-lookup"><span data-stu-id="ff365-108">The following code example implements handlers for both events in order to provide a gradient selection background and some custom foreground content that spans multiple columns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff365-109">範例</span><span class="sxs-lookup"><span data-stu-id="ff365-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewRowPainting#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/CS/datagridviewrowpainting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewRowPainting#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/VB/datagridviewrowpainting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ff365-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ff365-110">Compiling the Code</span></span>  
 <span data-ttu-id="ff365-111">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="ff365-111">This example requires:</span></span>  
  
-   <span data-ttu-id="ff365-112">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="ff365-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="ff365-113">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="ff365-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="ff365-114">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="ff365-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="ff365-115">另請參閱[How to:編譯並執行完整的 Windows Form 程式碼範例使用 Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="ff365-115">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff365-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff365-116">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>
- [<span data-ttu-id="ff365-117">自訂 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="ff365-117">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="ff365-118">DataGridView 控制項架構</span><span class="sxs-lookup"><span data-stu-id="ff365-118">DataGridView Control Architecture</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)

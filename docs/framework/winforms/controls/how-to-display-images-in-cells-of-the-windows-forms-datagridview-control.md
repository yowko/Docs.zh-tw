---
title: 在 DataGridView 控制項的儲存格中顯示影像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], displaying images
- data grids [Windows Forms], displaying in grids
- DataGridView control [Windows Forms], displaying images
- data grids [Windows Forms], displaying images in cells
ms.assetid: 53b13d31-1b56-476d-9ab4-18bfac138a22
ms.openlocfilehash: e0e125c816877875b80e0f20887d9beee443577a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740282"
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="da5e2-102">如何：顯示 Windows Form DataGridView 控制項的儲存格影像</span><span class="sxs-lookup"><span data-stu-id="da5e2-102">How to: Display Images in Cells of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="da5e2-103">圖片或圖形是您可以在資料列中顯示的其中一個值。</span><span class="sxs-lookup"><span data-stu-id="da5e2-103">A picture or graphic is one of the values that you can display in a row of data.</span></span> <span data-ttu-id="da5e2-104">這些圖形經常會採用員工相片或公司標誌的形式。</span><span class="sxs-lookup"><span data-stu-id="da5e2-104">Frequently, these graphics take the form of an employee's photograph or a company logo.</span></span>  
  
 <span data-ttu-id="da5e2-105">當您在 <xref:System.Windows.Forms.DataGridView> 控制項中顯示資料時，合併圖片就很簡單。</span><span class="sxs-lookup"><span data-stu-id="da5e2-105">Incorporating pictures is simple when you display data within the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="da5e2-106"><xref:System.Windows.Forms.DataGridView> 控制項原本就會處理 <xref:System.Drawing.Image> 類別支援的任何影像格式，以及某些資料庫所使用的 OLE 圖片格式。</span><span class="sxs-lookup"><span data-stu-id="da5e2-106">The <xref:System.Windows.Forms.DataGridView> control natively handles any image format supported by the <xref:System.Drawing.Image> class, as well as the OLE picture format used by some databases.</span></span>  
  
 <span data-ttu-id="da5e2-107">如果 <xref:System.Windows.Forms.DataGridView> 控制項的資料來源有一欄影像，<xref:System.Windows.Forms.DataGridView> 控制項就會自動顯示它們。</span><span class="sxs-lookup"><span data-stu-id="da5e2-107">If the <xref:System.Windows.Forms.DataGridView> control's data source has a column of images, they will be displayed automatically by the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <span data-ttu-id="da5e2-108">下列程式碼範例示範如何從內嵌資源將圖示解壓縮，並將其轉換成點陣圖，以顯示在影像資料行的每個資料格中。</span><span class="sxs-lookup"><span data-stu-id="da5e2-108">The following code example demonstrates how to extract an icon from an embedded resource and convert it to a bitmap for display in every cell of an image column.</span></span> <span data-ttu-id="da5e2-109">如需以對應影像取代文字資料格值的另一個範例，請參閱[如何：在 Windows Forms DataGridView 控制項中自訂資料格式](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="da5e2-109">For another example that replaces textual cell values with corresponding images, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="da5e2-110">範例</span><span class="sxs-lookup"><span data-stu-id="da5e2-110">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="da5e2-111">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="da5e2-111">Compiling the Code</span></span>  
 <span data-ttu-id="da5e2-112">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="da5e2-112">This example requires:</span></span>  
  
- <span data-ttu-id="da5e2-113">名為 <xref:System.Windows.Forms.DataGridView> 的 `dataGridView1` 控制項。</span><span class="sxs-lookup"><span data-stu-id="da5e2-113">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="da5e2-114">名為 `tree.ico`的內嵌圖示資源。</span><span class="sxs-lookup"><span data-stu-id="da5e2-114">An embedded icon resource named `tree.ico`.</span></span>  
  
- <span data-ttu-id="da5e2-115"><xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType> 和 <xref:System.Drawing?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="da5e2-115">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da5e2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da5e2-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="da5e2-117">Windows Forms DataGridView 控制項中的基本資料行、資料列和儲存格功能</span><span class="sxs-lookup"><span data-stu-id="da5e2-117">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="da5e2-118">操作說明：自訂 Windows Forms DataGridView 控制項中的資料格式</span><span class="sxs-lookup"><span data-stu-id="da5e2-118">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)

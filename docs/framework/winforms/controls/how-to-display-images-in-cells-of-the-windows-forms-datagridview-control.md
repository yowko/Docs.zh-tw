---
title: HOW TO：在 Windows Forms DataGridView 控制項的儲存格中顯示影像
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
ms.openlocfilehash: 90aaff419ecc2c890a8b3802f3aaf12092febb73
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082991"
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="d1164-102">HOW TO：在 Windows Forms DataGridView 控制項的儲存格中顯示影像</span><span class="sxs-lookup"><span data-stu-id="d1164-102">How to: Display Images in Cells of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="d1164-103">圖片或圖形是其中一個值，您可以將資料列中顯示。</span><span class="sxs-lookup"><span data-stu-id="d1164-103">A picture or graphic is one of the values that you can display in a row of data.</span></span> <span data-ttu-id="d1164-104">通常，這些圖形的形式是員工的照片或公司標誌。</span><span class="sxs-lookup"><span data-stu-id="d1164-104">Frequently, these graphics take the form of an employee's photograph or a company logo.</span></span>  
  
 <span data-ttu-id="d1164-105">將圖片很簡單，當您顯示內的資料時<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="d1164-105">Incorporating pictures is simple when you display data within the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="d1164-106"><xref:System.Windows.Forms.DataGridView>控制項以原生方式處理支援之任何映像格式<xref:System.Drawing.Image>類別，如 OLE 圖片某些資料庫所使用的格式。</span><span class="sxs-lookup"><span data-stu-id="d1164-106">The <xref:System.Windows.Forms.DataGridView> control natively handles any image format supported by the <xref:System.Drawing.Image> class, as well as the OLE picture format used by some databases.</span></span>  
  
 <span data-ttu-id="d1164-107">如果<xref:System.Windows.Forms.DataGridView>控制項的資料來源的資料行的映像，則會自動顯示<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="d1164-107">If the <xref:System.Windows.Forms.DataGridView> control's data source has a column of images, they will be displayed automatically by the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <span data-ttu-id="d1164-108">下列程式碼範例示範如何從內嵌資源擷取圖示，並將它轉換成 image 資料行的每個資料格中顯示的點陣圖。</span><span class="sxs-lookup"><span data-stu-id="d1164-108">The following code example demonstrates how to extract an icon from an embedded resource and convert it to a bitmap for display in every cell of an image column.</span></span> <span data-ttu-id="d1164-109">如需文字的資料格的值取代成對應的映像的其他範例，請參閱[How to:自訂 Windows Form DataGridView 控制項中的資料格式](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="d1164-109">For another example that replaces textual cell values with corresponding images, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1164-110">範例</span><span class="sxs-lookup"><span data-stu-id="d1164-110">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d1164-111">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="d1164-111">Compiling the Code</span></span>  
 <span data-ttu-id="d1164-112">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="d1164-112">This example requires:</span></span>  
  
-   <span data-ttu-id="d1164-113">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="d1164-113">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="d1164-114">名為內嵌的圖示資源`tree.ico`。</span><span class="sxs-lookup"><span data-stu-id="d1164-114">An embedded icon resource named `tree.ico`.</span></span>  
  
-   <span data-ttu-id="d1164-115"><xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType> 和 <xref:System.Drawing?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="d1164-115">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1164-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1164-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="d1164-117">Windows Form DataGridView 控制項中的基本資料行、資料列和儲存格功能</span><span class="sxs-lookup"><span data-stu-id="d1164-117">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="d1164-118">HOW TO：自訂 Windows Forms DataGridView 控制項中的資料格式</span><span class="sxs-lookup"><span data-stu-id="d1164-118">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)

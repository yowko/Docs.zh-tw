---
title: HOW TO：在 Windows Forms DataGridView 控制項中使用資料列範本自訂資料列
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
ms.openlocfilehash: cb3a826262a49a8653e3a344bd126d434f2522dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073030"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="c7bb6-102">HOW TO：在 Windows Forms DataGridView 控制項中使用資料列範本自訂資料列</span><span class="sxs-lookup"><span data-stu-id="c7bb6-102">How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="c7bb6-103"><xref:System.Windows.Forms.DataGridView>控制項會使用做為基礎的資料列範本，透過資料繫結中，或當您呼叫時，它將加入此控制項的所有資料列<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType>方法，而不指定要使用現有的資料列。</span><span class="sxs-lookup"><span data-stu-id="c7bb6-103">The <xref:System.Windows.Forms.DataGridView> control uses the row template as a basis for all rows that it adds to the control either through data binding or when you call the <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> method without specifying an existing row to use.</span></span>  
  
 <span data-ttu-id="c7bb6-104">資料列範本可讓您更有效控制的外觀和行為的資料列<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>屬性提供。</span><span class="sxs-lookup"><span data-stu-id="c7bb6-104">The row template gives you greater control over the appearance and behavior of rows than the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> property provides.</span></span> <span data-ttu-id="c7bb6-105">資料列範本後，您可以設定任何<xref:System.Windows.Forms.DataGridViewRow>屬性，包括<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>。</span><span class="sxs-lookup"><span data-stu-id="c7bb6-105">With the row template, you can set any <xref:System.Windows.Forms.DataGridViewRow> properties, including <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.</span></span>  
  
 <span data-ttu-id="c7bb6-106">有一些情況下，您必須在其中使用來達成特定效果的資料列範本。</span><span class="sxs-lookup"><span data-stu-id="c7bb6-106">There are some situations where you must use the row template to achieve a particular effect.</span></span> <span data-ttu-id="c7bb6-107">例如，資料列高度資訊無法儲存在<xref:System.Windows.Forms.DataGridViewCellStyle>，因此您必須使用資料列範本來變更所有資料列所使用的預設高度。</span><span class="sxs-lookup"><span data-stu-id="c7bb6-107">For example, row height information cannot be stored in a <xref:System.Windows.Forms.DataGridViewCellStyle>, so you must use a row template to change the default height used by all rows.</span></span> <span data-ttu-id="c7bb6-108">資料列範本也適用於當您建立您自己的類別衍生自<xref:System.Windows.Forms.DataGridViewRow>和您想要您新的資料列加入至控制項時所使用的自訂類型。</span><span class="sxs-lookup"><span data-stu-id="c7bb6-108">The row template is also useful when you create your own classes derived from <xref:System.Windows.Forms.DataGridViewRow> and you want your custom type used when new rows are added to the control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7bb6-109">只有在加入資料列時，才使用資料列範本。</span><span class="sxs-lookup"><span data-stu-id="c7bb6-109">The row template is used only when rows are added.</span></span> <span data-ttu-id="c7bb6-110">您無法變更現有的資料列，藉由變更資料列範本。</span><span class="sxs-lookup"><span data-stu-id="c7bb6-110">You cannot change existing rows by changing the row template.</span></span>  
  
### <a name="to-use-the-row-template"></a><span data-ttu-id="c7bb6-111">若要使用資料列範本</span><span class="sxs-lookup"><span data-stu-id="c7bb6-111">To use the row template</span></span>  
  
-   <span data-ttu-id="c7bb6-112">從擷取的物件上設定屬性<xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="c7bb6-112">Set properties on the object retrieved from the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c7bb6-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="c7bb6-113">Compiling the Code</span></span>  
 <span data-ttu-id="c7bb6-114">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="c7bb6-114">This example requires:</span></span>  
  
-   <span data-ttu-id="c7bb6-115">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="c7bb6-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="c7bb6-116"><xref:System?displayProperty=nameWithType>、<xref:System.Drawing?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="c7bb6-116">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7bb6-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7bb6-117">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c7bb6-118">Windows Form DataGridView 控制項中的基本格式化和樣式設定</span><span class="sxs-lookup"><span data-stu-id="c7bb6-118">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="c7bb6-119">Windows Form DataGridView 控制項中的儲存格樣式</span><span class="sxs-lookup"><span data-stu-id="c7bb6-119">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)

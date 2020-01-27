---
title: 在資料系結 DataGridView 控制項中自動產生資料行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], autogenerating columns
- columns [Windows Forms], autogenerating
- DataGridView control [Windows Forms], data-bound columns
ms.assetid: 699f6f9e-6aa5-4811-902b-6a2c57dec7d6
ms.openlocfilehash: 860e640e095537358d2f8778c810aa577e9d7ff0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746240"
---
# <a name="how-to-autogenerate-columns-in-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="17a79-102">如何：在資料繫結 Windows Form DataGridView 控制項中自動產生資料行</span><span class="sxs-lookup"><span data-stu-id="17a79-102">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="17a79-103">下列程式碼範例示範如何在 <xref:System.Windows.Forms.DataGridView> 控制項中顯示系結資料來源中的資料行。</span><span class="sxs-lookup"><span data-stu-id="17a79-103">The following code example demonstrates how to display columns from a bound data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="17a79-104">當 <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> 屬性值 `true` （預設）時，就會為數據來源資料表中的每個資料行建立 <xref:System.Windows.Forms.DataGridViewColumn>。</span><span class="sxs-lookup"><span data-stu-id="17a79-104">When the <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> property value is `true` (the default), a <xref:System.Windows.Forms.DataGridViewColumn> is created for each column in the data source table.</span></span>  
  
 <span data-ttu-id="17a79-105">當您設定 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> 屬性時，如果 <xref:System.Windows.Forms.DataGridView> 控制項已有資料行，則會將現有的系結資料行與資料來源中的資料行進行比較，並在每次符合時保留。</span><span class="sxs-lookup"><span data-stu-id="17a79-105">If the <xref:System.Windows.Forms.DataGridView> control already has columns when you set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property, the existing bound columns are compared to the columns in the data source and preserved whenever there is a match.</span></span> <span data-ttu-id="17a79-106">未系結的資料行一律會保留。</span><span class="sxs-lookup"><span data-stu-id="17a79-106">Unbound columns are always preserved.</span></span> <span data-ttu-id="17a79-107">移除資料來源中沒有相符項的系結資料行。</span><span class="sxs-lookup"><span data-stu-id="17a79-107">Bound columns for which there is no match in the data source are removed.</span></span> <span data-ttu-id="17a79-108">在資料來源中，如果控制項中沒有符合的資料行，則會產生新的 <xref:System.Windows.Forms.DataGridViewColumn> 物件，並加入至 <xref:System.Windows.Forms.DataGridView.Columns%2A> 集合的結尾。</span><span class="sxs-lookup"><span data-stu-id="17a79-108">Columns in the data source for which there is no match in the control generate new <xref:System.Windows.Forms.DataGridViewColumn> objects, which are added to the end of the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17a79-109">範例</span><span class="sxs-lookup"><span data-stu-id="17a79-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#020](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#020)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#020](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#020)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="17a79-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="17a79-110">Compiling the Code</span></span>  
 <span data-ttu-id="17a79-111">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="17a79-111">This example requires:</span></span>  
  
- <span data-ttu-id="17a79-112">名為 `customersDataGridView` 的 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="17a79-112">A <xref:System.Windows.Forms.DataGridView> control named `customersDataGridView`.</span></span>  
  
- <span data-ttu-id="17a79-113">名為 `customersDataSet` 的 <xref:System.Data.DataSet> 物件，其具有名為 `Customers`的資料表。</span><span class="sxs-lookup"><span data-stu-id="17a79-113">A <xref:System.Data.DataSet> object named `customersDataSet` that has a table named `Customers`.</span></span>  
  
- <span data-ttu-id="17a79-114"><xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType>、<xref:System.Data?displayProperty=nameWithType> 和 <xref:System.Xml?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="17a79-114">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, and <xref:System.Xml?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17a79-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="17a79-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A?displayProperty=nameWithType>
- [<span data-ttu-id="17a79-116">在 Windows Forms DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="17a79-116">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="17a79-117">操作說明：移除 Windows Forms DataGridView 控制項中自動產生的資料行</span><span class="sxs-lookup"><span data-stu-id="17a79-117">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)

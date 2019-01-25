---
title: HOW TO：自動產生資料繫結 Windows Form DataGridView 控制項中的資料行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], autogenerating columns
- columns [Windows Forms], autogenerating
- DataGridView control [Windows Forms], data-bound columns
ms.assetid: 699f6f9e-6aa5-4811-902b-6a2c57dec7d6
ms.openlocfilehash: 1968968461edb475be4cd30261a66b53cd7f0e94
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554006"
---
# <a name="how-to-autogenerate-columns-in-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="dafb9-102">HOW TO：自動產生資料繫結 Windows Form DataGridView 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="dafb9-102">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="dafb9-103">下列程式碼範例示範如何顯示資料行中的繫結的資料來源從<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="dafb9-103">The following code example demonstrates how to display columns from a bound data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="dafb9-104">當<xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A>屬性值是`true`（預設值），<xref:System.Windows.Forms.DataGridViewColumn>建立每個資料行中的資料來源資料表。</span><span class="sxs-lookup"><span data-stu-id="dafb9-104">When the <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> property value is `true` (the default), a <xref:System.Windows.Forms.DataGridViewColumn> is created for each column in the data source table.</span></span>  
  
 <span data-ttu-id="dafb9-105">如果<xref:System.Windows.Forms.DataGridView>控制項已有資料行，當您設定<xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>屬性、 現有的繫結資料行相較於資料來源中的資料行，而相符項目時予以儲存。</span><span class="sxs-lookup"><span data-stu-id="dafb9-105">If the <xref:System.Windows.Forms.DataGridView> control already has columns when you set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property, the existing bound columns are compared to the columns in the data source and preserved whenever there is a match.</span></span> <span data-ttu-id="dafb9-106">未繫結的資料行，一律會保留。</span><span class="sxs-lookup"><span data-stu-id="dafb9-106">Unbound columns are always preserved.</span></span> <span data-ttu-id="dafb9-107">會移除資料來源中的沒有相符項目是繫結的資料行。</span><span class="sxs-lookup"><span data-stu-id="dafb9-107">Bound columns for which there is no match in the data source are removed.</span></span> <span data-ttu-id="dafb9-108">控制項中的沒有相符項目是資料來源中的資料行產生新<xref:System.Windows.Forms.DataGridViewColumn>物件，會新增至結尾<xref:System.Windows.Forms.DataGridView.Columns%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="dafb9-108">Columns in the data source for which there is no match in the control generate new <xref:System.Windows.Forms.DataGridViewColumn> objects, which are added to the end of the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dafb9-109">範例</span><span class="sxs-lookup"><span data-stu-id="dafb9-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#020](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#020)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#020](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#020)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dafb9-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="dafb9-110">Compiling the Code</span></span>  
 <span data-ttu-id="dafb9-111">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="dafb9-111">This example requires:</span></span>  
  
-   <span data-ttu-id="dafb9-112">名為 `customersDataGridView` 的 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="dafb9-112">A <xref:System.Windows.Forms.DataGridView> control named `customersDataGridView`.</span></span>  
  
-   <span data-ttu-id="dafb9-113">A<xref:System.Data.DataSet>名為物件`customersDataSet`具有一個名為資料表`Customers`。</span><span class="sxs-lookup"><span data-stu-id="dafb9-113">A <xref:System.Data.DataSet> object named `customersDataSet` that has a table named `Customers`.</span></span>  
  
-   <span data-ttu-id="dafb9-114"><xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType>、<xref:System.Data?displayProperty=nameWithType> 和 <xref:System.Xml?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="dafb9-114">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, and <xref:System.Xml?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dafb9-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dafb9-115">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A?displayProperty=nameWithType>
- [<span data-ttu-id="dafb9-116">在 Windows Forms DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="dafb9-116">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="dafb9-117">如何：移除 Windows Form DataGridView 控制項中的自動產生資料行</span><span class="sxs-lookup"><span data-stu-id="dafb9-117">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/remove-autogenerated-columns-from-a-wf-datagridview-control.md)

---
title: "如何：在資料繫結 Windows Form DataGridView 控制項中自動產生資料行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], autogenerating columns
- columns [Windows Forms], autogenerating
- DataGridView control [Windows Forms], data-bound columns
ms.assetid: 699f6f9e-6aa5-4811-902b-6a2c57dec7d6
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e1d6a790f8a43f4ea2f9d3ad2cdb282186554da6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-autogenerate-columns-in-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="876de-102">如何：在資料繫結 Windows Form DataGridView 控制項中自動產生資料行</span><span class="sxs-lookup"><span data-stu-id="876de-102">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="876de-103">下列程式碼範例示範如何顯示資料行中的繫結的資料來源從<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="876de-103">The following code example demonstrates how to display columns from a bound data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="876de-104">當<xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A>屬性值是`true`（預設）、<xref:System.Windows.Forms.DataGridViewColumn>建立每個資料行的資料來源資料表中。</span><span class="sxs-lookup"><span data-stu-id="876de-104">When the <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> property value is `true` (the default), a <xref:System.Windows.Forms.DataGridViewColumn> is created for each column in the data source table.</span></span>  
  
 <span data-ttu-id="876de-105">如果<xref:System.Windows.Forms.DataGridView>控制項已經有資料行，當您設定<xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>屬性，現有的繫結資料行是相較於資料來源中的資料行和相符項目時，會保留。</span><span class="sxs-lookup"><span data-stu-id="876de-105">If the <xref:System.Windows.Forms.DataGridView> control already has columns when you set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property, the existing bound columns are compared to the columns in the data source and preserved whenever there is a match.</span></span> <span data-ttu-id="876de-106">未繫結的資料行一定會被保留。</span><span class="sxs-lookup"><span data-stu-id="876de-106">Unbound columns are always preserved.</span></span> <span data-ttu-id="876de-107">會移除資料來源中的沒有相符項目是繫結的資料行。</span><span class="sxs-lookup"><span data-stu-id="876de-107">Bound columns for which there is no match in the data source are removed.</span></span> <span data-ttu-id="876de-108">在控制項中的沒有相符項目是資料來源中的資料行產生新的<xref:System.Windows.Forms.DataGridViewColumn>物件加入至結尾<xref:System.Windows.Forms.DataGridView.Columns%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="876de-108">Columns in the data source for which there is no match in the control generate new <xref:System.Windows.Forms.DataGridViewColumn> objects, which are added to the end of the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="876de-109">範例</span><span class="sxs-lookup"><span data-stu-id="876de-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#020](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#020)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#020](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#020)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="876de-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="876de-110">Compiling the Code</span></span>  
 <span data-ttu-id="876de-111">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="876de-111">This example requires:</span></span>  
  
-   <span data-ttu-id="876de-112">名為 `customersDataGridView` 的 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="876de-112">A <xref:System.Windows.Forms.DataGridView> control named `customersDataGridView`.</span></span>  
  
-   <span data-ttu-id="876de-113">A<xref:System.Data.DataSet>名為物件`customersDataSet`具有名為的資料表`Customers`。</span><span class="sxs-lookup"><span data-stu-id="876de-113">A <xref:System.Data.DataSet> object named `customersDataSet` that has a table named `Customers`.</span></span>  
  
-   <span data-ttu-id="876de-114"><xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType>、<xref:System.Data?displayProperty=nameWithType> 和 <xref:System.Xml?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="876de-114">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, and <xref:System.Xml?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="876de-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="876de-115">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="876de-116">在 Windows Forms DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="876de-116">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="876de-117">操作說明：移除 Windows Forms DataGridView 控制項中自動產生的資料行</span><span class="sxs-lookup"><span data-stu-id="876de-117">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/remove-autogenerated-columns-from-a-wf-datagridview-control.md)

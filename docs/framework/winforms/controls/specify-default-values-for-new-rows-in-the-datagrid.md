---
title: "如何：指定 Windows Form DataGridView 控制項新資料列的預設值"
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
- data grids [Windows Forms], default values for new rows
- DataGridView control [Windows Forms], data entry
- rows [Windows Forms], specifying default values
- DataGridView control [Windows Forms], default values for new rows
ms.assetid: 8d127963-d9f8-4e4e-9f7f-beb66688f1f2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 26f2ab0247c9d13a90560337c103a970afc8996c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="aea6f-102">如何：指定 Windows Form DataGridView 控制項新資料列的預設值</span><span class="sxs-lookup"><span data-stu-id="aea6f-102">How to: Specify Default Values for New Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="aea6f-103">當應用程式的預設填新加入的資料列的值時，您可以進行資料的項目更方便。</span><span class="sxs-lookup"><span data-stu-id="aea6f-103">You can make data entry more convenient when the application fills in default values for newly added rows.</span></span> <span data-ttu-id="aea6f-104">與<xref:System.Windows.Forms.DataGridView>類別，您可以填入預設值與<xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>事件。</span><span class="sxs-lookup"><span data-stu-id="aea6f-104">With the <xref:System.Windows.Forms.DataGridView> class, you can fill in default values with the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span> <span data-ttu-id="aea6f-105">當使用者輸入新記錄的資料列時，會引發這個事件。</span><span class="sxs-lookup"><span data-stu-id="aea6f-105">This event is raised when the user enters the row for new records.</span></span> <span data-ttu-id="aea6f-106">當您的程式碼會處理此事件時，您可以填入所需的資料格具有您所選擇的值。</span><span class="sxs-lookup"><span data-stu-id="aea6f-106">When your code handles this event, you can populate desired cells with values of your choosing.</span></span>  
  
 <span data-ttu-id="aea6f-107">下列程式碼範例示範如何指定預設值為使用新的資料列<xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>事件。</span><span class="sxs-lookup"><span data-stu-id="aea6f-107">The following code example demonstrates how to specify default values for new rows using the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aea6f-108">範例</span><span class="sxs-lookup"><span data-stu-id="aea6f-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="aea6f-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="aea6f-109">Compiling the Code</span></span>  
 <span data-ttu-id="aea6f-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="aea6f-110">This example requires:</span></span>  
  
-   <span data-ttu-id="aea6f-111">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="aea6f-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="aea6f-112">A`NewCustomerId`函式來產生唯一`CustomerID`值。</span><span class="sxs-lookup"><span data-stu-id="aea6f-112">A `NewCustomerId` function for generating unique `CustomerID` values.</span></span>  
  
-   <span data-ttu-id="aea6f-113"><xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="aea6f-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aea6f-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="aea6f-114">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>  
 [<span data-ttu-id="aea6f-115">Windows Forms DataGridView 控制項中的資料輸入</span><span class="sxs-lookup"><span data-stu-id="aea6f-115">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="aea6f-116">使用 Windows Forms DataGridView 控制項中用於新增記錄的資料列</span><span class="sxs-lookup"><span data-stu-id="aea6f-116">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)

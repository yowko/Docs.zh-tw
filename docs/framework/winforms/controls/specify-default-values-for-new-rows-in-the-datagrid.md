---
title: HOW TO：指定 Windows Form DataGridView 控制項的新資料列預設值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], default values for new rows
- DataGridView control [Windows Forms], data entry
- rows [Windows Forms], specifying default values
- DataGridView control [Windows Forms], default values for new rows
ms.assetid: 8d127963-d9f8-4e4e-9f7f-beb66688f1f2
ms.openlocfilehash: 879c035366c4686ceff3250a63c6ae8d8d3cfec4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651953"
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="ebc11-102">HOW TO：指定 Windows Form DataGridView 控制項的新資料列預設值</span><span class="sxs-lookup"><span data-stu-id="ebc11-102">How to: Specify Default Values for New Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="ebc11-103">當應用程式的預設填新加入的資料列的值時，您可以讓資料輸入更方便。</span><span class="sxs-lookup"><span data-stu-id="ebc11-103">You can make data entry more convenient when the application fills in default values for newly added rows.</span></span> <span data-ttu-id="ebc11-104">具有<xref:System.Windows.Forms.DataGridView>類別，您可以填入預設值取代<xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>事件。</span><span class="sxs-lookup"><span data-stu-id="ebc11-104">With the <xref:System.Windows.Forms.DataGridView> class, you can fill in default values with the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span> <span data-ttu-id="ebc11-105">當使用者輸入新資料錄的資料列時，會引發這個事件。</span><span class="sxs-lookup"><span data-stu-id="ebc11-105">This event is raised when the user enters the row for new records.</span></span> <span data-ttu-id="ebc11-106">當您的程式碼會處理此事件時，您可以填入所需的資料格，以您選擇的值。</span><span class="sxs-lookup"><span data-stu-id="ebc11-106">When your code handles this event, you can populate desired cells with values of your choosing.</span></span>  
  
 <span data-ttu-id="ebc11-107">下列程式碼範例示範如何指定預設值的新資料列，使用<xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>事件。</span><span class="sxs-lookup"><span data-stu-id="ebc11-107">The following code example demonstrates how to specify default values for new rows using the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebc11-108">範例</span><span class="sxs-lookup"><span data-stu-id="ebc11-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ebc11-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ebc11-109">Compiling the Code</span></span>  
 <span data-ttu-id="ebc11-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="ebc11-110">This example requires:</span></span>  
  
- <span data-ttu-id="ebc11-111">名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="ebc11-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="ebc11-112">A`NewCustomerId`函式來產生唯一`CustomerID`值。</span><span class="sxs-lookup"><span data-stu-id="ebc11-112">A `NewCustomerId` function for generating unique `CustomerID` values.</span></span>  
  
- <span data-ttu-id="ebc11-113"><xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="ebc11-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebc11-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebc11-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [<span data-ttu-id="ebc11-115">Windows Forms DataGridView 控制項中的資料輸入</span><span class="sxs-lookup"><span data-stu-id="ebc11-115">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="ebc11-116">使用 Windows Forms DataGridView 控制項中用於新增記錄的資料列</span><span class="sxs-lookup"><span data-stu-id="ebc11-116">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)

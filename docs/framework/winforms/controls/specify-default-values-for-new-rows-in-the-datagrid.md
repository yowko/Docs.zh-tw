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
ms.openlocfilehash: 8a90cbef7032fd3753a6c9ec0b856a4e2ea1db27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009730"
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a>HOW TO：指定 Windows Form DataGridView 控制項的新資料列預設值
當應用程式的預設填新加入的資料列的值時，您可以讓資料輸入更方便。 具有<xref:System.Windows.Forms.DataGridView>類別，您可以填入預設值取代<xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>事件。 當使用者輸入新資料錄的資料列時，會引發這個事件。 當您的程式碼會處理此事件時，您可以填入所需的資料格，以您選擇的值。  
  
 下列程式碼範例示範如何指定預設值的新資料列，使用<xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>事件。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- 名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
- A`NewCustomerId`函式來產生唯一`CustomerID`值。  
  
- <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [Windows Forms DataGridView 控制項中的資料輸入](data-entry-in-the-windows-forms-datagridview-control.md)
- [使用 Windows Forms DataGridView 控制項中用於新增記錄的資料列](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)

---
title: 指定 DataGridView 控制項中新資料列的預設值
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
ms.openlocfilehash: 364f922aefc10e57f2ed7f3a0c2a5b25c922d87a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742939"
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a>如何：指定 Windows Form DataGridView 控制項新資料列的預設值
當應用程式在新加入的資料列中填入預設值時，您可以更方便地進行資料輸入。 使用 <xref:System.Windows.Forms.DataGridView> 類別，您可以使用 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> 事件填入預設值。 當使用者輸入新記錄的資料列時，就會引發這個事件。 當您的程式碼處理這個事件時，您可以使用您選擇的值填入所需的儲存格。  
  
 下列程式碼範例示範如何使用 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> 事件來指定新資料列的預設值。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- 名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
- 用來產生唯一 `CustomerID` 值的 `NewCustomerId` 函數。  
  
- <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [Windows Forms DataGridView 控制項中的資料輸入](data-entry-in-the-windows-forms-datagridview-control.md)
- [使用 Windows Forms DataGridView 控制項中用於新增記錄的資料列](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)

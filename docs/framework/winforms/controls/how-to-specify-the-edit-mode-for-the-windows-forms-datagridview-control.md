---
title: 指定 DataGridView 控制項的編輯模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
ms.openlocfilehash: c0318202a80f9a43f1b656201732ef032f430b5b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743759"
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a>如何：指定 Windows Form DataGridView 控制項的編輯模式
根據預設，使用者可以藉由在 [目前 <xref:System.Windows.Forms.DataGridView> 文字方塊] 儲存格中輸入或按 F2 來編輯其內容。 這會在符合下列所有條件時，將儲存格置於編輯模式：  
  
- 基礎資料來源支援編輯。  
  
- <xref:System.Windows.Forms.DataGridView> 控制項已啟用。  
  
- <xref:System.Windows.Forms.DataGridView.EditMode%2A> 屬性值不是 <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>。  
  
- 資料格、資料列、資料行和控制項的 `ReadOnly` 屬性全都設定為 `false`。  
  
 在編輯模式中，使用者可以變更資料格的值，然後按 ENTER 來認可變更，或按 ESC 將資料格還原成其原始值。  
  
 您可以設定 <xref:System.Windows.Forms.DataGridView> 控制項，讓資料格在資料變成目前儲存格時進入編輯模式。 在此情況下，ENTER 和 ESC 鍵的行為不會變更，但是在認可或還原值之後，資料格仍會保持編輯模式。 您也可以設定控制項，讓資料格只會在使用者輸入儲存格，或只有在使用者按下 F2 時才進入編輯模式。 最後，您可以防止資料格進入編輯模式，除非您呼叫 <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> 方法。  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a>變更 DataGridView 控制項的編輯模式  
  
- 將 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> 屬性設定為適當的 <xref:System.Windows.Forms.DataGridViewEditMode> 列舉。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- 名為 <xref:System.Windows.Forms.DataGridView> 的 `dataGridView1` 控制項。  
  
- <xref:System> 和 <xref:System.Windows.Forms> 組件的參考。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView 控制項中的資料輸入](data-entry-in-the-windows-forms-datagridview-control.md)

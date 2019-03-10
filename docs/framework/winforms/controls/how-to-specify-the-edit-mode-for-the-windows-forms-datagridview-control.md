---
title: HOW TO：Windows Form DataGridView 控制項中指定的編輯模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
ms.openlocfilehash: 00c5bb85eb1b238371e58a631d90b69a41c49140
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725297"
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a>HOW TO：Windows Form DataGridView 控制項中指定的編輯模式
根據預設，使用者可以編輯的目前內容<xref:System.Windows.Forms.DataGridView>文字 方塊中儲存格，在其中輸入，或按下 f2 鍵。 在編輯模式中，如果符合所有下列條件，這會使儲存格：  
  
-   基礎資料來源支援編輯。  
  
-   <xref:System.Windows.Forms.DataGridView>啟用控制項。  
  
-   <xref:System.Windows.Forms.DataGridView.EditMode%2A>屬性值不是<xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>。  
  
-   `ReadOnly`資料格、 資料列、 資料行和控制項的屬性都設為`false`。  
  
 在編輯模式中，使用者可以變更儲存格的值，然後按 ENTER 認可的變更或 esc 鍵還原為其原始值的資料格。  
  
 您可以設定<xref:System.Windows.Forms.DataGridView>控制項，使儲存格進入編輯模式，因為它會變成目前儲存格。 ENTER 和 ESC 鍵行為不會變更在此情況下，但是之後的值是認可或還原的資料格會保留在編輯模式。 您也可以設定控制項，以便儲存格進入編輯模式，只在使用者輸入中的資料格，或只有當使用者按下 f2 鍵時，才。 最後，您可以防止儲存格進入編輯模式，但當您呼叫<xref:System.Windows.Forms.DataGridView.BeginEdit%2A>方法。  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a>若要變更 DataGridView 控制項的編輯模式  
  
-   設定<xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>屬性為適當<xref:System.Windows.Forms.DataGridViewEditMode>列舉型別。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
-   
  <xref:System> 和 <xref:System.Windows.Forms> 組件的參考。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView 控制項中的資料輸入](data-entry-in-the-windows-forms-datagridview-control.md)

---
title: "如何：指定 Windows Form DataGridView 控制項的編輯模式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "資料格, 編輯模式"
  - "DataGridView 控制項 [Windows Form], 編輯模式"
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：指定 Windows Form DataGridView 控制項的編輯模式
根據預設，使用者可以在文字方塊儲存格中輸入或按下 F2，編輯目前 <xref:System.Windows.Forms.DataGridView> 文字方塊儲存格的內容。  如果符合下列所有條件，便會將儲存格置於編輯模式之中：  
  
-   基礎資料來源支援編輯。  
  
-   <xref:System.Windows.Forms.DataGridView> 控制項已啟用。  
  
-   <xref:System.Windows.Forms.DataGridView.EditMode%2A> 屬性值不是 <xref:System.Windows.Forms.DataGridViewEditMode>。  
  
-   儲存格、資料列、資料行和控制項的 `ReadOnly` 屬性全都設定為 `false`。  
  
 在編輯模式中，使用者可以變更儲存格值，並按下 ENTER 以認可變更，或按下 ESC 將儲存格轉換成原始值。  
  
 您可以設定 <xref:System.Windows.Forms.DataGridView> 控制項，使得儲存格在成為目前的儲存格時馬上進入編輯模式。  在這種情況下，不會變更 ENTER 和 ESC 鍵的行為，但在認可或轉換值之後，儲存格仍然會處於編輯模式。  您也可以設定控制項，讓儲存格只有當使用者在儲存格中輸入或當使用者按下 F2 時，才進入編輯模式。  最後，您還可以避免儲存格進入編輯模式，除了呼叫 <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> 方法時例外。  
  
### 若要變更 DataGridView 控制項的編輯模式  
  
-   將 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=fullName> 屬性設定為適當的 <xref:System.Windows.Forms.DataGridViewEditMode> 列舉型別 \(Enumeration\)。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
-   <xref:System> 和 <xref:System.Windows.Forms> 組件的參考。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=fullName>   
 [Windows Form DataGridView 控制項中的資料輸入](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)
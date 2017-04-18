---
title: "使用 Windows Form DataGridView 控制項中用於新增資料錄的資料列 | Microsoft Docs"
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
  - "DataGridView 控制項 [Windows Form], 加入新資料錄的資料列"
  - "DataGridView 控制項 [Windows Form], 資料輸入"
  - "資料列, 新資料錄"
ms.assetid: 6110f1ea-9794-442c-a98a-f104a1feeaf4
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 使用 Windows Form DataGridView 控制項中用於新增資料錄的資料列
當您在應用程式中使用編輯資料的 <xref:System.Windows.Forms.DataGridView> 時，通常會想提供使用者加入新資料列或資料行至資料存放區的能力。  <xref:System.Windows.Forms.DataGridView> 控制項會藉由提供新資料錄的資料列來支援這項功能，此資料列永遠顯示為最後一列。  在資料列行首中，會以星號 \(\*\) 符號做標記。  下列章節討論若您要在進行程式設計時啟用新資料錄的資料列，所應該考量的一些事項。  
  
## 顯示新資料錄的資料列  
 使用 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> 屬性來表示是否顯示新資料錄的資料列。  此屬性的預設值為 `true`。  
  
 針對資料繫結的情況，如果控制項的 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> 屬性和資料來源的 <xref:System.ComponentModel.IBindingList.AllowNew%2A?displayProperty=fullName> 屬性都為 `true`，便會顯示新資料錄的資料列。  如果其中一個為 `false`，就不會顯示資料列。  
  
## 將預設的資料填入新資料錄的資料列  
 當使用者選取新資料錄的資料列做為目前的資料列時，<xref:System.Windows.Forms.DataGridView> 控制項會引發 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> 事件。  
  
 這個事件提供對新 <xref:System.Windows.Forms.DataGridViewRow> 的存取，並且讓您將預設的資料填入新資料列。  如需詳細資訊，請參閱 [如何：指定 Windows Form DataGridView 控制項新資料列的預設值](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)  
  
## 資料列集合  
 新資料錄的資料列是包含在 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.Rows%2A> 集合中，但在行為上具有兩大方面的差異：  
  
-   新資料錄的資料列無法以程式設計方式從 <xref:System.Windows.Forms.DataGridView.Rows%2A> 集合中移除。  如果嘗試這麼做，就會擲回 <xref:System.InvalidOperationException>。  使用者也不能刪除新資料錄的資料列。  <xref:System.Windows.Forms.DataGridViewRowCollection.Clear%2A?displayProperty=fullName> 方法不會從 <xref:System.Windows.Forms.DataGridView.Rows%2A> 集合中移除這個資料列。  
  
-   在新資料錄的資料列之後不能加入任何資料列。  如果嘗試這麼做，就會引發 <xref:System.InvalidOperationException>。  因此，新資料錄的資料列永遠都會是 <xref:System.Windows.Forms.DataGridView> 控制項中的最後一列。  加入資料列的 <xref:System.Windows.Forms.DataGridViewRowCollection> 上的方法 \(<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>、<xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A> 和 <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>\) 在呈現新資料錄的資料列時，全部都會在內部呼叫插入方法。  
  
## 新資料錄的資料列的視覺自訂  
 在建立新資料錄的資料列時，會依據由 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> 屬性所指定的資料列來進行。  任何不是指定給這個資料列的儲存格樣式，都是繼承自其他屬性。  如需儲存格樣式繼承的詳細資訊，請參閱 [Windows Form DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)。  
  
 在新資料錄的資料列中，由儲存格所顯示的初始值是擷取自每一個儲存格的 <xref:System.Windows.Forms.DataGridViewCell.DefaultNewRowValue%2A> 屬性。  對於 <xref:System.Windows.Forms.DataGridViewImageCell> 型別的儲存格，這個屬性會傳回預留位置影像。  否則，這個函式會傳回 `null`。  您可以覆寫這個屬性，以傳回自訂值。  不過，當焦點輸入新資料錄的資料列時，這些初始值可用 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> 事件處理常式加以取代。  
  
 這個資料列行首的標準圖示 \(箭號或星號\) 並沒有公開 \(Expose\) 為公用圖示。  如果想要自訂圖示，就需要建立自訂的 <xref:System.Windows.Forms.DataGridViewRowHeaderCell> 類別。  
  
 標準圖示使用由資料列行首儲存格所使用的 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> 屬性。  若沒有足夠空間完整顯示標準圖示，就不會呈現標準圖示。  
  
 如果資料列行首儲存格具有字串值集，且如果沒有足夠空間供文字與圖示使用，便會先卸除圖示。  
  
## 排序  
 在未繫結模式中，即便使用者已經排序 <xref:System.Windows.Forms.DataGridView> 的內容，新資料錄仍一定會加入至 <xref:System.Windows.Forms.DataGridView> 的結尾。  為了將資料列排序至正確的位置，使用者需要再次套用排序；這種行為與 <xref:System.Windows.Forms.ListView> 控制項的行為類似。  
  
 在資料繫結與虛擬模式中，套用排序時的插入行為會根據資料模型的實作而定。  對於 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]，資料列則會馬上排序至正確的位置。  
  
## 新資料錄的資料列的其他注意事項  
 您不能將此資料列的 <xref:System.Windows.Forms.DataGridViewRow.Visible%2A> 屬性設定為 `false`。  如果嘗試這麼做，就會引發 <xref:System.InvalidOperationException>。  
  
 新資料錄的資料列一定會以未選取的狀態建立。  
  
## 虛擬模式  
 如果您實作虛擬模式，就會需要追蹤在資料模型中需要新資料錄的資料列的時機，以及復原加入資料列的時機。  這項功能的精確實作是依據資料模型的實作和交易語意 \(例如，認可範圍是否為儲存格或資料列層級\) 而定。  如需詳細資訊，請參閱 [Windows Form DataGridView 控制項中的虛擬模式](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=fullName>   
 [Windows Form DataGridView 控制項中的資料輸入](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)   
 [如何：指定 Windows Form DataGridView 控制項新資料列的預設值](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)
---
title: "如何：確保繫結至相同資料來源的多個控制項都能保持同步 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "控制項 [Windows Form], 繫結多個"
  - "控制項 [Windows Form], 與資料來源同步處理"
ms.assetid: c2f0ecc6-11e6-4c2c-a1ca-0759630c451e
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：確保繫結至相同資料來源的多個控制項都能保持同步
在 Windows Form 中使用資料繫結 \(Data Binding\) 時，經常都會將多個控制項繫結到相同的資料來源。  在某些情況下必須採取額外的步驟，以確保控制項的繫結屬性會與彼此和資料來源維持同步。  遇到下面兩種情況時，必須採取這些步驟：  
  
-   如果資料來源沒有實作 <xref:System.ComponentModel.IBindingList>，並因此產生 <xref:System.ComponentModel.ListChangedType> 型別的 <xref:System.ComponentModel.IBindingList.ListChanged> 事件。  
  
-   如果資料來源有實作 <xref:System.ComponentModel.IEditableObject>。  
  
 在第一種情況下，您可以使用 <xref:System.Windows.Forms.BindingSource> 將資料來源繫結到控制項。  在第二種情況下，則是可以使用 <xref:System.Windows.Forms.BindingSource> 並處理 <xref:System.Windows.Forms.BindingSource.BindingComplete> 事件，以及呼叫關聯之 <xref:System.Windows.Forms.BindingManagerBase> 上的 <xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A>。  
  
## 範例  
 下列程式碼範例示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件，將三個控制項 \(兩個文字方塊控制項和一個 <xref:System.Windows.Forms.DataGridView> 控制項\) 繫結到 <xref:System.Data.DataSet> 中的同一欄。  這個範例示範如何處理 <xref:System.Windows.Forms.BindingSource.BindingComplete> 事件，並確保當一個文字方塊的文字值變更時，另一個文字方塊和 <xref:System.Windows.Forms.DataGridView> 控制項將會以正確的值進行更新。  
  
 此範例使用 <xref:System.Windows.Forms.BindingSource> 來繫結資料來源和控制項。  或者，您也可以將控制項直接繫結到資料來源並擷取 <xref:System.Windows.Forms.BindingManagerBase>，以便從表單之 <xref:System.Windows.Forms.Control.BindingContext%2A> 進行繫結，然後再處理 <xref:System.Windows.Forms.BindingManagerBase> 的 <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> 事件。  如需執行這項操作的範例，請參閱關於 <xref:System.Windows.Forms.BindingManagerBase> 之 <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> 事件的說明頁。  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/VB/Form1.vb#1)]  
  
## 編譯程式碼  
  
-   這個程式碼範例需要  
  
-   <xref:System>、<xref:System.Windows.Forms> 和 <xref:System.Drawing> 組件的參考。  
  
-   已處理 <xref:System.Windows.Forms.Form.Load> 事件的表單，以及從表單的 <xref:System.Windows.Forms.Form.Load> 事件處理常式對範例中的 `InitializeControlsAndDataSource` 方法進行的呼叫。  
  
## 請參閱  
 [如何：使用 BindingSource 元件跨表單共用繫結資料](../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)   
 [Windows Form 資料繫結中的變更告知](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)   
 [與資料繫結相關的介面](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)   
 [Windows Form 資料繫結](../../../docs/framework/winforms/windows-forms-data-binding.md)
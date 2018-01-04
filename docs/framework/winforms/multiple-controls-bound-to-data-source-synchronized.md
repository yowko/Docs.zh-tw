---
title: "如何：確保繫結至相同資料來源的多個控制項都能保持同步"
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
- controls [Windows Forms], binding multiple
- controls [Windows Forms], synchronizing with data source
ms.assetid: c2f0ecc6-11e6-4c2c-a1ca-0759630c451e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 227ad36e87c3deceb7fefe3cd19013fc8e76c686
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-ensure-multiple-controls-bound-to-the-same-data-source-remain-synchronized"></a>如何：確保繫結至相同資料來源的多個控制項都能保持同步
有時候當使用 Windows Form 中的資料繫結時，多個控制項所繫結至相同的資料來源。 在某些情況下，可能必須採取額外步驟以確保控制項的繫結的內容中與其他每個及資料來源同步處理。 這些步驟是兩個情況中，必須：  
  
-   如果資料來源沒有實作<xref:System.ComponentModel.IBindingList>，並因此產生<xref:System.ComponentModel.IBindingList.ListChanged>類型的事件<xref:System.ComponentModel.ListChangedType.ItemChanged>。  
  
-   如果資料來源實作<xref:System.ComponentModel.IEditableObject>。  
  
 在前一個案例中，您可以使用<xref:System.Windows.Forms.BindingSource>繫結至控制項的資料來源。 在後者的情況下，您可以使用<xref:System.Windows.Forms.BindingSource>及處理<xref:System.Windows.Forms.BindingSource.BindingComplete>事件和呼叫<xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A>上相關聯<xref:System.Windows.Forms.BindingManagerBase>。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何繫結的三個控制項，兩個文字方塊控制項和<xref:System.Windows.Forms.DataGridView>控制項 — 中的相同資料行<xref:System.Data.DataSet>使用<xref:System.Windows.Forms.BindingSource>元件。 這個範例示範如何處理<xref:System.Windows.Forms.BindingSource.BindingComplete>事件，並確定單一文字方塊的文字值變更時，其他文字方塊和<xref:System.Windows.Forms.DataGridView>控制項以正確的值更新。  
  
 此範例會使用<xref:System.Windows.Forms.BindingSource>繫結資料來源和控制項。 或者，您可以直接繫結控制項至資料來源並擷取<xref:System.Windows.Forms.BindingManagerBase>從表單的繫結<xref:System.Windows.Forms.Control.BindingContext%2A>然後處理<xref:System.Windows.Forms.BindingManagerBase.BindingComplete>事件<xref:System.Windows.Forms.BindingManagerBase>。 如何執行此動作的範例，請參閱 [說明] 頁面，關於<xref:System.Windows.Forms.BindingManagerBase.BindingComplete>事件<xref:System.Windows.Forms.BindingManagerBase>。  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   這個程式碼範例要求  
  
-   <xref:System>、<xref:System.Windows.Forms> 和 <xref:System.Drawing> 組件的參考。  
  
-   表單具有<xref:System.Windows.Forms.Form.Load>處理事件和呼叫`InitializeControlsAndDataSource`從表單的範例方法<xref:System.Windows.Forms.Form.Load>事件處理常式。  
  
## <a name="see-also"></a>請參閱  
 [操作說明：使用 BindingSource 元件跨表單共用繫結資料](../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 [Windows Forms 資料繫結中的變更告知](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [與資料繫結相關的介面](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)  
 [Windows Forms 資料繫結](../../../docs/framework/winforms/windows-forms-data-binding.md)

---
title: "如何：將 Windows Form ComboBox 或 ListBox 控制項繫結至資料"
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
- data [Windows Forms], binding to controls
- list boxes [Windows Forms], data binding
- ComboBox control [Windows Forms], data binding
- data binding [Windows Forms], combo boxes
- ListBox control [Windows Forms], data binding
- combo boxes [Windows Forms], data binding
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- data-bound controls [Windows Forms], Windows Forms
ms.assetid: dfd7f081-8bea-4a41-86a3-86a1934828ef
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6193e4cc86a470f046c220dc21150e0fc0bf792a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>如何：將 Windows Form ComboBox 或 ListBox 控制項繫結至資料
您可以繫結<xref:System.Windows.Forms.ComboBox>和<xref:System.Windows.Forms.ListBox>執行工作，例如瀏覽資料在資料庫中的資料，請輸入新的資料，或編輯現有的資料。  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>將 ComboBox 或 ListBox 控制項繫結  
  
1.  設定`DataSource`資料來源物件的屬性。 可能的資料來源包括<xref:System.Windows.Forms.BindingSource>管理員、 陣列或任何類別所實作的繫結至資料、 資料表、 資料檢視、 資料集，資料檢視<xref:System.Collections.IList>介面。 如需詳細資訊，請參閱[支援的 Windows Form 資料來源](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)。  
  
2.  如果您要繫結至資料表，將`DisplayMember`屬性設為資料來源中的資料行的名稱。  
  
     \-或-  
  
     如果您要繫結<xref:System.Collections.IList>，設為清單中類型的公用屬性的 顯示成員。  
  
    ```vb  
    Private Sub BindComboBox()  
      ComboBox1.DataSource = DataSet1.Tables("Suppliers")  
      ComboBox1.DisplayMember = "ProductName"  
    End Sub  
    ```  
  
    ```csharp  
    private void BindComboBox()  
    {  
      comboBox1.DataSource = dataSet1.Tables["Suppliers"];  
      comboBox1.DisplayMember = "ProductName";  
    }  
    ```  
  
    > [!NOTE]
    >  如果您繫結至資料來源不會實作<xref:System.ComponentModel.IBindingList>介面，例如<xref:System.Collections.ArrayList>，更新資料來源時，將不會更新繫結的控制項的資料。 例如，如果您有下拉式方塊繫結至<xref:System.Collections.ArrayList>和資料加入至<xref:System.Collections.ArrayList>，這些新的項目不會出現在下拉式方塊。 不過，您可以強制下拉式方塊，以藉由呼叫更新<xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A>和<xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A>方法的執行個體上<xref:System.Windows.Forms.BindingContext>控制項所繫結類別。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 [Windows Forms 資料繫結](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [資料繫結和 Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [用來列出選項的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)

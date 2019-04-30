---
title: HOW TO：將 Windows Forms ComboBox 或 ListBox 控制項繫結至資料
ms.date: 03/30/2017
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
ms.openlocfilehash: b869898a20008343b6c6cbe4bc7e399fc86fb232
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054012"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>HOW TO：將 Windows Forms ComboBox 或 ListBox 控制項繫結至資料
您可以繫結<xref:System.Windows.Forms.ComboBox>和<xref:System.Windows.Forms.ListBox>資料，以執行工作，例如瀏覽資料庫中的資料，以在輸入新的資料，或編輯現有的資料。  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>將 ComboBox 或 ListBox 控制項繫結  
  
1. 設定`DataSource`資料來源物件的屬性。 可能的資料來源包括<xref:System.Windows.Forms.BindingSource>管理員、 陣列或任何實作類別的繫結至資料、 資料表、 資料檢視、 資料集，資料檢視<xref:System.Collections.IList>介面。 如需詳細資訊，請參閱 <<c0> [ 支援的 Windows Form 資料來源](../data-sources-supported-by-windows-forms.md)。  
  
2. 如果您要繫結至資料表，將設定`DisplayMember`屬性設為資料來源中的資料行的名稱。  
  
     \-或-  
  
     如果您要繫結<xref:System.Collections.IList>，顯示成員設定為清單中類型的公用屬性。  
  
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
    >  如果您繫結至資料來源未實作<xref:System.ComponentModel.IBindingList>介面，例如<xref:System.Collections.ArrayList>，更新資料來源時，將不會更新繫結的控制項的資料。 例如，如果您有下拉式方塊繫結至<xref:System.Collections.ArrayList>而且資料會加入至<xref:System.Collections.ArrayList>，這些新的項目不會出現在下拉式方塊。 不過，您可以在其中強制下拉式方塊，藉由呼叫更新<xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A>並<xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A>執行個體上的方法<xref:System.Windows.Forms.BindingContext>控制項所繫結類別。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Windows Forms 資料繫結](../windows-forms-data-binding.md)
- [資料繫結和 Windows Forms](../data-binding-and-windows-forms.md)
- [用來列出選項的 Windows Forms 控制項](windows-forms-controls-used-to-list-options.md)

---
title: 如何：建立 MDI 子表單
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: d4351e88de896f366ae2c4050f0e1c32aa0188a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527495"
---
# <a name="how-to-create-mdi-child-forms"></a>如何：建立 MDI 子表單
MDI 子表單是不可或缺的要素的[多重文件介面 (MDI) 應用程式](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)，如下列形式會與使用者互動的中心。  
  
 在下列程序中，您將建立顯示 <xref:System.Windows.Forms.RichTextBox> 控制項的 MDI 子表單，這和大多數文書處理應用程式類似。 以其他控制項 (例如 <xref:System.Windows.Forms.DataGridView> 控制項) 或混合控制項來取代 <xref:System.Windows.Forms> 控制項，可讓您建立各種可能的 MDI 子視窗 (甚至是 MDI 應用程式)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-create-mdi-child-forms"></a>建立 MDI 子表單  
  
1.  建立新的 Windows Form 專案。 在 **[屬性] 視窗**表單中，設定其<xref:System.Windows.Forms.Form.IsMdiContainer%2A>屬性`true`，並將其`WindowsState`屬性`Maximized`。  
  
     如此即可將表單指定為子視窗的 MDI 容器。  
  
2.  將 <xref:System.Windows.Forms.MenuStrip> 控制項從 [`Toolbox`] 拖曳至表單。 設定其`Text`屬性**檔案**。  
  
3.  按一下省略符號 （...） 下, 一步**項目**屬性，然後按一下**新增**加入兩個子工具區域功能表項目。 設定`Text`屬性，這些項目**新增**和**視窗**。  
  
4.  在**方案總管 中**，以滑鼠右鍵按一下專案，指向**新增**，然後選取**加入新項目**。  
  
5.  在**加入新項目**對話方塊中，選取**Windows Form** （在 Visual Basic 或 Visual C# 中） 或**Windows Forms 應用程式 (.NET)** (在[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 從**範本**窗格。 在**名稱**方塊中，將表單命名為**Form2**。 按一下**開啟**按鈕，將表單加入至專案。  
  
    > [!NOTE]
    >  您在這個步驟中所建立的 MDI 子表單是標準的 Windows Form。 因此，它具有 <xref:System.Windows.Forms.Form.Opacity%2A> 屬性，可讓您控制表單的透明度。 然而，<xref:System.Windows.Forms.Form.Opacity%2A> 屬性是專為最上層視窗而設計的。 請勿搭配 MDI 子表單使用這個屬性，這樣做可能會發生繪製問題。  
  
     這個表單將是您的 MDI 子表單範本。  
  
     **Windows Form 設計工具**隨即開啟，顯示**Form2**。  
  
6.  從**工具箱**，拖曳**RichTextBox**控制項加入表單。  
  
7.  在**屬性**視窗中，將`Anchor`屬性**左上**和`Dock`屬性**填滿**。  
  
     如此一來，<xref:System.Windows.Forms.RichTextBox> 控制項就會完全填滿 MDI 子表單區域，即使表單大小重新調整過亦可。  
  
8.  按兩下 **新增**功能表項目，以建立<xref:System.Windows.Forms.Control.Click>為它的事件處理常式。  
  
9. 插入程式碼，如下所示來建立新的 MDI 子表單，當使用者按一下**新增**功能表項目。  
  
    > [!NOTE]
    >  在下列範例中，事件處理常式會處理 `MenuItem2` 的 <xref:System.Windows.Forms.Control.Click> 事件。 請注意，根據您的應用程式架構的細節您**新增**功能表項目可能無法`MenuItem2`。  
  
    ```vb  
    Protected Sub MDIChildNew_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MenuItem2.Click  
       Dim NewMDIChild As New Form2()  
       'Set the Parent Form of the Child window.  
       NewMDIChild.MdiParent = Me  
       'Display the new form.  
       NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    protected void MDIChildNew_Click(object sender, System.EventArgs e){  
       Form2 newMDIChild = new Form2();  
       // Set the Parent Form of the Child window.  
       newMDIChild.MdiParent = this;  
       // Display the new form.  
       newMDIChild.Show();  
    }  
    ```  
  
    ```cpp  
    private:  
       void menuItem2_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          Form2^ newMDIChild = gcnew Form2();  
          // Set the Parent Form of the Child window.  
          newMDIChild->MdiParent = this;  
          // Display the new form.  
          newMDIChild->Show();  
       }  
    ```  
  
     在 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)] 中，將下列 `#include` 指示詞加入 Form1.h 上方：  
  
    ```cpp  
    #include "Form2.h"  
    ```  
  
10. 在頂端的下拉式清單中**屬性**視窗中，選取對應至功能表列**檔案**功能表列和組<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>屬性視窗<xref:System.Windows.Forms.ToolStripMenuItem>。  
  
     這會讓**視窗**功能表維護一份開啟的 MDI 子視窗，在使用中的子視窗旁的核取記號。  
  
11. 按 F5 執行應用程式。 藉由選取**新增**從**檔案**功能表上，您可以建立新的 MDI 子表單，這會保留在追蹤的**視窗**功能表項目。  
  
    > [!NOTE]
    >  在 <xref:System.Windows.Forms.MainMenu> 元件 (這個元件通常具有功能表項目的功能表結構) 的 MDI 父表單中，開啟同樣具有 <xref:System.Windows.Forms.MainMenu> 元件 (這個元件通常具有功能表項目的功能表結構) 的 MDI 子表單時，如果您已設定 <xref:System.Windows.Forms.MenuItem.MergeType%2A> 屬性 (並選擇性地設定 <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> 屬性)，則功能表項目會自動合併。 將上述兩個 <xref:System.Windows.Forms.MainMenu> 的 <xref:System.Windows.Forms.MenuItem.MergeType%2A> 屬性和子表單的所有功能表項目設定為 <xref:System.Windows.Forms.MenuMerge.MergeItems>。 接著再設定 <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> 屬性，如此一來，來自兩個功能表的功能表項目即可依指定順序出現。 再者，請記住，在關閉 MDI 父表單時，每個 MDI 子表單都會在 MDI 父表單的 <xref:System.Windows.Forms.Form.Closing> 事件引發前，先引發 <xref:System.Windows.Forms.Form.Closing> 事件。 只取消 MDI 子表單的 <xref:System.Windows.Forms.Form.Closing> 事件並無法避免引發 MDI 父表單的 <xref:System.Windows.Forms.Form.Closing> 事件；不過，MDI 父表單之 <xref:System.Windows.Forms.Form.Closing> 事件的 <xref:System.ComponentModel.CancelEventArgs> 引數現在會設定為 `true`。 您可以將 <xref:System.ComponentModel.CancelEventArgs> 引數設定為 `false`，以強制關閉 MDI 父表單和所有 MDI 子表單。  
  
## <a name="see-also"></a>另請參閱  
 [多重文件介面 (MDI) 應用程式](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [操作說明：建立 MDI 父表單](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [操作說明：決定作用中的 MDI 子系](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [操作說明：傳送資料至作用中的 MDI 子系](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [操作說明：安排 MDI 子表單](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)

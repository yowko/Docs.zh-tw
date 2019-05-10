---
title: HOW TO：建立 MDI 子表單
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: fbc92c03da69dd452f35e5b4e00cd4a9ca17e252
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211188"
---
# <a name="how-to-create-mdi-child-forms"></a>HOW TO：建立 MDI 子表單

MDI 子表單是不可或缺的元素[多重文件介面 (MDI) 應用程式](multiple-document-interface-mdi-applications.md)，如下列形式會使用者互動的中心。

在下列程序中，您將使用 Visual Studio 建立 MDI 子表單顯示<xref:System.Windows.Forms.RichTextBox>控制項，這和大多數文書處理應用程式類似。 以其他控制項 (例如 <xref:System.Windows.Forms.DataGridView> 控制項) 或混合控制項來取代 <xref:System.Windows.Forms> 控制項，可讓您建立各種可能的 MDI 子視窗 (甚至是 MDI 應用程式)。

## <a name="create-mdi-child-forms"></a>建立 MDI 子表單

1. 建立新的 Windows Form 專案。 在**屬性 Windows**表單中，設定其<xref:System.Windows.Forms.Form.IsMdiContainer%2A>屬性設`true`，並將其`WindowsState`屬性設`Maximized`。

   如此即可將表單指定為子視窗的 MDI 容器。

2. 將 <xref:System.Windows.Forms.MenuStrip> 控制項從 [`Toolbox`] 拖曳至表單。 設定其`Text`屬性，以**檔案**。

3. 按一下旁邊的省略符號 （...）**項目**屬性，然後按一下**新增**加入兩個子工具區域功能表項目。 設定`Text`屬性，這些項目的**新增**並**視窗**。

4. 在 [**方案總管] 中**，以滑鼠右鍵按一下專案，指向**新增**，然後選取**加入新項目**。

5. 在 **加入新項目**對話方塊方塊中，選取**Windows 表單**（在 Visual Basic 或 Visual C# 中） 或**Windows Forms 應用程式 (.NET)** (在[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 從**範本**窗格。 在 **名稱**方塊中，將表單命名**Form2**。 按一下 **開啟**按鈕以新增至專案的表單。

    > [!NOTE]
    > 您在這個步驟中所建立的 MDI 子表單是標準的 Windows Form。 因此，它具有 <xref:System.Windows.Forms.Form.Opacity%2A> 屬性，可讓您控制表單的透明度。 然而，<xref:System.Windows.Forms.Form.Opacity%2A> 屬性是專為最上層視窗而設計的。 請勿搭配 MDI 子表單使用這個屬性，這樣做可能會發生繪製問題。

     這個表單將是您的 MDI 子表單範本。

     **Windows Form 設計工具**隨即開啟，顯示**Form2**。

6. 從**工具箱**，拖曳**RichTextBox**控制項加入表單。

7. 在**屬性**視窗中，將`Anchor`屬性設**左上**而`Dock`屬性設**填滿**。

   如此一來，<xref:System.Windows.Forms.RichTextBox> 控制項就會完全填滿 MDI 子表單區域，即使表單大小重新調整過亦可。

8. 按兩下**的新** 功能表項目，以建立<xref:System.Windows.Forms.Control.Click>為它的事件處理常式。

9. 插入程式碼如下所示來建立新的 MDI 子表單，當使用者按一下**新增**功能表項目。

   > [!NOTE]
   > 在下列範例中，事件處理常式會處理 `MenuItem2` 的 <xref:System.Windows.Forms.Control.Click> 事件。 請注意，根據您的應用程式架構的細節您**新增**功能表項目可能無法`MenuItem2`。

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

   在C++，新增下列`#include`指示詞 form1.h 上方：

   ```cpp
   #include "Form2.h"
   ```

10. 在頂端的下拉式清單中**屬性** 視窗中，選取對應至功能表列**檔案**功能表列並將<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>屬性 視窗<xref:System.Windows.Forms.ToolStripMenuItem>。

    這可讓**視窗**功能表維護一份開啟的 MDI 子視窗，在作用中的子視窗旁邊的核取記號。

11. 按 **F5** 執行應用程式。 藉由選取**的新**從**檔案**功能表中，您可以建立新的 MDI 子表單，其中會保留在追蹤的**視窗**功能表項目。

    > [!NOTE]
    > 在 <xref:System.Windows.Forms.MainMenu> 元件 (這個元件通常具有功能表項目的功能表結構) 的 MDI 父表單中，開啟同樣具有 <xref:System.Windows.Forms.MainMenu> 元件 (這個元件通常具有功能表項目的功能表結構) 的 MDI 子表單時，如果您已設定 <xref:System.Windows.Forms.MenuItem.MergeType%2A> 屬性 (並選擇性地設定 <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> 屬性)，則功能表項目會自動合併。 將上述兩個 <xref:System.Windows.Forms.MainMenu> 的 <xref:System.Windows.Forms.MenuItem.MergeType%2A> 屬性和子表單的所有功能表項目設定為 <xref:System.Windows.Forms.MenuMerge.MergeItems>。 接著再設定 <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> 屬性，如此一來，來自兩個功能表的功能表項目即可依指定順序出現。 再者，請記住，在關閉 MDI 父表單時，每個 MDI 子表單都會在 MDI 父表單的 <xref:System.Windows.Forms.Form.Closing> 事件引發前，先引發 <xref:System.Windows.Forms.Form.Closing> 事件。 只取消 MDI 子表單的 <xref:System.Windows.Forms.Form.Closing> 事件並無法避免引發 MDI 父表單的 <xref:System.Windows.Forms.Form.Closing> 事件；不過，MDI 父表單之 <xref:System.Windows.Forms.Form.Closing> 事件的 <xref:System.ComponentModel.CancelEventArgs> 引數現在會設定為 `true`。 您可以將 <xref:System.ComponentModel.CancelEventArgs> 引數設定為 `false`，以強制關閉 MDI 父表單和所有 MDI 子表單。

## <a name="see-also"></a>另請參閱

- [多重文件介面 (MDI) 應用程式](multiple-document-interface-mdi-applications.md)
- [如何：建立 MDI 父表單](how-to-create-mdi-parent-forms.md)
- [如何：決定作用中的 MDI 子系](how-to-determine-the-active-mdi-child.md)
- [如何：將資料傳送至作用中的 MDI 子系](how-to-send-data-to-the-active-mdi-child.md)
- [如何：排列 MDI 子表單](how-to-arrange-mdi-child-forms.md)

---
title: 作法：建立 MDI 子表單
ms.date: 03/30/2017
dev_langs:
- CSharp
- CPP
- VB
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: f5e8682caf658d159f044528f040b99676355448
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040117"
---
# <a name="how-to-create-mdi-child-forms"></a>HOW TO：建立 MDI 子表單

MDI 子表單是[多重文件介面 (MDI) 應用程式](multiple-document-interface-mdi-applications.md)的重要元素, 因為這些形式是使用者互動的中心。

在下列程式中, 您將使用 Visual Studio 來建立顯示<xref:System.Windows.Forms.RichTextBox>控制項的 MDI 子表單, 類似于大部分的文字處理應用程式。 藉由將<xref:System.Windows.Forms>控制項替換為其他控制項 (例如<xref:System.Windows.Forms.DataGridView>控制項) 或控制項的混合, 您可以建立具有各種可能性的 MDI 子視窗 (以及擴充功能、mdi 應用程式)。

## <a name="create-mdi-child-forms"></a>建立 MDI 子表單

1. 在 Visual Studio 中建立新的 Windows Forms 應用程式專案。 在表單的 [**屬性**] 視窗中, <xref:System.Windows.Forms.Form.IsMdiContainer%2A>將其`true`屬性設`WindowsState`為, `Maximized`並將其屬性設定為。

   如此即可將表單指定為子視窗的 MDI 容器。

2. 將 <xref:System.Windows.Forms.MenuStrip> 控制項從 [`Toolbox`] 拖曳至表單。 將其`Text`屬性設為**File**。

3. 按一下 [**專案**] 屬性旁的省略號 (...), 然後按一下 [**新增**] 以加入兩個子工具區域的功能表項目。 將這些`Text`專案的屬性設定為 [**新增**] 和 [**視窗]** 。

4. 在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。

5. 在 [**加入新專案**] 對話方塊中, 從 [**範本**] 窗格選取 [ **Windows Form** ] (在 Visual Basic 或 Visual C#中) 或 [ **Windows Forms 應用程式 (.net)** ] (在 visual C++中)。 在 [**名稱**] 方塊中, 將表單命名為**Form2**。 選取 [**開啟**], 將表單新增至專案。

    > [!NOTE]
    > 您在這個步驟中所建立的 MDI 子表單是標準的 Windows Form。 因此，它具有 <xref:System.Windows.Forms.Form.Opacity%2A> 屬性，可讓您控制表單的透明度。 然而，<xref:System.Windows.Forms.Form.Opacity%2A> 屬性是專為最上層視窗而設計的。 請勿搭配 MDI 子表單使用這個屬性，這樣做可能會發生繪製問題。

     這個表單將是您的 MDI 子表單範本。

     **Windows Form 設計工具**隨即開啟, 並顯示**Form2**。

6. 從 [**工具箱**] 將 [ **RichTextBox** ] 控制項拖曳至表單。

7. 在 [**屬性**] 視窗中, `Anchor`將屬性設定為**Top、Left** , 以及要`Dock` **填入**的屬性。

   如此一來，<xref:System.Windows.Forms.RichTextBox> 控制項就會完全填滿 MDI 子表單區域，即使表單大小重新調整過亦可。

8. 按兩下 [**新增**] 功能表項目, 為其<xref:System.Windows.Forms.Control.Click>建立事件處理常式。

9. 插入與下列類似的程式碼, 以便在使用者按一下 [**新增**] 功能表項目時建立新的 MDI 子表單。

   > [!NOTE]
   > 在下列範例中，事件處理常式會處理 `MenuItem2` 的 <xref:System.Windows.Forms.Control.Click> 事件。 請注意, 視應用程式架構的細節而定, 您的**新**功能表項目可能不是`MenuItem2`。

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

   在C++中, 于 Form1 `#include`的頂端新增下列指示詞:

   ```cpp
   #include "Form2.h"
   ```

10. 在 [**屬性**] 視窗頂端的下拉式清單中, 選取對應至 [檔案] 功能表區域的功能表區域 , <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>並將屬性設定為視窗<xref:System.Windows.Forms.ToolStripMenuItem>。

    這可讓 [**視窗]** 功能表使用作用中子視窗旁的核取記號, 維護開啟的 MDI 子視窗清單。

11. 按 **F5** 執行應用程式。 藉由從 [檔案 ] 功能表選取 [**新增**], 您可以建立新的 MDI 子表單, 其會在 [**視窗]** 功能表項目中保持追蹤。

    > [!NOTE]
    > 在 <xref:System.Windows.Forms.MainMenu> 元件 (這個元件通常具有功能表項目的功能表結構) 的 MDI 父表單中，開啟同樣具有 <xref:System.Windows.Forms.MainMenu> 元件 (這個元件通常具有功能表項目的功能表結構) 的 MDI 子表單時，如果您已設定 <xref:System.Windows.Forms.MenuItem.MergeType%2A> 屬性 (並選擇性地設定 <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> 屬性)，則功能表項目會自動合併。 將上述兩個 <xref:System.Windows.Forms.MainMenu> 的 <xref:System.Windows.Forms.MenuItem.MergeType%2A> 屬性和子表單的所有功能表項目設定為 <xref:System.Windows.Forms.MenuMerge.MergeItems>。 接著再設定 <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> 屬性，如此一來，來自兩個功能表的功能表項目即可依指定順序出現。 再者，請記住，在關閉 MDI 父表單時，每個 MDI 子表單都會在 MDI 父表單的 <xref:System.Windows.Forms.Form.Closing> 事件引發前，先引發 <xref:System.Windows.Forms.Form.Closing> 事件。 只取消 MDI 子表單的 <xref:System.Windows.Forms.Form.Closing> 事件並無法避免引發 MDI 父表單的 <xref:System.Windows.Forms.Form.Closing> 事件；不過，MDI 父表單之 <xref:System.Windows.Forms.Form.Closing> 事件的 <xref:System.ComponentModel.CancelEventArgs> 引數現在會設定為 `true`。 您可以將 <xref:System.ComponentModel.CancelEventArgs> 引數設定為 `false`，以強制關閉 MDI 父表單和所有 MDI 子表單。

## <a name="see-also"></a>另請參閱

- [多重文件介面 (MDI) 應用程式](multiple-document-interface-mdi-applications.md)
- [如何：建立 MDI 父表單](how-to-create-mdi-parent-forms.md)
- [如何：決定作用中的 MDI 子系](how-to-determine-the-active-mdi-child.md)
- [如何：將資料傳送至作用中的 MDI 子系](how-to-send-data-to-the-active-mdi-child.md)
- [如何：排列 MDI 子表單](how-to-arrange-mdi-child-forms.md)

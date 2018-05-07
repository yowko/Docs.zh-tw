---
title: 逐步解說：使用 MaskedTextBox 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- input [Windows Forms], controlling to ensure validity
- MaskedTextBox control [Windows Forms], walkthroughs
- MaskedTextBox control [Windows Forms], validation
- user input [Windows Forms], controlling
- text [Windows Forms], controls for input
ms.assetid: df60565e-5447-4110-92a6-be1f6ff5faa3
ms.openlocfilehash: bcca6c5f5481d351a39a4e71532cc0f006075128
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a>逐步解說：使用 MaskedTextBox 控制項
這個逐步解說中所述的工作包括：  
  
-   初始化<xref:System.Windows.Forms.MaskedTextBox>控制項  
  
-   使用<xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected>遮罩不符合一個字元時，通知使用者的事件處理常式  
  
-   指派的型別<xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A>屬性，並使用<xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted>來提醒使用者當他們嘗試認可的值不是有效類型的事件處理常式  
  
## <a name="creating-the-project-and-adding-a-control"></a>建立專案並加入控制項  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a>若要將 MaskedTextBox 控制項加入至表單  
  
1.  開啟您想要放置的表單<xref:System.Windows.Forms.MaskedTextBox>控制項。  
  
2.  拖曳<xref:System.Windows.Forms.MaskedTextBox>控制項從**工具箱**加入至表單。  
  
3.  以滑鼠右鍵按一下控制項，然後選擇 **屬性**。 在**屬性**視窗中，選取**遮罩**屬性，然後按一下 **...** （省略符號） 按鈕旁的屬性名稱。  
  
4.  在**輸入遮罩**對話方塊中，選取**簡短日期**遮罩，並按一下**確定**。  
  
5.  在**屬性**視窗中，將<xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A>屬性`true`。 這個屬性會導致發出短的嗶聲音每次使用者嘗試輸入違反遮罩定義的字元。  
  
 如需摘要的遮罩屬性支援的字元，請參閱的 < 備註 > 一節<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>屬性。  
  
## <a name="alert-the-user-to-input-errors"></a>警示使用者輸入錯誤  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a>新增拒絕的遮罩輸入氣球提示  
  
1.  返回**工具箱**並加入<xref:System.Windows.Forms.ToolTip>加入至表單。  
  
2.  建立事件處理常式<xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected>所引發的事件<xref:System.Windows.Forms.ToolTip>發生輸入的錯誤。 五秒，或直到使用者按一下它，仍會顯示汽球提示。  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)   
    {  
        ... // Other initialization code  
        maskedTextBox1.Mask = "00/00/0000";  
        maskedTextBox1.MaskInputRejected += new MaskInputRejectedEventHandler(maskedTextBox1_MaskInputRejected)  
    }  
  
    void maskedTextBox1_MaskInputRejected(object sender, MaskInputRejectedEventArgs e)  
    {  
        toolTip1.ToolTipTitle = "Invalid Input";  
        toolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", maskedTextBox1, maskedTextBox1.Location, 5000);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load  
        Me.ToolTip1.IsBalloon = True  
        Me.MaskedTextBox1.Mask = "00/00/0000"  
    End Sub  
  
    Private Sub MaskedTextBox1_MaskInputRejected(sender as Object, e as MaskInputRejectedEventArgs) Handles MaskedTextBox1.MaskInputRejected  
        ToolTip1.ToolTipTitle = "Invalid Input"  
        ToolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", MaskedTextBox1, 5000)  
    End Sub  
    ```  
  
## <a name="alert-the-user-to-a-type-that-is-not-valid"></a>警示使用者不是有效的類型  
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a>無效的資料類型建立汽球提示  
  
1.  在您的表單<xref:System.Windows.Forms.Form.Load>事件處理常式，指派<xref:System.Type>物件，代表<xref:System.DateTime>類型<xref:System.Windows.Forms.MaskedTextBox>控制項的<xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A>屬性：  
  
    ```csharp  
    private void Form1_Load(Object sender, EventArgs e)  
    {  
        // Other code  
        maskedTextBox1.ValidatingType = typeof(System.DateTime);  
        maskedTextBox1.TypeValidationCompleted += new TypeValidationEventHandler(maskedTextBox1_TypeValidationCompleted);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(sender as Object, e as EventArgs)  
        // Other code  
        MaskedTextBox1.ValidatingType = GetType(System.DateTime)  
    End Sub  
    ```  
  
2.  新增 <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> 事件的事件處理常式：  
  
    ```csharp  
    public void maskedTextBox1_TypeValidationCompleted(object sender, TypeValidationEventArgs e)  
    {  
        if (!e.IsValidInput)  
        {  
           toolTip1.ToolTipTitle = "Invalid Date Value";  
           toolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000);  
           e.Cancel = true;  
        }  
    }  
    ```  
  
    ```vb  
    Public Sub MaskedTextBox1_TypeValidationCompleted(sender as Object, e as TypeValidationEventArgs)  
        If Not e.IsValidInput Then  
           ToolTip1.ToolTipTitle = "Invalid Date Value"  
           ToolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000)  
           e.Cancel = True  
        End If  
    End Sub  
    ```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.MaskedTextBox>  
 [MaskedTextBox 控制項](../../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md)

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
ms.openlocfilehash: db32b3ec88a07747ea3e286af9f04edce3f1ba3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182065"
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a>逐步解說：使用 MaskedTextBox 控制項
這個逐步解說中所述的工作包括：  
  
- 初始化控制項<xref:System.Windows.Forms.MaskedTextBox>  
  
- 當字元<xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected>不符合遮罩時，使用事件處理常式提醒使用者  
  
- 將類型分配給<xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A>屬性，<xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted>並使用事件處理常式在使用者嘗試提交的值對類型無效時提醒使用者  
  
## <a name="creating-the-project-and-adding-a-control"></a>創建專案和添加控制項  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a>向表單添加蒙版文字方塊控制項  
  
1. 打開要在其上放置控制項的<xref:System.Windows.Forms.MaskedTextBox>表單。  
  
2. 將<xref:System.Windows.Forms.MaskedTextBox>控制項從**工具箱**拖動到表單。  
  
3. 按右鍵控制項並選擇 **"屬性**"。 在 **"屬性"** 視窗中，選擇 **"蒙版"** 屬性，然後按一下屬性名稱旁邊的 **..."（** 省略號）按鈕。  
  
4. 在 **"輸入遮罩"** 對話方塊中，選擇 **"短日期**"蒙版，然後按一下 **"確定**"。  
  
5. 在 **"屬性"** 視窗中將<xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A>屬性設置為`true`。 每次使用者嘗試輸入違反遮罩定義的字元時，此屬性都會發出短促的蜂鳴音。  
  
 有關蒙版屬性支援的字元的摘要，請參閱<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>該屬性的備註部分。  
  
## <a name="alert-the-user-to-input-errors"></a>提醒使用者輸入錯誤  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a>為被拒絕的蒙版輸入添加氣球提示  
  
1. 返回到**工具箱**並將 添加到<xref:System.Windows.Forms.ToolTip>表單中。  
  
2. 為<xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected>發生輸入錯誤時引發 的事件<xref:System.Windows.Forms.ToolTip>創建事件處理常式。 氣球提示保持可見五秒，或直到使用者按一下它。  
  
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
  
## <a name="alert-the-user-to-a-type-that-is-not-valid"></a>提醒使用者輸入無效類型  
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a>為無效資料類型添加氣球提示  
  
1. 在<xref:System.Windows.Forms.Form.Load>表單的事件處理常式中，將表示<xref:System.Type><xref:System.DateTime>該類型的物件分配給<xref:System.Windows.Forms.MaskedTextBox>控制項的屬性： <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A>  
  
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
  
2. 新增 <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> 事件的事件處理常式：  
  
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

- <xref:System.Windows.Forms.MaskedTextBox>
- [MaskedTextBox 控制項](maskedtextbox-control-windows-forms.md)

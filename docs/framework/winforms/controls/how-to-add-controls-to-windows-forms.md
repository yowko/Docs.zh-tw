---
title: "如何：將控制項加入至 Windows Form | Microsoft Docs"
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
  - "控制項 [Windows Form], 加入"
  - "Windows Form 控制項, 加入至表單"
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：將控制項加入至 Windows Form
大部分表單都設計成將控制項加入表單的表面，以便定義使用者介面 \(UI\)。  「*控制項*」是表單上的元件，用來顯示資訊或接受使用者輸入。  如需控制項的詳細資訊，請參閱 [Windows Form 控制項](../../../../docs/framework/winforms/controls/index.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要在表單上繪製控制項  
  
1.  開啟表單。  如需詳細資訊，請參閱 [How to: Display Windows Forms in the Designer](http://msdn.microsoft.com/zh-tw/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5)。  
  
2.  在 \[**工具箱**\] 中，按一下要加入至表單的控制項。  
  
3.  在表單上，在您希望成為控制項左上角的位置按一下，然後拖曳到希望成為控制項右下角的位置。  
  
     控制項依指定的位置和大小加入至表單。  
  
    > [!NOTE]
    >  每個控制項皆已定義預設大小。  您可以將控制項從 \[**工具箱**\] 拖曳到表單中，以便將預設大小的控制項加入表單。  
  
### 若要將控制項拖曳到表單中  
  
1.  開啟表單。  如需詳細資訊，請參閱 [How to: Display Windows Forms in the Designer](http://msdn.microsoft.com/zh-tw/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5)。  
  
2.  在 \[**工具箱**\] 中，按一下要加入的控制項並拖曳到表單。  
  
     控制項在指定的位置，以其預設大小加入至表單。  
  
    > [!NOTE]
    >  您可以按兩下 \[**工具箱**\] 中的控制項，以便將預設大小的控制項加入至表單的左上角。  
  
     您也可以在執行階段時動態將控制項加入表單。  在下列程式碼範例中，當按一下 <xref:System.Windows.Forms.Button> 控制項時，會將 <xref:System.Windows.Forms.TextBox> 控制項加入表單。  
  
    > [!NOTE]
    >  執行下列程序前必須已具有表單，而且表單中已放置名為 `Button1` 的 **Button** 控制項。  
  
### 若要以程式設計方式將控制項加入表單中  
  
1.  在表單的類別中，於處理按鈕之 `Click` 事件的方法中，插入類似以下程式碼，以便將參考加入控制項變數、設定控制項的 `Location` 並且加入控制項。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim MyText As New TextBox()  
       MyText.Location = New Point(25, 25)  
       Me.Controls.Add(MyText)  
    End Sub  
  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
       TextBox myText = new TextBox();  
       myText.Location = new Point(25,25);  
       this.Controls.Add (myText);  
    }  
  
    ```  
  
    ```cpp  
    private:  
      System::Void button1_Click(System::Object ^  sender,  
        System::EventArgs ^  e)  
      {  
        TextBox ^ myText = gcnew TextBox();  
        myText->Location = Point(25,25);  
        this->Controls->Add(myText);  
      }  
    ```  
  
    > [!NOTE]
    >  也可以加入程式碼來初始化控制項的其他屬性。  
  
    > [!IMPORTANT]
    >  參考惡意的 `UserControl`，可能會讓本機電腦透過網路暴露在安全性風險下。  這只會在使用者惡意建立破壞性的自訂控制項，且稍後您不小心將它加入專案的情況下，才會是要考慮的問題。  
  
## 請參閱  
 [Windows Form 控制項](../../../../docs/framework/winforms/controls/index.md)   
 [排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [如何：重新調整 Windows Form 上控制項的大小](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md)   
 [如何：設定由 Windows Form 控制項所顯示的文字](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)   
 [在 Windows Form 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
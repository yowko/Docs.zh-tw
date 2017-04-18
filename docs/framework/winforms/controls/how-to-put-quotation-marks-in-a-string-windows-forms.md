---
title: "如何：將引號放入字串中 (Windows Form) | Microsoft Docs"
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
  - "引號"
  - "引號, 在文字方塊中加入字串"
  - "TextBox 控制項 [Windows Form], 顯示引號"
ms.assetid: 68bdc3f3-4177-4eab-99cd-cac17a82b515
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：將引號放入字串中 (Windows Form)
有時，可能會想在文字字串中放入引號 \(" "\)。  例如：  
  
 She said, "You deserve a treat\!"  
  
 或者，您也可以使用 <xref:Microsoft.VisualBasic.ControlChars.Quote> 欄位當做常數。  
  
### 若要在程式碼中的字串中放置引號  
  
1.  在 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 中，請在資料列中插入兩個引號當做內嵌的引號。  在 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 和 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)] 中，請插入逸出序列 \(Escape Sequence\) \\" 當做內嵌的引號。  例如，使用以下程式碼來建立前置字串：  
  
    ```vb  
    Private Sub InsertQuote()  
       TextBox1.Text = "She said, ""You deserve a treat!"" "  
    End Sub  
  
    ```  
  
    ```csharp  
    private void InsertQuote(){  
       textBox1.Text = "She said, \"You deserve a treat!\" ";  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void InsertQuote()  
       {  
          textBox1->Text = "She said, \"You deserve a treat!\" ";  
       }  
    ```  
  
     \-或\-  
  
2.  插入 ASCII 或 Unicode 字元來當做引號。  在 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 中請使用 ASCII 字元 \(34\)。  在 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 中請使用 Unicode 字元 \(\\u0022\)。  
  
    ```vb  
    Private Sub InsertAscii()  
       TextBox1.Text = "She said, " & Chr(34) & "You deserve a treat!" & Chr(34)  
    End Sub  
  
    ```  
  
    ```csharp  
    private void InsertAscii(){  
       textBox1.Text = "She said, " + '\u0022' + "You deserve a treat!" + '\u0022';  
    }  
    ```  
  
    > [!NOTE]
    >  在此範例中您無法使用 \\u0022，因為無法使用基礎字元集中用以指定字元的通用字元名稱。  否則的話，將會導致 C3851。  如需詳細資訊，請參閱[編譯器錯誤 C3851](../Topic/Compiler%20Error%20C3851.md)。  
  
     \-或\-  
  
3.  您也可以定義字元的常數，並在需要時使用：  
  
    ```vb  
    Const quote As String = """"  
    TextBox1.Text = "She said, " & quote & "You deserve a treat!" & quote  
  
    ```  
  
    ```csharp  
    const string quote = "\"";  
    textBox1.Text = "She said, " + quote +  "You deserve a treat!"+ quote ;  
  
    ```  
  
    ```cpp  
    const String^ quote = "\"";  
    textBox1->Text = String::Concat("She said, ",  
       const_cast<String^>(quote), "You deserve a treat!",  
       const_cast<String^>(quote));  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.TextBox>   
 <xref:Microsoft.VisualBasic.ControlChars.Quote>   
 [TextBox 控制項概觀](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)   
 [如何：控制 Windows Form TextBox 控制項的插入點](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)   
 [如何：使用 Windows Form TextBox 控制項建立密碼文字方塊](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)   
 [如何：建立唯讀文字方塊](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)   
 [如何：在 Windows Form TextBox 控制項中選取文字](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)   
 [如何：檢視 Windows Form TextBox 控制項中的多行](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)   
 [TextBox 控制項](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
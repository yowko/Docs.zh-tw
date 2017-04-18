---
title: "如何：使用 Windows Form LinkLabel 控制項連結至物件或 Web 網頁 | Microsoft Docs"
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
  - "範例 [Windows Form], LinkLabel 控制項"
  - "連結, 至其他表單"
  - "LinkLabel 控制項 [Windows Form], 範例"
  - "LinkLabel 控制項 [Windows Form], 連結至物件或 Web 網頁"
  - "連結, 至其他表單"
  - "Web 網頁連結控制項"
  - "Windows Form, 連結到物件"
  - "Windows Form, 連結至 Web 網頁"
ms.assetid: 6c91c975-3cb7-4504-82f0-fc6255f8fb85
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：使用 Windows Form LinkLabel 控制項連結至物件或 Web 網頁
Windows Form <xref:System.Windows.Forms.LinkLabel> 控制項可讓您在表單上建立 Web 樣式連結。  按一下連結時，您可以變更其色彩以指示已瀏覽該連結。  如需變更色彩的詳細資訊，請參閱 [如何：變更 Windows Form LinkLabel 控制項的外觀](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)。  
  
## 連結至另一個表單  
  
#### 若要使用 LinkLabel 控制項連結至另一個表單  
  
1.  將 <xref:System.Windows.Forms.LinkLabel.Text%2A> 屬性設定為適當的標題。  
  
2.  設定 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> 屬性，決定標題的哪個部分會表示為連結。  指示它的方式是依與連結標籤外觀相關的屬性而定。  <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> 值是由包含兩個數字、開始字元位置和字元數目的 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> 物件所代表。  可以在 \[屬性\] 視窗中設定 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> 屬性，或使用類似下列的方式在程式碼中設定此屬性：  
  
    ```vb  
    ' In this code example, the link area has been set to begin  
    ' at the first character and extend for eight characters.  
    ' You may need to modify this based on the text entered in Step 1.  
    LinkLabel1.LinkArea = New LinkArea(0, 8)  
  
    ```  
  
    ```csharp  
    // In this code example, the link area has been set to begin  
    // at the first character and extend for eight characters.  
    // You may need to modify this based on the text entered in Step 1.  
    linkLabel1.LinkArea = new LinkArea(0,8);  
  
    ```  
  
    ```cpp  
    // In this code example, the link area has been set to begin  
    // at the first character and extend for eight characters.  
    // You may need to modify this based on the text entered in Step 1.  
    linkLabel1->LinkArea = LinkArea(0,8);  
    ```  
  
3.  在 <xref:System.Windows.Forms.LinkLabel.LinkClicked> 事件處理常式中叫用 <xref:System.Windows.Forms.Form.Show%2A> 方法在專案中開啟另一個表單，並將 <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> 屬性設定為 `true`。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> 類別的執行個體帶有被按一下的 <xref:System.Windows.Forms.LinkLabel> 控制項參考，因此不需要轉換 `sender`  物件。  
  
    ```vb  
    Protected Sub LinkLabel1_LinkClicked(ByVal Sender As System.Object, _  
       ByVal e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) _  
       Handles LinkLabel1.LinkClicked  
       ' Show another form.  
       Dim f2 As New Form()  
       f2.Show  
       LinkLabel1.LinkVisited = True  
    End Sub  
  
    ```  
  
    ```csharp  
    protected void linkLabel1_LinkClicked(object sender, System. Windows.Forms.LinkLabelLinkClickedEventArgs e)  
    {  
       // Show another form.  
       Form f2 = new Form();  
       f2.Show();  
       linkLabel1.LinkVisited = true;  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void linkLabel1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)  
       {  
          // Show another form.  
          Form ^ f2 = new Form();  
          f2->Show();  
          linkLabel1->LinkVisited = true;  
       }  
    ```  
  
## 連結至 Web 網頁  
 <xref:System.Windows.Forms.LinkLabel> 控制項也可使用預設的瀏覽器來顯示 Web 網頁。  
  
#### 若要啟動 Internet Explorer 及使用 LinkLabel 控制項連結至 Web 網頁  
  
1.  將 <xref:System.Windows.Forms.LinkLabel.Text%2A> 屬性設定為適當的標題。  
  
2.  設定 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> 屬性，決定標題的哪個部分會表示為連結。  
  
3.  在 <xref:System.Windows.Forms.LinkLabel.LinkClicked> 事件處理常式的例外狀況處理區塊當中，呼叫將 <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> 屬性設定為 `true`，並使用 <xref:System.Diagnostics.Process.Start%2A> 方法的第二個程序，以 URL 啟動預設瀏覽器。  若要使用 <xref:System.Diagnostics.Process.Start%2A> 方法，您需要加入 <xref:System.Diagnostics?displayProperty=fullName> 命名空間的參考。  
  
    > [!IMPORTANT]
    >  如果以下程式碼是在部分信任的環境 \(例如共用磁碟機\) 中執行，則在呼叫 `VisitLink` 方法時，JIT 編譯器會失敗。  `System.Diagnostics.Process.Start`  陳述式造成失敗的連結要求。  以下程式碼藉由在呼叫 `VisitLink` 方法時攔截例外狀況 \(Exception\)，可確保萬一 JIT 編譯器失敗，錯誤會順利處理。  
  
    ```vb  
    Private Sub LinkLabel1_LinkClicked(ByVal sender As System.Object, _  
       ByVal e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) _  
       Handles LinkLabel1.LinkClicked  
       Try  
          VisitLink()  
       Catch ex As Exception  
          ' The error message  
          MessageBox.Show("Unable to open link that was clicked.")  
       End Try  
    End Sub  
  
    Sub VisitLink()  
       ' Change the color of the link text by setting LinkVisited   
       ' to True.  
       LinkLabel1.LinkVisited = True  
       ' Call the Process.Start method to open the default browser   
       ' with a URL:  
       System.Diagnostics.Process.Start("http://www.microsoft.com")  
    End Sub  
  
    ```  
  
    ```csharp  
    private void linkLabel1_LinkClicked(object sender, System.Windows.Forms.LinkLabelLinkClickedEventArgs e)  
    {  
       try  
       {  
          VisitLink();  
       }  
       catch (Exception ex )  
       {  
          MessageBox.Show("Unable to open link that was clicked.");  
       }  
    }  
  
    private void VisitLink()  
    {  
       // Change the color of the link text by setting LinkVisited   
       // to true.  
       linkLabel1.LinkVisited = true;  
       //Call the Process.Start method to open the default browser   
       //with a URL:  
       System.Diagnostics.Process.Start("http://www.microsoft.com");  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void linkLabel1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)  
       {  
          try  
          {  
             VisitLink();  
          }  
          catch (Exception ^ ex)  
          {  
             MessageBox::Show("Unable to open link that was clicked.");  
          }  
       }  
    private:  
       void VisitLink()  
       {  
          // Change the color of the link text by setting LinkVisited   
          // to true.  
          linkLabel1->LinkVisited = true;  
          // Call the Process.Start method to open the default browser   
          // with a URL:  
          System::Diagnostics::Process::Start("http://www.microsoft.com");  
       }  
    ```  
  
## 請參閱  
 <xref:System.Diagnostics.Process.Start%2A?displayProperty=fullName>   
 [LinkLabel 控制項概觀](../../../../docs/framework/winforms/controls/linklabel-control-overview-windows-forms.md)   
 [如何：變更 Windows Form LinkLabel 控制項的外觀](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)   
 [LinkLabel 控制項](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)
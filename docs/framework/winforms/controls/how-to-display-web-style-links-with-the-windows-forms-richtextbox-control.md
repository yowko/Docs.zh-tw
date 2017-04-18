---
title: "如何：使用 Windows Form RichTextBox 控制項顯示 Web 樣式連結 | Microsoft Docs"
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
  - "範例 [Windows Form], 文字方塊"
  - "RichTextBox 控制項 [Windows Form], 連結至 Web 網頁"
  - "文字方塊, 顯示 Web 連結"
ms.assetid: 95089a37-a202-4f7a-94ee-6ee312908851
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：使用 Windows Form RichTextBox 控制項顯示 Web 樣式連結
Windows Form <xref:System.Windows.Forms.RichTextBox> 控制項可以使用色彩和底線顯示 Web 連結。  您可以寫入程式碼來在按一下連結時，開啟瀏覽器視窗以顯示連結文字中指定的網站。  
  
### 若要使用 RichTextBox 控制項連結至網頁  
  
1.  將 <xref:System.Windows.Forms.RichTextBox.Text%2A> 屬性設定為包含有效 URL \(例如 "http:\/\/www.microsoft.com\/taiwan"\) 的字串。  
  
2.  確定 <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> 屬性是設為 `true` \(預設值\)。  
  
3.  建立 <xref:System.Diagnostics.Process> 物件的新的全域執行個體。  
  
4.  為 <xref:System.Windows.Forms.RichTextBox.LinkClicked> 事件撰寫事件處理常式，將所需文字傳送到瀏覽器。  
  
     在以下範例中，<xref:System.Windows.Forms.RichTextBox.LinkClicked> 事件將 Internet Explorer 的執行個體，開啟至 <xref:System.Windows.Forms.RichTextBox> 控制項的 <xref:System.Windows.Forms.RichTextBox.Text%2A> 屬性中指定之 URL。  這個範例假設含 <xref:System.Windows.Forms.RichTextBox> 控制項的表單。  
  
    > [!IMPORTANT]
    >  在呼叫 <xref:System.Diagnostics.Process.Start%2A?displayProperty=fullName> 方法時，如果您是在部分信任的內容中執行程式碼，將會因為權限不足而發生 <xref:System.Security.SecurityException> 例外狀況。  如需詳細資訊，請參閱[Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md)。  
  
    ```vb  
    Public p As New System.Diagnostics.Process  
    Private Sub RichTextBox1_LinkClicked _  
       (ByVal sender As Object, ByVal e As _  
       System.Windows.Forms.LinkClickedEventArgs) _  
       Handles RichTextBox1.LinkClicked  
          ' Call Process.Start method to open a browser  
          ' with link text as URL.  
          p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText)  
    End Sub  
  
    ```  
  
    ```csharp  
    public System.Diagnostics.Process p = new System.Diagnostics.Process();  
  
    private void richTextBox1_LinkClicked(object sender,   
    System.Windows.Forms.LinkClickedEventArgs e)  
    {  
       // Call Process.Start method to open a browser  
       // with link text as URL.  
       p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText);  
    }  
  
    ```  
  
    ```cpp  
    public:  
       System::Diagnostics::Process ^ p;  
  
    private:  
       void richTextBox1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkClickedEventArgs ^  e)  
       {  
          // Call Process.Start method to open a browser  
          // with link text as URL.  
          p = System::Diagnostics::Process::Start("IExplore.exe",  
             e->LinkText);  
       }  
    ```  
  
     \([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) 您必須初始化處理序`p`，方法是將以下陳述式加入表單的建構函式中：  
  
    ```cpp  
    p = gcnew System::Diagnostics::Process();  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) 將下列程式碼加入表單的建構函式以註冊事件處理常式。  
  
    ```csharp  
    this.richTextBox1.LinkClicked += new   
       System.Windows.Forms.LinkClickedEventHandler  
       (this.richTextBox1_LinkClicked);  
  
    ```  
  
    ```cpp  
    this->richTextBox1->LinkClicked += gcnew  
       System::Windows::Forms::LinkClickedEventHandler  
       (this, &Form1::richTextBox1_LinkClicked);  
    ```  
  
     一旦完成使用後，務必立即停止您已建立的處理序。  在參考上述的程式碼之後，用以停止處理序的程式碼可能看起來像是這樣：  
  
    ```vb  
    Public Sub StopWebProcess()  
       p.Kill()  
    End Sub  
  
    ```  
  
    ```csharp  
    public void StopWebProcess()  
    {  
       p.Kill();  
    }  
  
    ```  
  
    ```cpp  
    public: void StopWebProcess()  
    {  
       p->Kill();  
    }  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>   
 <xref:System.Windows.Forms.RichTextBox.LinkClicked>   
 <xref:System.Windows.Forms.RichTextBox>   
 [RichTextBox 控制項](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)   
 [在 Windows Form 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
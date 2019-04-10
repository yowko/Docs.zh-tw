---
title: HOW TO：使用 Windows Forms RichTextBox 控制項顯示 Web 樣式連結
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying Web links
- examples [Windows Forms], text boxes
- RichTextBox control [Windows Forms], linking to Web pages
ms.assetid: 95089a37-a202-4f7a-94ee-6ee312908851
ms.openlocfilehash: 1902557e5dbdcee3c1facc18b6f5c3037c266a8e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148235"
---
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a>HOW TO：使用 Windows Forms RichTextBox 控制項顯示 Web 樣式連結
Windows Form<xref:System.Windows.Forms.RichTextBox>控制項可以顯示為彩色和加底線的網頁連結。 您可以撰寫程式碼，會開啟瀏覽器視窗顯示時按一下連結，連結文字中指定的網站。  
  
### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a>若要連結至網頁上使用 RichTextBox 控制項  
  
1.  設定<xref:System.Windows.Forms.RichTextBox.Text%2A>屬性設為字串，其中包含有效的 URL (例如，"http://www.microsoft.com/」)。  
  
2.  請確定<xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>屬性設定為`true`（預設值）。  
  
3.  建立新的全域執行個體的<xref:System.Diagnostics.Process>物件。  
  
4.  撰寫事件處理常式<xref:System.Windows.Forms.RichTextBox.LinkClicked>傳送瀏覽器所需的文字的事件。  
  
     在下列範例中，<xref:System.Windows.Forms.RichTextBox.LinkClicked>事件會開啟 Internet Explorer 中指定的 URL 的執行個體<xref:System.Windows.Forms.RichTextBox.Text%2A>屬性<xref:System.Windows.Forms.RichTextBox>控制項。 這個範例假設表單<xref:System.Windows.Forms.RichTextBox>控制項。  
  
    > [!IMPORTANT]
    >  在呼叫<xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>方法中，您將會遇到<xref:System.Security.SecurityException>例外狀況，如果您在部分信任內容中執行的程式碼，因為沒有足夠的權限。 如需詳細資訊，請參閱[程式碼存取安全性基本概念](../../misc/code-access-security-basics.md)。  
  
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
  
     ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 您必須初始化程序`p`，可執行下列陳述式併入您的表單的建構函式：  
  
    ```cpp  
    p = gcnew System::Diagnostics::Process();  
    ```  
  
     (Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。  
  
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
  
     請務必立即停止您已經建立完成之後使用它的程序。 以上所顯示的程式碼參考時，您的程式碼，以停止處理程序可能會看起來像這樣：  
  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>
- <xref:System.Windows.Forms.RichTextBox.LinkClicked>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox 控制項](richtextbox-control-windows-forms.md)
- [在 Windows Form 上使用的控制項](controls-to-use-on-windows-forms.md)

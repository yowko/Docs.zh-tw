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
ms.openlocfilehash: ce71981f7b233d3e168689c766128646eed3e981
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046178"
---
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a>作法：使用 Windows Forms RichTextBox 控制項顯示 Web 樣式連結

Windows Forms <xref:System.Windows.Forms.RichTextBox>控制項可以將網頁連結顯示為彩色和加上底線。 您可以撰寫程式碼, 開啟瀏覽器視窗, 在按一下連結時, 顯示連結文字中指定的網站。

### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a>若要使用 RichTextBox 控制項連結至網頁

1. 將屬性設定為包含有效 URL 的字串 (例如, "http://www.microsoft.com/")。 <xref:System.Windows.Forms.RichTextBox.Text%2A>

2. 請確定<xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>屬性設定為`true` (預設值)。

3. 建立<xref:System.Diagnostics.Process>物件的新全域實例。

4. 撰寫<xref:System.Windows.Forms.RichTextBox.LinkClicked>事件的事件處理常式, 以傳送所需的文字給瀏覽器。

    在下列範例中, <xref:System.Windows.Forms.RichTextBox.LinkClicked>事件會將 Internet Explorer 的實例開啟至<xref:System.Windows.Forms.RichTextBox>控制項的<xref:System.Windows.Forms.RichTextBox.Text%2A>屬性中所指定的 URL。 這個範例假設有一個表單<xref:System.Windows.Forms.RichTextBox>具有控制項。

    > [!IMPORTANT]
    > 在呼叫<xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>方法時, 如果您因為許可權<xref:System.Security.SecurityException>不足而在部分信任內容中執行程式碼, 就會發生例外狀況。 如需詳細資訊，請參閱[程式碼存取安全性基本概念](../../misc/code-access-security-basics.md)。

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

    (視覺C++效果)您必須初始化處理`p`程式, 方法是在表單的函式中包含下列語句:

    ```cpp
    p = gcnew System::Diagnostics::Process();
    ```

    (視覺C#效果, C++視覺效果)將下列程式碼放在表單的函式中, 以註冊事件處理常式。

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

    當您完成使用程式之後, 請務必立即停止您所建立的進程。 參考上面顯示的程式碼, 停止進程的程式碼可能如下所示:

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
- [在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)

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
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="83ff8-102">作法：使用 Windows Forms RichTextBox 控制項顯示 Web 樣式連結</span><span class="sxs-lookup"><span data-stu-id="83ff8-102">How to: Display Web-Style Links with the Windows Forms RichTextBox Control</span></span>

<span data-ttu-id="83ff8-103">Windows Forms <xref:System.Windows.Forms.RichTextBox>控制項可以將網頁連結顯示為彩色和加上底線。</span><span class="sxs-lookup"><span data-stu-id="83ff8-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display Web links as colored and underlined.</span></span> <span data-ttu-id="83ff8-104">您可以撰寫程式碼, 開啟瀏覽器視窗, 在按一下連結時, 顯示連結文字中指定的網站。</span><span class="sxs-lookup"><span data-stu-id="83ff8-104">You can write code that opens a browser window showing the Web site specified in the link text when the link is clicked.</span></span>

### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a><span data-ttu-id="83ff8-105">若要使用 RichTextBox 控制項連結至網頁</span><span class="sxs-lookup"><span data-stu-id="83ff8-105">To link to a Web page with the RichTextBox control</span></span>

1. <span data-ttu-id="83ff8-106">將屬性設定為包含有效 URL 的字串 (例如, "http://www.microsoft.com/")。 <xref:System.Windows.Forms.RichTextBox.Text%2A></span><span class="sxs-lookup"><span data-stu-id="83ff8-106">Set the <xref:System.Windows.Forms.RichTextBox.Text%2A> property to a string that includes a valid URL (for example, "http://www.microsoft.com/").</span></span>

2. <span data-ttu-id="83ff8-107">請確定<xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>屬性設定為`true` (預設值)。</span><span class="sxs-lookup"><span data-stu-id="83ff8-107">Make sure the <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> property is set to `true` (the default).</span></span>

3. <span data-ttu-id="83ff8-108">建立<xref:System.Diagnostics.Process>物件的新全域實例。</span><span class="sxs-lookup"><span data-stu-id="83ff8-108">Create a new global instance of the <xref:System.Diagnostics.Process> object.</span></span>

4. <span data-ttu-id="83ff8-109">撰寫<xref:System.Windows.Forms.RichTextBox.LinkClicked>事件的事件處理常式, 以傳送所需的文字給瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="83ff8-109">Write an event handler for the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event that sends the browser the desired text.</span></span>

    <span data-ttu-id="83ff8-110">在下列範例中, <xref:System.Windows.Forms.RichTextBox.LinkClicked>事件會將 Internet Explorer 的實例開啟至<xref:System.Windows.Forms.RichTextBox>控制項的<xref:System.Windows.Forms.RichTextBox.Text%2A>屬性中所指定的 URL。</span><span class="sxs-lookup"><span data-stu-id="83ff8-110">In the example below, the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event opens an instance of Internet Explorer to the URL specified in the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="83ff8-111">這個範例假設有一個表單<xref:System.Windows.Forms.RichTextBox>具有控制項。</span><span class="sxs-lookup"><span data-stu-id="83ff8-111">This example assumes a form with a <xref:System.Windows.Forms.RichTextBox> control.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="83ff8-112">在呼叫<xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>方法時, 如果您因為許可權<xref:System.Security.SecurityException>不足而在部分信任內容中執行程式碼, 就會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="83ff8-112">In calling the <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> method, you will encounter a <xref:System.Security.SecurityException> exception if you are running the code in a partial-trust context because of insufficient privileges.</span></span> <span data-ttu-id="83ff8-113">如需詳細資訊，請參閱[程式碼存取安全性基本概念](../../misc/code-access-security-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="83ff8-113">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

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

    <span data-ttu-id="83ff8-114">(視覺C++效果)您必須初始化處理`p`程式, 方法是在表單的函式中包含下列語句:</span><span class="sxs-lookup"><span data-stu-id="83ff8-114">(Visual C++) You must initialize process `p`, which you can do by including the following statement in the constructor of your form:</span></span>

    ```cpp
    p = gcnew System::Diagnostics::Process();
    ```

    <span data-ttu-id="83ff8-115">(視覺C#效果, C++視覺效果)將下列程式碼放在表單的函式中, 以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="83ff8-115">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>

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

    <span data-ttu-id="83ff8-116">當您完成使用程式之後, 請務必立即停止您所建立的進程。</span><span class="sxs-lookup"><span data-stu-id="83ff8-116">It is important to immediately stop the process you have created once you have finished working with it.</span></span> <span data-ttu-id="83ff8-117">參考上面顯示的程式碼, 停止進程的程式碼可能如下所示:</span><span class="sxs-lookup"><span data-stu-id="83ff8-117">Referring to the code presented above, your code to stop the process might look like this:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="83ff8-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83ff8-118">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>
- <xref:System.Windows.Forms.RichTextBox.LinkClicked>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="83ff8-119">RichTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="83ff8-119">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="83ff8-120">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="83ff8-120">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)

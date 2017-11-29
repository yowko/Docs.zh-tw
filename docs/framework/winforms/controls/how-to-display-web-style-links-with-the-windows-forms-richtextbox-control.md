---
title: "如何：使用 Windows Form RichTextBox 控制項顯示 Web 樣式連結"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying Web links
- examples [Windows Forms], text boxes
- RichTextBox control [Windows Forms], linking to Web pages
ms.assetid: 95089a37-a202-4f7a-94ee-6ee312908851
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5391c48720e68a8a7e6e0fb7735252d00025adc6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="eea14-102">如何：使用 Windows Form RichTextBox 控制項顯示 Web 樣式連結</span><span class="sxs-lookup"><span data-stu-id="eea14-102">How to: Display Web-Style Links with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="eea14-103">Windows Form<xref:System.Windows.Forms.RichTextBox>控制項可以顯示為彩色和加底線的網頁連結。</span><span class="sxs-lookup"><span data-stu-id="eea14-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display Web links as colored and underlined.</span></span> <span data-ttu-id="eea14-104">您可以撰寫會顯示在按下連結時，連結文字中指定的網站的瀏覽器視窗開啟的程式碼。</span><span class="sxs-lookup"><span data-stu-id="eea14-104">You can write code that opens a browser window showing the Web site specified in the link text when the link is clicked.</span></span>  
  
### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a><span data-ttu-id="eea14-105">若要連結至 Web 網頁與 RichTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="eea14-105">To link to a Web page with the RichTextBox control</span></span>  
  
1.  <span data-ttu-id="eea14-106">設定<xref:System.Windows.Forms.RichTextBox.Text%2A>屬性設為字串，其中包含有效的 URL (例如"http://www.microsoft.com/taiwan/")。</span><span class="sxs-lookup"><span data-stu-id="eea14-106">Set the <xref:System.Windows.Forms.RichTextBox.Text%2A> property to a string that includes a valid URL (for example, "http://www.microsoft.com/").</span></span>  
  
2.  <span data-ttu-id="eea14-107">請確定<xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>屬性設定為`true`（預設值）。</span><span class="sxs-lookup"><span data-stu-id="eea14-107">Make sure the <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> property is set to `true` (the default).</span></span>  
  
3.  <span data-ttu-id="eea14-108">建立新的全域執行個體的<xref:System.Diagnostics.Process>物件。</span><span class="sxs-lookup"><span data-stu-id="eea14-108">Create a new global instance of the <xref:System.Diagnostics.Process> object.</span></span>  
  
4.  <span data-ttu-id="eea14-109">撰寫事件處理常式<xref:System.Windows.Forms.RichTextBox.LinkClicked>傳送瀏覽器所需的文字的事件。</span><span class="sxs-lookup"><span data-stu-id="eea14-109">Write an event handler for the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event that sends the browser the desired text.</span></span>  
  
     <span data-ttu-id="eea14-110">在下列範例中，<xref:System.Windows.Forms.RichTextBox.LinkClicked>事件就會開啟 Internet Explorer 中指定的 URL 的執行個體<xref:System.Windows.Forms.RichTextBox.Text%2A>屬性<xref:System.Windows.Forms.RichTextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="eea14-110">In the example below, the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event opens an instance of Internet Explorer to the URL specified in the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="eea14-111">這個範例假設的表單具有<xref:System.Windows.Forms.RichTextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="eea14-111">This example assumes a form with a <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="eea14-112">在呼叫<xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>方法，您將會遇到<xref:System.Security.SecurityException>例外狀況，如果您因為權限不足，而部分信任的內容中執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="eea14-112">In calling the <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> method, you will encounter a <xref:System.Security.SecurityException> exception if you are running the code in a partial-trust context because of insufficient privileges.</span></span> <span data-ttu-id="eea14-113">如需詳細資訊，請參閱[程式碼存取安全性基本概念](../../../../docs/framework/misc/code-access-security-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="eea14-113">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
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
  
     <span data-ttu-id="eea14-114">([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 您必須先初始化程序`p`，可執行下列陳述式併入您的表單的建構函式：</span><span class="sxs-lookup"><span data-stu-id="eea14-114">([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) You must initialize process `p`, which you can do by including the following statement in the constructor of your form:</span></span>  
  
    ```cpp  
    p = gcnew System::Diagnostics::Process();  
    ```  
  
     <span data-ttu-id="eea14-115">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 請將下列程式碼置於表單的建構函式中，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="eea14-115">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
     <span data-ttu-id="eea14-116">請務必立即停止處理序當處理完成後，您已建立。</span><span class="sxs-lookup"><span data-stu-id="eea14-116">It is important to immediately stop the process you have created once you have finished working with it.</span></span> <span data-ttu-id="eea14-117">參考上述程式碼，您的程式碼，以停止處理程序可能會看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="eea14-117">Referring to the code presented above, your code to stop the process might look like this:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eea14-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eea14-118">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>  
 <xref:System.Windows.Forms.RichTextBox.LinkClicked>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="eea14-119">RichTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="eea14-119">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="eea14-120">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="eea14-120">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)

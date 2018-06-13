---
title: 如何：使用 Windows Form LinkLabel 控制項連結至物件或 Web 網頁
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], LinkLabel control
- Windows Forms, linking to objects
- Web page link control
- linking [Windows Forms], to other forms
- Windows Forms, linking to Web pages
- links [Windows Forms], to other forms
- LinkLabel control [Windows Forms], linking to object or Web page
- LinkLabel control [Windows Forms], examples
ms.assetid: 6c91c975-3cb7-4504-82f0-fc6255f8fb85
ms.openlocfilehash: 9957eae7e15c99ec259574b435402420c6bcf5f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539629"
---
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a><span data-ttu-id="893b6-102">如何：使用 Windows Form LinkLabel 控制項連結至物件或 Web 網頁</span><span class="sxs-lookup"><span data-stu-id="893b6-102">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>
<span data-ttu-id="893b6-103">Windows Form<xref:System.Windows.Forms.LinkLabel>控制項可讓您在表單上建立 Web 樣式連結。</span><span class="sxs-lookup"><span data-stu-id="893b6-103">The Windows Forms <xref:System.Windows.Forms.LinkLabel> control allows you to create Web-style links on your form.</span></span> <span data-ttu-id="893b6-104">按一下連結時，您可以變更其色彩會以指出瀏覽的連結。</span><span class="sxs-lookup"><span data-stu-id="893b6-104">When the link is clicked, you can change its color to indicate the link has been visited.</span></span> <span data-ttu-id="893b6-105">如需有關如何變更色彩的詳細資訊，請參閱[如何： 變更 Windows Form LinkLabel 控制項的外觀](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)。</span><span class="sxs-lookup"><span data-stu-id="893b6-105">For more information on changing the color, see [How to: Change the Appearance of the Windows Forms LinkLabel Control](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).</span></span>  
  
## <a name="linking-to-another-form"></a><span data-ttu-id="893b6-106">連結至另一個表單</span><span class="sxs-lookup"><span data-stu-id="893b6-106">Linking to Another Form</span></span>  
  
#### <a name="to-link-to-another-form-with-a-linklabel-control"></a><span data-ttu-id="893b6-107">若要連結至另一種形式與 LinkLabel 控制項</span><span class="sxs-lookup"><span data-stu-id="893b6-107">To link to another form with a LinkLabel control</span></span>  
  
1.  <span data-ttu-id="893b6-108">設定<xref:System.Windows.Forms.LinkLabel.Text%2A>屬性設為適當的標題。</span><span class="sxs-lookup"><span data-stu-id="893b6-108">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>  
  
2.  <span data-ttu-id="893b6-109">設定<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>屬性來判斷哪一個部分的標題會指出以連結形式。</span><span class="sxs-lookup"><span data-stu-id="893b6-109">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span> <span data-ttu-id="893b6-110">指示它的方式取決於連結標籤與外觀相關屬性。</span><span class="sxs-lookup"><span data-stu-id="893b6-110">How it is indicated depends on the appearance-related properties of the link label.</span></span> <span data-ttu-id="893b6-111"><xref:System.Windows.Forms.LinkLabel.LinkArea%2A>值由<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>物件，其中包含兩個數字，起始字元位置的字元數。</span><span class="sxs-lookup"><span data-stu-id="893b6-111">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> value is represented by a <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> object containing two numbers, the starting character position and the number of characters.</span></span> <span data-ttu-id="893b6-112"><xref:System.Windows.Forms.LinkLabel.LinkArea%2A>可以設定屬性，在 [屬性] 視窗中或在程式碼類似下列的方式：</span><span class="sxs-lookup"><span data-stu-id="893b6-112">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property can be set in the Properties window or in code in a manner similar to the following:</span></span>  
  
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
  
3.  <span data-ttu-id="893b6-113">在<xref:System.Windows.Forms.LinkLabel.LinkClicked>事件處理常式，叫用<xref:System.Windows.Forms.Form.Show%2A>方法在專案中，開啟另一個表單，並設定<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="893b6-113">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, invoke the <xref:System.Windows.Forms.Form.Show%2A> method to open another form in the project, and set the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="893b6-114">執行個體<xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs>類別具有其參照<xref:System.Windows.Forms.LinkLabel>已按下控制項，因此不需要轉換`sender`物件。</span><span class="sxs-lookup"><span data-stu-id="893b6-114">An instance of the <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> class carries a reference to the <xref:System.Windows.Forms.LinkLabel> control that was clicked, so there is no need to cast the `sender` object.</span></span>  
  
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
  
## <a name="linking-to-a-web-page"></a><span data-ttu-id="893b6-115">連結至 Web 網頁</span><span class="sxs-lookup"><span data-stu-id="893b6-115">Linking to a Web Page</span></span>  
 <span data-ttu-id="893b6-116"><xref:System.Windows.Forms.LinkLabel>控制項也可用來顯示預設的瀏覽器的網頁。</span><span class="sxs-lookup"><span data-stu-id="893b6-116">The <xref:System.Windows.Forms.LinkLabel> control can also be used to display a Web page with the default browser.</span></span>  
  
#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a><span data-ttu-id="893b6-117">若要啟動 Internet Explorer 和網頁的連結與 LinkLabel 控制項</span><span class="sxs-lookup"><span data-stu-id="893b6-117">To start Internet Explorer and link to a Web page with a LinkLabel control</span></span>  
  
1.  <span data-ttu-id="893b6-118">設定<xref:System.Windows.Forms.LinkLabel.Text%2A>屬性設為適當的標題。</span><span class="sxs-lookup"><span data-stu-id="893b6-118">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>  
  
2.  <span data-ttu-id="893b6-119">設定<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>屬性來判斷哪一個部分的標題會指出以連結形式。</span><span class="sxs-lookup"><span data-stu-id="893b6-119">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span>  
  
3.  <span data-ttu-id="893b6-120">在<xref:System.Windows.Forms.LinkLabel.LinkClicked>之中例外狀況處理區塊中，事件處理常式，呼叫第二個程序，以設定<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>屬性`true`，並使用<xref:System.Diagnostics.Process.Start%2A>方法以 URL 啟動預設瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="893b6-120">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, in the midst of an exception-handling block, call a second procedure that sets the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true` and uses the <xref:System.Diagnostics.Process.Start%2A> method to start the default browser with a URL.</span></span> <span data-ttu-id="893b6-121">若要使用<xref:System.Diagnostics.Process.Start%2A>方法，您需要將參考加入<xref:System.Diagnostics?displayProperty=nameWithType>命名空間。</span><span class="sxs-lookup"><span data-stu-id="893b6-121">To use the <xref:System.Diagnostics.Process.Start%2A> method you need to add a reference to the <xref:System.Diagnostics?displayProperty=nameWithType> namespace.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="893b6-122">如果在部分信任環境中執行下列程式碼 (例如共用的磁碟機上)，JIT 編譯器失敗時`VisitLink`方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="893b6-122">If the code below is run in a partial-trust environment (such as on a shared drive), the JIT compiler fails when the `VisitLink` method is called.</span></span> <span data-ttu-id="893b6-123">`System.Diagnostics.Process.Start`陳述式會導致失敗的連結要求。</span><span class="sxs-lookup"><span data-stu-id="893b6-123">The `System.Diagnostics.Process.Start` statement causes a link demand that fails.</span></span> <span data-ttu-id="893b6-124">藉由捕捉例外狀況時`VisitLink`呼叫方法時，下列程式碼可確保，如果 JIT 編譯器失敗，錯誤處理是依正常程序。</span><span class="sxs-lookup"><span data-stu-id="893b6-124">By catching the exception when the `VisitLink` method is called, the code below ensures that if the JIT compiler fails, the error is handled gracefully.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="893b6-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="893b6-125">See Also</span></span>  
 <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="893b6-126">LinkLabel 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="893b6-126">LinkLabel Control Overview</span></span>](../../../../docs/framework/winforms/controls/linklabel-control-overview-windows-forms.md)  
 [<span data-ttu-id="893b6-127">操作說明：變更 Windows Forms LinkLabel 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="893b6-127">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)  
 [<span data-ttu-id="893b6-128">LinkLabel 控制項</span><span class="sxs-lookup"><span data-stu-id="893b6-128">LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)

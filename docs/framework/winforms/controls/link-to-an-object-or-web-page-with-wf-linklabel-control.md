---
title: HOW TO：使用 Windows Forms LinkLabel 控制項連結至物件或網頁
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
ms.openlocfilehash: 1ed27826b92d34f05055ab7fdda2a16eb4a79b17
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952168"
---
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a><span data-ttu-id="41050-102">HOW TO：使用 Windows Forms LinkLabel 控制項連結至物件或網頁</span><span class="sxs-lookup"><span data-stu-id="41050-102">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>
<span data-ttu-id="41050-103">Windows Forms <xref:System.Windows.Forms.LinkLabel>控制項可讓您在表單上建立 Web 樣式連結。</span><span class="sxs-lookup"><span data-stu-id="41050-103">The Windows Forms <xref:System.Windows.Forms.LinkLabel> control allows you to create Web-style links on your form.</span></span> <span data-ttu-id="41050-104">按一下連結時, 您可以變更其色彩, 以表示已流覽過該連結。</span><span class="sxs-lookup"><span data-stu-id="41050-104">When the link is clicked, you can change its color to indicate the link has been visited.</span></span> <span data-ttu-id="41050-105">如需變更色彩的詳細資訊, 請[參閱如何:變更 Windows Forms LinkLabel 控制項](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)的外觀。</span><span class="sxs-lookup"><span data-stu-id="41050-105">For more information on changing the color, see [How to: Change the Appearance of the Windows Forms LinkLabel Control](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).</span></span>  
  
## <a name="linking-to-another-form"></a><span data-ttu-id="41050-106">連結至另一個表單</span><span class="sxs-lookup"><span data-stu-id="41050-106">Linking to Another Form</span></span>  
  
#### <a name="to-link-to-another-form-with-a-linklabel-control"></a><span data-ttu-id="41050-107">若要使用 LinkLabel 控制項連結至另一個表單</span><span class="sxs-lookup"><span data-stu-id="41050-107">To link to another form with a LinkLabel control</span></span>  
  
1. <span data-ttu-id="41050-108"><xref:System.Windows.Forms.LinkLabel.Text%2A>將屬性設定為適當的標題。</span><span class="sxs-lookup"><span data-stu-id="41050-108">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>  
  
2. <span data-ttu-id="41050-109"><xref:System.Windows.Forms.LinkLabel.LinkArea%2A>設定屬性, 以決定要將哪一部分的標題指定為連結。</span><span class="sxs-lookup"><span data-stu-id="41050-109">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span> <span data-ttu-id="41050-110">其表示方式取決於連結標籤的外觀相關屬性。</span><span class="sxs-lookup"><span data-stu-id="41050-110">How it is indicated depends on the appearance-related properties of the link label.</span></span> <span data-ttu-id="41050-111">此<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>值以包含兩個<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>數位的物件、起始字元位置和字元數來表示。</span><span class="sxs-lookup"><span data-stu-id="41050-111">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> value is represented by a <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> object containing two numbers, the starting character position and the number of characters.</span></span> <span data-ttu-id="41050-112"><xref:System.Windows.Forms.LinkLabel.LinkArea%2A>屬性可以在屬性視窗或程式碼中, 以類似下列的方式設定:</span><span class="sxs-lookup"><span data-stu-id="41050-112">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property can be set in the Properties window or in code in a manner similar to the following:</span></span>  
  
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
  
3. <span data-ttu-id="41050-113">在事件處理常式中, <xref:System.Windows.Forms.Form.Show%2A>叫用方法以在<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>專案中開啟另一個表單, 並將屬性設定為。 `true` <xref:System.Windows.Forms.LinkLabel.LinkClicked></span><span class="sxs-lookup"><span data-stu-id="41050-113">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, invoke the <xref:System.Windows.Forms.Form.Show%2A> method to open another form in the project, and set the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="41050-114"><xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs>類別的實例會攜帶已按<xref:System.Windows.Forms.LinkLabel>下之控制項的參考, 因此不需要轉換`sender`物件。</span><span class="sxs-lookup"><span data-stu-id="41050-114">An instance of the <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> class carries a reference to the <xref:System.Windows.Forms.LinkLabel> control that was clicked, so there is no need to cast the `sender` object.</span></span>  
  
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
  
## <a name="linking-to-a-web-page"></a><span data-ttu-id="41050-115">連結至網頁</span><span class="sxs-lookup"><span data-stu-id="41050-115">Linking to a Web Page</span></span>  
 <span data-ttu-id="41050-116"><xref:System.Windows.Forms.LinkLabel>控制項也可以用來顯示具有預設瀏覽器的網頁。</span><span class="sxs-lookup"><span data-stu-id="41050-116">The <xref:System.Windows.Forms.LinkLabel> control can also be used to display a Web page with the default browser.</span></span>  
  
#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a><span data-ttu-id="41050-117">啟動 Internet Explorer 並連結至具有 LinkLabel 控制項的網頁</span><span class="sxs-lookup"><span data-stu-id="41050-117">To start Internet Explorer and link to a Web page with a LinkLabel control</span></span>  
  
1. <span data-ttu-id="41050-118"><xref:System.Windows.Forms.LinkLabel.Text%2A>將屬性設定為適當的標題。</span><span class="sxs-lookup"><span data-stu-id="41050-118">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>  
  
2. <span data-ttu-id="41050-119"><xref:System.Windows.Forms.LinkLabel.LinkArea%2A>設定屬性, 以決定要將哪一部分的標題指定為連結。</span><span class="sxs-lookup"><span data-stu-id="41050-119">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span>  
  
3. <span data-ttu-id="41050-120">在事件處理常式中, 在例外狀況處理區塊的過程中呼叫第二個程式, <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>將<xref:System.Diagnostics.Process.Start%2A>屬性設定為`true` , 並使用方法來啟動具有 URL 的預設瀏覽器。 <xref:System.Windows.Forms.LinkLabel.LinkClicked></span><span class="sxs-lookup"><span data-stu-id="41050-120">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, in the midst of an exception-handling block, call a second procedure that sets the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true` and uses the <xref:System.Diagnostics.Process.Start%2A> method to start the default browser with a URL.</span></span> <span data-ttu-id="41050-121">若要使用<xref:System.Diagnostics.Process.Start%2A>方法, 您必須加入<xref:System.Diagnostics?displayProperty=nameWithType>命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="41050-121">To use the <xref:System.Diagnostics.Process.Start%2A> method you need to add a reference to the <xref:System.Diagnostics?displayProperty=nameWithType> namespace.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="41050-122">如果下列程式碼是在部分信任環境中執行 (例如在共用磁片磁碟機上), 則在呼叫`VisitLink`方法時, JIT 編譯程式會失敗。</span><span class="sxs-lookup"><span data-stu-id="41050-122">If the code below is run in a partial-trust environment (such as on a shared drive), the JIT compiler fails when the `VisitLink` method is called.</span></span> <span data-ttu-id="41050-123">`System.Diagnostics.Process.Start`語句會導致連結要求失敗。</span><span class="sxs-lookup"><span data-stu-id="41050-123">The `System.Diagnostics.Process.Start` statement causes a link demand that fails.</span></span> <span data-ttu-id="41050-124">藉由在呼叫`VisitLink`方法時攔截例外狀況, 下列程式碼可確保如果 JIT 編譯程式失敗, 則會正常處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="41050-124">By catching the exception when the `VisitLink` method is called, the code below ensures that if the JIT compiler fails, the error is handled gracefully.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="41050-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41050-125">See also</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- [<span data-ttu-id="41050-126">LinkLabel 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="41050-126">LinkLabel Control Overview</span></span>](linklabel-control-overview-windows-forms.md)
- [<span data-ttu-id="41050-127">如何：變更 Windows Forms LinkLabel 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="41050-127">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
- [<span data-ttu-id="41050-128">LinkLabel 控制項</span><span class="sxs-lookup"><span data-stu-id="41050-128">LinkLabel Control</span></span>](linklabel-control-windows-forms.md)

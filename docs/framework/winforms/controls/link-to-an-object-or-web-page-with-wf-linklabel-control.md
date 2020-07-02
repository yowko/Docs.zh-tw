---
title: 使用 LinkLabel 控制項連結至物件或網頁
description: 瞭解如何使用 Windows Forms LinkLabel 控制項，建立物件或網頁的 Web 樣式連結。
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
ms.openlocfilehash: a5fb1c03e9a8d82fe77f4133ba04c42114787d23
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618308"
---
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a><span data-ttu-id="53369-103">如何：使用 Windows Form LinkLabel 控制項連結至物件或 Web 網頁</span><span class="sxs-lookup"><span data-stu-id="53369-103">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>

<span data-ttu-id="53369-104">Windows Forms <xref:System.Windows.Forms.LinkLabel> 控制項可讓您在表單上建立 Web 樣式連結。</span><span class="sxs-lookup"><span data-stu-id="53369-104">The Windows Forms <xref:System.Windows.Forms.LinkLabel> control allows you to create Web-style links on your form.</span></span> <span data-ttu-id="53369-105">按一下連結時，您可以變更其色彩，以表示已流覽過該連結。</span><span class="sxs-lookup"><span data-stu-id="53369-105">When the link is clicked, you can change its color to indicate the link has been visited.</span></span> <span data-ttu-id="53369-106">如需變更色彩的詳細資訊，請參閱[如何：變更 Windows Forms LinkLabel 控制項的外觀](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)。</span><span class="sxs-lookup"><span data-stu-id="53369-106">For more information on changing the color, see [How to: Change the Appearance of the Windows Forms LinkLabel Control](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).</span></span>

## <a name="linking-to-another-form"></a><span data-ttu-id="53369-107">連結至另一個表單</span><span class="sxs-lookup"><span data-stu-id="53369-107">Linking to Another Form</span></span>

#### <a name="to-link-to-another-form-with-a-linklabel-control"></a><span data-ttu-id="53369-108">若要使用 LinkLabel 控制項連結至另一個表單</span><span class="sxs-lookup"><span data-stu-id="53369-108">To link to another form with a LinkLabel control</span></span>

1. <span data-ttu-id="53369-109">將 <xref:System.Windows.Forms.LinkLabel.Text%2A> 屬性設定為適當的標題。</span><span class="sxs-lookup"><span data-stu-id="53369-109">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>

2. <span data-ttu-id="53369-110">設定 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> 屬性，以決定要將哪一部分的標題指定為連結。</span><span class="sxs-lookup"><span data-stu-id="53369-110">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span> <span data-ttu-id="53369-111">其表示方式取決於連結標籤的外觀相關屬性。</span><span class="sxs-lookup"><span data-stu-id="53369-111">How it is indicated depends on the appearance-related properties of the link label.</span></span> <span data-ttu-id="53369-112">此 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> 值以 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> 包含兩個數字的物件、起始字元位置和字元數來表示。</span><span class="sxs-lookup"><span data-stu-id="53369-112">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> value is represented by a <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> object containing two numbers, the starting character position and the number of characters.</span></span> <span data-ttu-id="53369-113"><xref:System.Windows.Forms.LinkLabel.LinkArea%2A>屬性可以在屬性視窗或程式碼中，以類似下列的方式設定：</span><span class="sxs-lookup"><span data-stu-id="53369-113">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property can be set in the Properties window or in code in a manner similar to the following:</span></span>

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

3. <span data-ttu-id="53369-114">在 <xref:System.Windows.Forms.LinkLabel.LinkClicked> 事件處理常式中，叫用 <xref:System.Windows.Forms.Form.Show%2A> 方法以在專案中開啟另一個表單，並將 <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> 屬性設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="53369-114">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, invoke the <xref:System.Windows.Forms.Form.Show%2A> method to open another form in the project, and set the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="53369-115">類別的實例 <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> 會攜帶已按下之控制項的參考 <xref:System.Windows.Forms.LinkLabel> ，因此不需要轉換 `sender` 物件。</span><span class="sxs-lookup"><span data-stu-id="53369-115">An instance of the <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> class carries a reference to the <xref:System.Windows.Forms.LinkLabel> control that was clicked, so there is no need to cast the `sender` object.</span></span>

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

## <a name="linking-to-a-web-page"></a><span data-ttu-id="53369-116">連結至網頁</span><span class="sxs-lookup"><span data-stu-id="53369-116">Linking to a Web Page</span></span>

<span data-ttu-id="53369-117"><xref:System.Windows.Forms.LinkLabel>控制項也可以用來顯示具有預設瀏覽器的網頁。</span><span class="sxs-lookup"><span data-stu-id="53369-117">The <xref:System.Windows.Forms.LinkLabel> control can also be used to display a Web page with the default browser.</span></span>

#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a><span data-ttu-id="53369-118">啟動 Internet Explorer 並連結至具有 LinkLabel 控制項的網頁</span><span class="sxs-lookup"><span data-stu-id="53369-118">To start Internet Explorer and link to a Web page with a LinkLabel control</span></span>

1. <span data-ttu-id="53369-119">將 <xref:System.Windows.Forms.LinkLabel.Text%2A> 屬性設定為適當的標題。</span><span class="sxs-lookup"><span data-stu-id="53369-119">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>

2. <span data-ttu-id="53369-120">設定 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> 屬性，以決定要將哪一部分的標題指定為連結。</span><span class="sxs-lookup"><span data-stu-id="53369-120">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span>

3. <span data-ttu-id="53369-121">在 <xref:System.Windows.Forms.LinkLabel.LinkClicked> 事件處理常式中，在例外狀況處理區塊的過程中呼叫第二個程式，將 <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> 屬性設定為 `true` ，並使用 <xref:System.Diagnostics.Process.Start%2A> 方法來啟動具有 URL 的預設瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="53369-121">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, in the midst of an exception-handling block, call a second procedure that sets the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true` and uses the <xref:System.Diagnostics.Process.Start%2A> method to start the default browser with a URL.</span></span> <span data-ttu-id="53369-122">若要使用 <xref:System.Diagnostics.Process.Start%2A> 方法，您必須加入命名空間的參考 <xref:System.Diagnostics?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="53369-122">To use the <xref:System.Diagnostics.Process.Start%2A> method you need to add a reference to the <xref:System.Diagnostics?displayProperty=nameWithType> namespace.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="53369-123">如果下列程式碼是在部分信任環境中執行（例如在共用磁片磁碟機上），則在呼叫方法時，JIT 編譯程式會失敗 `VisitLink` 。</span><span class="sxs-lookup"><span data-stu-id="53369-123">If the code below is run in a partial-trust environment (such as on a shared drive), the JIT compiler fails when the `VisitLink` method is called.</span></span> <span data-ttu-id="53369-124">`System.Diagnostics.Process.Start`語句會導致連結要求失敗。</span><span class="sxs-lookup"><span data-stu-id="53369-124">The `System.Diagnostics.Process.Start` statement causes a link demand that fails.</span></span> <span data-ttu-id="53369-125">藉由在呼叫方法時攔截例外狀況 `VisitLink` ，下列程式碼可確保如果 JIT 編譯程式失敗，則會正常處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="53369-125">By catching the exception when the `VisitLink` method is called, the code below ensures that if the JIT compiler fails, the error is handled gracefully.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="53369-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53369-126">See also</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- [<span data-ttu-id="53369-127">LinkLabel 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="53369-127">LinkLabel Control Overview</span></span>](linklabel-control-overview-windows-forms.md)
- [<span data-ttu-id="53369-128">操作說明：變更 Windows Forms LinkLabel 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="53369-128">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
- [<span data-ttu-id="53369-129">LinkLabel 控制項</span><span class="sxs-lookup"><span data-stu-id="53369-129">LinkLabel Control</span></span>](linklabel-control-windows-forms.md)

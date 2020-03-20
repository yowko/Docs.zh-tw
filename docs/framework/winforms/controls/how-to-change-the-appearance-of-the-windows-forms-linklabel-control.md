---
title: 更改連結標籤控制項的外觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- LinkLabel properties
- LinkLabel control [Windows Forms], changing appearance of links
- links [Windows Forms], changing appearance
- examples [Windows Forms], LinkLabel control
- LinkLabel control [Windows Forms], examples
ms.assetid: fdc5854f-5162-4457-8cbe-1042feb2d132
ms.openlocfilehash: df66991289373a05fc7c27b7768a96643e3bbae0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142126"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a><span data-ttu-id="21f85-102">如何：變更 Windows Form LinkLabel 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="21f85-102">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>
<span data-ttu-id="21f85-103">您可以更改<xref:System.Windows.Forms.LinkLabel>控制項顯示的文本，以適應各種用途。</span><span class="sxs-lookup"><span data-stu-id="21f85-103">You can change the text displayed by the <xref:System.Windows.Forms.LinkLabel> control to suit a variety of purposes.</span></span> <span data-ttu-id="21f85-104">例如，通常的做法是，通過將文本設置為以帶有底線的特定顏色顯示，可以向使用者指示可以按一下文本。</span><span class="sxs-lookup"><span data-stu-id="21f85-104">For example, it is common practice to indicate to the user that text can be clicked by setting the text to appear in a specific color with an underline.</span></span> <span data-ttu-id="21f85-105">使用者按一下文本後，顏色將更改為其他顏色。</span><span class="sxs-lookup"><span data-stu-id="21f85-105">After the user clicks the text, the color changes to a different color.</span></span> <span data-ttu-id="21f85-106">要控制此行為，可以設置五個不同的<xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>屬性：、 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>、<xref:System.Windows.Forms.LinkLabel.LinkColor%2A><xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>和<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="21f85-106">To control this behavior, you can set five different properties: the <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, and <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> properties.</span></span>  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a><span data-ttu-id="21f85-107">更改連結標籤控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="21f85-107">To change the appearance of a LinkLabel control</span></span>  
  
1. <span data-ttu-id="21f85-108">將<xref:System.Windows.Forms.LinkLabel.LinkColor%2A>和<xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>屬性設置為所需的顏色。</span><span class="sxs-lookup"><span data-stu-id="21f85-108">Set the <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> and <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> properties to the colors you want.</span></span>  
  
     <span data-ttu-id="21f85-109">這可以以程式設計方式或在 **"屬性"** 視窗中的設計階段完成。</span><span class="sxs-lookup"><span data-stu-id="21f85-109">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    ' You can set the color using decimal values for red, green, and blue  
    LinkLabel1.LinkColor = Color.FromArgb(0, 0, 255)  
    ' Or you can set the color using defined constants  
    LinkLabel1.VisitedLinkColor = Color.Purple  
    ```  
  
    ```csharp  
    // You can set the color using decimal values for red, green, and blue  
    linkLabel1.LinkColor = Color.FromArgb(0, 0, 255);  
    // Or you can set the color using defined constants  
    linkLabel1.VisitedLinkColor = Color.Purple;  
    ```  
  
    ```cpp  
    // You can set the color using decimal values for red, green, and blue  
    linkLabel1->LinkColor = Color::FromArgb(0, 0, 255);  
    // Or you can set the color using defined constants  
    linkLabel1->VisitedLinkColor = Color::Purple;  
    ```  
  
2. <span data-ttu-id="21f85-110">將<xref:System.Windows.Forms.LinkLabel.Text%2A>屬性設置為適當的標題。</span><span class="sxs-lookup"><span data-stu-id="21f85-110">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>  
  
     <span data-ttu-id="21f85-111">這可以以程式設計方式或在 **"屬性"** 視窗中的設計階段完成。</span><span class="sxs-lookup"><span data-stu-id="21f85-111">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3. <span data-ttu-id="21f85-112">設置屬性<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>以確定標題的哪個部分將指示為連結。</span><span class="sxs-lookup"><span data-stu-id="21f85-112">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span>  
  
     <span data-ttu-id="21f85-113">該<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>值用<xref:System.Windows.Forms.LinkArea>包含兩個數字、起始字元位置和字元數表示。</span><span class="sxs-lookup"><span data-stu-id="21f85-113">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> value is represented with a <xref:System.Windows.Forms.LinkArea> containing two numbers, the starting character position and the number of characters.</span></span> <span data-ttu-id="21f85-114">這可以以程式設計方式或在 **"屬性"** 視窗中的設計階段完成。</span><span class="sxs-lookup"><span data-stu-id="21f85-114">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4. <span data-ttu-id="21f85-115">將<xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>屬性設置為<xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>或<xref:System.Windows.Forms.LinkBehavior.HoverUnderline>。 <xref:System.Windows.Forms.LinkBehavior.NeverUnderline></span><span class="sxs-lookup"><span data-stu-id="21f85-115">Set the <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> property to <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, or <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.</span></span>  
  
     <span data-ttu-id="21f85-116">如果設置為<xref:System.Windows.Forms.LinkBehavior.HoverUnderline>，則確定<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>的標題部分僅在指標位於其上時進行底線。</span><span class="sxs-lookup"><span data-stu-id="21f85-116">If it is set to <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, the part of the caption determined by <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> will only be underlined when the pointer rests on it.</span></span>  
  
5. <span data-ttu-id="21f85-117">在事件<xref:System.Windows.Forms.LinkLabel.LinkClicked>處理常式中，將<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>屬性設置為`true`。</span><span class="sxs-lookup"><span data-stu-id="21f85-117">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, set the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="21f85-118">訪問連結後，通常的做法是以某種方式（通常按顏色）更改其外觀。</span><span class="sxs-lookup"><span data-stu-id="21f85-118">When a link has been visited, it is common practice to change its appearance in some way, usually by color.</span></span> <span data-ttu-id="21f85-119">文本將更改為<xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>屬性指定的顏色。</span><span class="sxs-lookup"><span data-stu-id="21f85-119">The text will change to the color specified by the <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> property.</span></span>  
  
    ```vb  
    Protected Sub LinkLabel1_LinkClicked (ByVal sender As Object, _  
       ByVal e As EventArgs) Handles LinkLabel1.LinkClicked  
       ' Change the color of the link text  
       ' by setting LinkVisited to True.  
       LinkLabel1.LinkVisited = True  
       ' Then do whatever other action is appropriate  
    End Sub  
    ```  
  
    ```csharp  
    protected void LinkLabel1_LinkClicked(object sender, System.EventArgs e)  
    {  
       // Change the color of the link text by setting LinkVisited
       // to True.  
       linkLabel1.LinkVisited = true;  
       // Then do whatever other action is appropriate  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void linkLabel1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)  
       {  
          // Change the color of the link text by setting LinkVisited
          // to True.  
          linkLabel1->LinkVisited = true;  
          // Then do whatever other action is appropriate  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="21f85-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21f85-120">See also</span></span>

- <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>
- [<span data-ttu-id="21f85-121">LinkLabel 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="21f85-121">LinkLabel Control Overview</span></span>](linklabel-control-overview-windows-forms.md)
- [<span data-ttu-id="21f85-122">操作說明：使用 Windows Forms LinkLabel 控制項連結至物件或網頁</span><span class="sxs-lookup"><span data-stu-id="21f85-122">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [<span data-ttu-id="21f85-123">LinkLabel 控制項</span><span class="sxs-lookup"><span data-stu-id="21f85-123">LinkLabel Control</span></span>](linklabel-control-windows-forms.md)

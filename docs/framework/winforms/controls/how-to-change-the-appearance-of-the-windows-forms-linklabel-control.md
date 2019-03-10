---
title: HOW TO：變更 Windows Forms LinkLabel 控制項的外觀
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
ms.openlocfilehash: 451faf04e3a51e7dbcb992feb3f38025894be631
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717722"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a><span data-ttu-id="698e5-102">HOW TO：變更 Windows Forms LinkLabel 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="698e5-102">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>
<span data-ttu-id="698e5-103">您可以變更所顯示的文字<xref:System.Windows.Forms.LinkLabel>控制項，以符合各種用途。</span><span class="sxs-lookup"><span data-stu-id="698e5-103">You can change the text displayed by the <xref:System.Windows.Forms.LinkLabel> control to suit a variety of purposes.</span></span> <span data-ttu-id="698e5-104">比方說，它是常見的作法是藉由設定才會出現在特定的色彩與底線的文字，可以按一下文字向使用者指示。</span><span class="sxs-lookup"><span data-stu-id="698e5-104">For example, it is common practice to indicate to the user that text can be clicked by setting the text to appear in a specific color with an underline.</span></span> <span data-ttu-id="698e5-105">使用者按一下文字之後，色彩變更為不同的色彩。</span><span class="sxs-lookup"><span data-stu-id="698e5-105">After the user clicks the text, the color changes to a different color.</span></span> <span data-ttu-id="698e5-106">若要控制此行為，您可以設定五個不同的屬性： <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>， <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>， <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>， <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>，和<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="698e5-106">To control this behavior, you can set five different properties: the <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, and <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> properties.</span></span>  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a><span data-ttu-id="698e5-107">若要變更 LinkLabel 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="698e5-107">To change the appearance of a LinkLabel control</span></span>  
  
1.  <span data-ttu-id="698e5-108">設定<xref:System.Windows.Forms.LinkLabel.LinkColor%2A>和<xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>屬性，以您想要的色彩。</span><span class="sxs-lookup"><span data-stu-id="698e5-108">Set the <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> and <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> properties to the colors you want.</span></span>  
  
     <span data-ttu-id="698e5-109">這可以是以程式設計方式或在設計階段在**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="698e5-109">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
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
  
2.  <span data-ttu-id="698e5-110">設定<xref:System.Windows.Forms.LinkLabel.Text%2A>屬性設為適當的標題。</span><span class="sxs-lookup"><span data-stu-id="698e5-110">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>  
  
     <span data-ttu-id="698e5-111">這可以是以程式設計方式或在設計階段在**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="698e5-111">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3.  <span data-ttu-id="698e5-112">設定<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>屬性來判斷哪一部分的標題會指出以連結形式。</span><span class="sxs-lookup"><span data-stu-id="698e5-112">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span>  
  
     <span data-ttu-id="698e5-113"><xref:System.Windows.Forms.LinkLabel.LinkArea%2A>值會表示與<xref:System.Windows.Forms.LinkArea>包含兩個數字，起始字元的位置和字元數。</span><span class="sxs-lookup"><span data-stu-id="698e5-113">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> value is represented with a <xref:System.Windows.Forms.LinkArea> containing two numbers, the starting character position and the number of characters.</span></span> <span data-ttu-id="698e5-114">這可以是以程式設計方式或在設計階段在**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="698e5-114">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4.  <span data-ttu-id="698e5-115">設定<xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>屬性，以<xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>， <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>，或<xref:System.Windows.Forms.LinkBehavior.NeverUnderline>。</span><span class="sxs-lookup"><span data-stu-id="698e5-115">Set the <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> property to <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, or <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.</span></span>  
  
     <span data-ttu-id="698e5-116">如果設定為<xref:System.Windows.Forms.LinkBehavior.HoverUnderline>，取決於標題一部分<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>將只會加上底線指標停留在其上時。</span><span class="sxs-lookup"><span data-stu-id="698e5-116">If it is set to <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, the part of the caption determined by <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> will only be underlined when the pointer rests on it.</span></span>  
  
5.  <span data-ttu-id="698e5-117">在 <xref:System.Windows.Forms.LinkLabel.LinkClicked>事件處理常式中，設定<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="698e5-117">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, set the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="698e5-118">瀏覽過的連結，它是常見的做法，來變更以某種方式，其外觀通常色彩。</span><span class="sxs-lookup"><span data-stu-id="698e5-118">When a link has been visited, it is common practice to change its appearance in some way, usually by color.</span></span> <span data-ttu-id="698e5-119">文字會變更為所指定的色彩<xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="698e5-119">The text will change to the color specified by the <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> property.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="698e5-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="698e5-120">See also</span></span>
- <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>
- [<span data-ttu-id="698e5-121">LinkLabel 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="698e5-121">LinkLabel Control Overview</span></span>](linklabel-control-overview-windows-forms.md)
- [<span data-ttu-id="698e5-122">如何：連結的物件，或使用 Windows Forms LinkLabel 控制項的網頁</span><span class="sxs-lookup"><span data-stu-id="698e5-122">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [<span data-ttu-id="698e5-123">LinkLabel 控制項</span><span class="sxs-lookup"><span data-stu-id="698e5-123">LinkLabel Control</span></span>](linklabel-control-windows-forms.md)

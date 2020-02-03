---
title: 變更 LinkLabel 控制項的外觀
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
ms.openlocfilehash: 0b38722fb1647ea215c3bb8978dd3f54b300a0e0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746627"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a>如何：變更 Windows Form LinkLabel 控制項的外觀
您可以變更 <xref:System.Windows.Forms.LinkLabel> 控制項所顯示的文字，以符合各種用途。 例如，一般做法是將文字設定為以具有底線的特定色彩顯示，以向使用者指出可以按一下文字。 使用者按一下文字之後，色彩會變更為不同的色彩。 若要控制這個行為，您可以設定五個不同的屬性： <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>、<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>、<xref:System.Windows.Forms.LinkLabel.LinkColor%2A>、<xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>和 <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> 屬性。  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a>變更 LinkLabel 控制項的外觀  
  
1. 將 [<xref:System.Windows.Forms.LinkLabel.LinkColor%2A>] 和 [<xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> 屬性] 設定為您想要的色彩。  
  
     這可以透過程式設計方式或在 [**屬性**] 視窗的設計階段來完成。  
  
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
  
2. 將 [<xref:System.Windows.Forms.LinkLabel.Text%2A>] 屬性設定為適當的標題。  
  
     這可以透過程式設計方式或在 [**屬性**] 視窗的設計階段來完成。  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3. 設定 [<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>] 屬性，以決定要將哪一部分的標題指定為連結。  
  
     <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> 值會以包含兩個數字的 <xref:System.Windows.Forms.LinkArea> （起始字元位置和字元數）來表示。 這可以透過程式設計方式或在 [**屬性**] 視窗的設計階段來完成。  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4. 將 [<xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>] 屬性設定為 [<xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>]、[<xref:System.Windows.Forms.LinkBehavior.HoverUnderline>] 或 [<xref:System.Windows.Forms.LinkBehavior.NeverUnderline>]。  
  
     如果設定為 [<xref:System.Windows.Forms.LinkBehavior.HoverUnderline>]，由 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> 決定的標題部分只有在指標停留在其上時才會加上底線。  
  
5. 在 <xref:System.Windows.Forms.LinkLabel.LinkClicked> 事件處理常式中，將 <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> 屬性設定為 [`true`]。  
  
     流覽過連結時，通常會以某種方式變更其外觀，通常是以色彩顯示。 文字會變更為 [<xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>] 屬性所指定的色彩。  
  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>
- [LinkLabel 控制項概觀](linklabel-control-overview-windows-forms.md)
- [操作說明：使用 Windows Forms LinkLabel 控制項連結至物件或網頁](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [LinkLabel 控制項](linklabel-control-windows-forms.md)

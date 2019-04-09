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
ms.openlocfilehash: be2f6e8e10d9f9b23b4f57fa696f1fb88c4726c0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105023"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a>HOW TO：變更 Windows Forms LinkLabel 控制項的外觀
您可以變更所顯示的文字<xref:System.Windows.Forms.LinkLabel>控制項，以符合各種用途。 比方說，它是常見的作法是藉由設定才會出現在特定的色彩與底線的文字，可以按一下文字向使用者指示。 使用者按一下文字之後，色彩變更為不同的色彩。 若要控制此行為，您可以設定五個不同的屬性： <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>， <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>， <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>， <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>，和<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>屬性。  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a>若要變更 LinkLabel 控制項的外觀  
  
1.  設定<xref:System.Windows.Forms.LinkLabel.LinkColor%2A>和<xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>屬性，以您想要的色彩。  
  
     這可以是以程式設計方式或在設計階段在**屬性**視窗。  
  
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
  
2.  設定<xref:System.Windows.Forms.LinkLabel.Text%2A>屬性設為適當的標題。  
  
     這可以是以程式設計方式或在設計階段在**屬性**視窗。  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3.  設定<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>屬性來判斷哪一部分的標題會指出以連結形式。  
  
     <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>值會表示與<xref:System.Windows.Forms.LinkArea>包含兩個數字，起始字元的位置和字元數。 這可以是以程式設計方式或在設計階段在**屬性**視窗。  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4.  設定<xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>屬性，以<xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>， <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>，或<xref:System.Windows.Forms.LinkBehavior.NeverUnderline>。  
  
     如果設定為<xref:System.Windows.Forms.LinkBehavior.HoverUnderline>，取決於標題一部分<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>將只會加上底線指標停留在其上時。  
  
5.  在 <xref:System.Windows.Forms.LinkLabel.LinkClicked>事件處理常式中，設定<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>屬性設`true`。  
  
     瀏覽過的連結，它是常見的做法，來變更以某種方式，其外觀通常色彩。 文字會變更為所指定的色彩<xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>屬性。  
  
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
- [HOW TO：使用 Windows Forms LinkLabel 控制項連結至物件或網頁](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [LinkLabel 控制項](linklabel-control-windows-forms.md)

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
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a>如何：變更 Windows Form LinkLabel 控制項的外觀
您可以更改<xref:System.Windows.Forms.LinkLabel>控制項顯示的文本，以適應各種用途。 例如，通常的做法是，通過將文本設置為以帶有底線的特定顏色顯示，可以向使用者指示可以按一下文本。 使用者按一下文本後，顏色將更改為其他顏色。 要控制此行為，可以設置五個不同的<xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>屬性：、 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>、<xref:System.Windows.Forms.LinkLabel.LinkColor%2A><xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>和<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>屬性。  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a>更改連結標籤控制項的外觀  
  
1. 將<xref:System.Windows.Forms.LinkLabel.LinkColor%2A>和<xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>屬性設置為所需的顏色。  
  
     這可以以程式設計方式或在 **"屬性"** 視窗中的設計階段完成。  
  
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
  
2. 將<xref:System.Windows.Forms.LinkLabel.Text%2A>屬性設置為適當的標題。  
  
     這可以以程式設計方式或在 **"屬性"** 視窗中的設計階段完成。  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3. 設置屬性<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>以確定標題的哪個部分將指示為連結。  
  
     該<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>值用<xref:System.Windows.Forms.LinkArea>包含兩個數字、起始字元位置和字元數表示。 這可以以程式設計方式或在 **"屬性"** 視窗中的設計階段完成。  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4. 將<xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>屬性設置為<xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>或<xref:System.Windows.Forms.LinkBehavior.HoverUnderline>。 <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>  
  
     如果設置為<xref:System.Windows.Forms.LinkBehavior.HoverUnderline>，則確定<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>的標題部分僅在指標位於其上時進行底線。  
  
5. 在事件<xref:System.Windows.Forms.LinkLabel.LinkClicked>處理常式中，將<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>屬性設置為`true`。  
  
     訪問連結後，通常的做法是以某種方式（通常按顏色）更改其外觀。 文本將更改為<xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>屬性指定的顏色。  
  
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

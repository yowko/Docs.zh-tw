---
title: "如何：變更 Windows Form LinkLabel 控制項的外觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "範例 [Windows Form], LinkLabel 控制項"
  - "LinkLabel 控制項 [Windows Form], 變更連結外觀"
  - "LinkLabel 控制項 [Windows Form], 範例"
  - "LinkLabel 屬性"
  - "連結, 變更外觀"
ms.assetid: fdc5854f-5162-4457-8cbe-1042feb2d132
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：變更 Windows Form LinkLabel 控制項的外觀
您可變更 <xref:System.Windows.Forms.LinkLabel> 控制項顯示的文字，以配合各種用途的需求。  例如，通常您可將文字設定為以特定色彩與底線顯示，以向使用者表示可以按選該文字。  在使用者按一下文字之後，會變更為不同的色彩。  若要控制這個行為，您可以設定五種屬性：<xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>、<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>、<xref:System.Windows.Forms.LinkLabel.LinkColor%2A>、<xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> 和 <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> 屬性。  
  
### 若要變更 LinkLabel 控制項的外觀  
  
1.  將 <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> 和 <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> 屬性設定為想要的色彩。  
  
     可以利用程式設計方式或在設計階段使用 \[**屬性**\] 視窗完成這項工作。  
  
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
  
2.  將 <xref:System.Windows.Forms.LinkLabel.Text%2A> 屬性設定為適當的標題。  
  
     可以利用程式設計方式或在設計階段使用 \[**屬性**\] 視窗完成這項工作。  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3.  設定 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> 屬性，決定標題的哪個部分會表示為連結。  
  
     <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> 值是以包含兩個數字、開始字元位置和字元數目的 <xref:System.Windows.Forms.LinkArea> 所代表。  可以利用程式設計方式或在設計階段使用 \[**屬性**\] 視窗完成這項工作。  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4.  將 <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> 屬性設定為 <xref:System.Windows.Forms.LinkBehavior>、<xref:System.Windows.Forms.LinkBehavior> 或 <xref:System.Windows.Forms.LinkBehavior>。  
  
     若將它設定為 <xref:System.Windows.Forms.LinkBehavior>，則由 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> 決定的標題部分只會在指標指向它時才加上底線。  
  
5.  在 <xref:System.Windows.Forms.LinkLabel.LinkClicked> 事件處理常式中，將 <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> 屬性設定成 `true`。  
  
     已瀏覽過的連結通常會以某種方式變更其外觀，通常是變更色彩。  此文字色彩將會變更為 <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> 屬性所指定的色彩。  
  
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
  
## 請參閱  
 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>   
 <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>   
 <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>   
 <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>   
 [LinkLabel 控制項概觀](../../../../docs/framework/winforms/controls/linklabel-control-overview-windows-forms.md)   
 [如何：使用 Windows Form LinkLabel 控制項連結至物件或 Web 網頁](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)   
 [LinkLabel 控制項](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)
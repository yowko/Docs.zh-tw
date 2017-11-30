---
title: "如何：使用 Windows Form LinkLabel 控制項連結至物件或 Web 網頁"
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
- examples [Windows Forms], LinkLabel control
- Windows Forms, linking to objects
- Web page link control
- linking [Windows Forms], to other forms
- Windows Forms, linking to Web pages
- links [Windows Forms], to other forms
- LinkLabel control [Windows Forms], linking to object or Web page
- LinkLabel control [Windows Forms], examples
ms.assetid: 6c91c975-3cb7-4504-82f0-fc6255f8fb85
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 04566d96fe9031821b904df3bf9ec93244b62cfe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a>如何：使用 Windows Form LinkLabel 控制項連結至物件或 Web 網頁
Windows Form<xref:System.Windows.Forms.LinkLabel>控制項可讓您在表單上建立 Web 樣式連結。 按一下連結時，您可以變更其色彩會以指出瀏覽的連結。 如需有關如何變更色彩的詳細資訊，請參閱[如何： 變更 Windows Form LinkLabel 控制項的外觀](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)。  
  
## <a name="linking-to-another-form"></a>連結至另一個表單  
  
#### <a name="to-link-to-another-form-with-a-linklabel-control"></a>若要連結至另一種形式與 LinkLabel 控制項  
  
1.  設定<xref:System.Windows.Forms.LinkLabel.Text%2A>屬性設為適當的標題。  
  
2.  設定<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>屬性來判斷哪一個部分的標題會指出以連結形式。 指示它的方式取決於連結標籤與外觀相關屬性。 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>值由<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>物件，其中包含兩個數字，起始字元位置的字元數。 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>可以設定屬性，在 [屬性] 視窗中或在程式碼類似下列的方式：  
  
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
  
3.  在<xref:System.Windows.Forms.LinkLabel.LinkClicked>事件處理常式，叫用<xref:System.Windows.Forms.Form.Show%2A>方法在專案中，開啟另一個表單，並設定<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>屬性`true`。  
  
    > [!NOTE]
    >  執行個體<xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs>類別具有其參照<xref:System.Windows.Forms.LinkLabel>已按下控制項，因此不需要轉換`sender`物件。  
  
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
  
## <a name="linking-to-a-web-page"></a>連結至 Web 網頁  
 <xref:System.Windows.Forms.LinkLabel>控制項也可用來顯示預設的瀏覽器的網頁。  
  
#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a>若要啟動 Internet Explorer 和網頁的連結與 LinkLabel 控制項  
  
1.  設定<xref:System.Windows.Forms.LinkLabel.Text%2A>屬性設為適當的標題。  
  
2.  設定<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>屬性來判斷哪一個部分的標題會指出以連結形式。  
  
3.  在<xref:System.Windows.Forms.LinkLabel.LinkClicked>之中例外狀況處理區塊中，事件處理常式，呼叫第二個程序，以設定<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>屬性`true`，並使用<xref:System.Diagnostics.Process.Start%2A>方法以 URL 啟動預設瀏覽器。 若要使用<xref:System.Diagnostics.Process.Start%2A>方法，您需要將參考加入<xref:System.Diagnostics?displayProperty=nameWithType>命名空間。  
  
    > [!IMPORTANT]
    >  如果在部分信任環境中執行下列程式碼 (例如共用的磁碟機上)，JIT 編譯器失敗時`VisitLink`方法呼叫。 `System.Diagnostics.Process.Start`陳述式會導致失敗的連結要求。 藉由捕捉例外狀況時`VisitLink`呼叫方法時，下列程式碼可確保，如果 JIT 編譯器失敗，錯誤處理是依正常程序。  
  
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
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>  
 [LinkLabel 控制項概觀](../../../../docs/framework/winforms/controls/linklabel-control-overview-windows-forms.md)  
 [操作說明：變更 Windows Forms LinkLabel 控制項的外觀](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)  
 [LinkLabel 控制項](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)

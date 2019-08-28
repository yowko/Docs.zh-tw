---
title: 作法：使用 Windows Forms LinkLabel 控制項連結至物件或網頁
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
ms.openlocfilehash: cd9c53527429dfc3e7156c4023b52509452b96cd
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046244"
---
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a>作法：使用 Windows Forms LinkLabel 控制項連結至物件或網頁

Windows Forms <xref:System.Windows.Forms.LinkLabel>控制項可讓您在表單上建立 Web 樣式連結。 按一下連結時, 您可以變更其色彩, 以表示已流覽過該連結。 如需變更色彩的詳細資訊, 請[參閱如何:變更 Windows Forms LinkLabel 控制項](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)的外觀。

## <a name="linking-to-another-form"></a>連結至另一個表單

#### <a name="to-link-to-another-form-with-a-linklabel-control"></a>若要使用 LinkLabel 控制項連結至另一個表單

1. <xref:System.Windows.Forms.LinkLabel.Text%2A>將屬性設定為適當的標題。

2. <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>設定屬性, 以決定要將哪一部分的標題指定為連結。 其表示方式取決於連結標籤的外觀相關屬性。 此<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>值以包含兩個<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>數位的物件、起始字元位置和字元數來表示。 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>屬性可以在屬性視窗或程式碼中, 以類似下列的方式設定:

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

3. 在事件處理常式中, <xref:System.Windows.Forms.Form.Show%2A>叫用方法以在<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>專案中開啟另一個表單, 並將屬性設定為。 `true` <xref:System.Windows.Forms.LinkLabel.LinkClicked>

    > [!NOTE]
    > <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs>類別的實例會攜帶已按<xref:System.Windows.Forms.LinkLabel>下之控制項的參考, 因此不需要轉換`sender`物件。

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

## <a name="linking-to-a-web-page"></a>連結至網頁

<xref:System.Windows.Forms.LinkLabel>控制項也可以用來顯示具有預設瀏覽器的網頁。

#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a>啟動 Internet Explorer 並連結至具有 LinkLabel 控制項的網頁

1. <xref:System.Windows.Forms.LinkLabel.Text%2A>將屬性設定為適當的標題。

2. <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>設定屬性, 以決定要將哪一部分的標題指定為連結。

3. 在事件處理常式中, 在例外狀況處理區塊的過程中呼叫第二個程式, <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>將<xref:System.Diagnostics.Process.Start%2A>屬性設定為`true` , 並使用方法來啟動具有 URL 的預設瀏覽器。 <xref:System.Windows.Forms.LinkLabel.LinkClicked> 若要使用<xref:System.Diagnostics.Process.Start%2A>方法, 您必須加入<xref:System.Diagnostics?displayProperty=nameWithType>命名空間的參考。

    > [!IMPORTANT]
    > 如果下列程式碼是在部分信任環境中執行 (例如在共用磁片磁碟機上), 則在呼叫`VisitLink`方法時, JIT 編譯程式會失敗。 `System.Diagnostics.Process.Start`語句會導致連結要求失敗。 藉由在呼叫`VisitLink`方法時攔截例外狀況, 下列程式碼可確保如果 JIT 編譯程式失敗, 則會正常處理錯誤。

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

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- [LinkLabel 控制項概觀](linklabel-control-overview-windows-forms.md)
- [如何：變更 Windows Forms LinkLabel 控制項的外觀](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
- [LinkLabel 控制項](linklabel-control-windows-forms.md)

---
title: 作法：定義工具列按鈕的圖示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- buttons [Windows Forms], icons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: 84db98b4-8566-49ce-b2c8-1fd66a5eb3a0
ms.openlocfilehash: 2b85f734a5f8b31531cfe48f87681d98304db09b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929635"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button"></a>作法：定義工具列按鈕的圖示
> [!NOTE]
> <xref:System.Windows.Forms.ToolStrip> 控制項會取代 <xref:System.Windows.Forms.ToolBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ToolBar> 控制項，以提供回溯相容性及未來使用。  
  
 <xref:System.Windows.Forms.ToolBar>按鈕可以在其中顯示圖示, 供使用者輕鬆識別。 這可以透過將影像加入至[ImageList 元件](imagelist-component-windows-forms.md)元件, 然後將<xref:System.Windows.Forms.ImageList>元件與<xref:System.Windows.Forms.ToolBar>控制項建立關聯來達成。  
  
### <a name="to-set-an-icon-for-a-toolbar-button-programmatically"></a>以程式設計方式設定工具列按鈕的圖示  
  
1. 在程式中, 將<xref:System.Windows.Forms.ImageList>元件<xref:System.Windows.Forms.ToolBar>和控制項具現化。  
  
2. 在相同的程式中, 將影像指派給<xref:System.Windows.Forms.ImageList>元件。  
  
3. 在相同的程式中, 將<xref:System.Windows.Forms.ImageList>控制項指派<xref:System.Windows.Forms.ToolBar>給控制項, 並指派<xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A>個別工具列按鈕的屬性。  
  
     在下列程式碼範例中, 為影像位置設定的路徑是 [我的**文檔**] 資料夾。 這是因為您可以假設大部分執行 Windows 作業系統的電腦都包含此目錄。 也可讓具備最小系統存取層級的使用者安全地執行應用程式。 下列範例假設已加入<xref:System.Windows.Forms.PictureBox>控制項的表單。  
  
     遵循上述步驟, 您應該已撰寫如下所示的程式碼。  
  
    ```vb  
    Public Sub InitializeMyToolBar()  
    ' Instantiate an ImageList component and a ToolBar control.  
       Dim ToolBar1 as New ToolBar  
       Dim ImageList1 as New ImageList  
    ' Assign an image to the ImageList component.  
    ' You should replace the bold image  
    ' in the sample below with an icon of your own choosing.  
       Dim myImage As System.Drawing.Image = _   
          Image.FromFile Image.FromFile _  
          (System.Environment.GetFolderPath _  
          (System.Environment.SpecialFolder.Personal) _  
          & "\Image.gif")  
       ImageList1.Images.Add(myImage)  
    ' Create a ToolBarButton.  
       Dim ToolBarButton1 As New ToolBarButton()  
    ' Add the ToolBarButton to the ToolBar.  
       ToolBar1.Buttons.Add(toolBarButton1)  
    ' Assign an ImageList to the ToolBar.  
       ToolBar1.ImageList = ImageList1  
    ' Assign the ImageIndex property of the ToolBarButton.  
       ToolBarButton1.ImageIndex = 0  
    End Sub  
    ```  
  
    ```csharp  
    public void InitializeMyToolBar()  
    {  
       // Instantiate an ImageList component and a ToolBar control.  
       ToolBar toolBar1 = new  ToolBar();   
       ImageList imageList1 = new ImageList();  
       // Assign an image to the ImageList component.  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       Image myImage = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
       imageList1.Images.Add(myImage);  
       // Create a ToolBarButton.  
       ToolBarButton toolBarButton1 = new ToolBarButton();  
       // Add the ToolBarButton to the ToolBar.  
       toolBar1.Buttons.Add(toolBarButton1);  
       // Assign an ImageList to the ToolBar.  
       toolBar1.ImageList = imageList1;  
       // Assign ImageIndex property of the ToolBarButton.  
       toolBarButton1.ImageIndex = 0;  
    }  
    ```  
  
    ```cpp  
    public:  
       void InitializeMyToolBar()  
       {  
          // Instantiate an ImageList component and a ToolBar control.  
          ToolBar ^ toolBar1 = gcnew  ToolBar();   
          ImageList ^ imageList1 = gcnew ImageList();  
          // Assign an image to the ImageList component.  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          Image ^ myImage = Image::FromFile(String::Concat  
             (System::Environment::GetFolderPath  
             (System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
          imageList1->Images->Add(myImage);  
          // Create a ToolBarButton.  
          ToolBarButton ^ toolBarButton1 = gcnew ToolBarButton();  
          // Add the ToolBarButton to the ToolBar.  
          toolBar1->Buttons->Add(toolBarButton1);  
          // Assign an ImageList to the ToolBar.  
          toolBar1->ImageList = imageList1;  
          // Assign ImageIndex property of the ToolBarButton.  
          toolBarButton1->ImageIndex = 0;  
       }  
    ```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ToolBar>
- [如何：觸發工具列按鈕的功能表事件](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [ToolBar 控制項](toolbar-control-windows-forms.md)
- [ImageList 元件](imagelist-component-windows-forms.md)

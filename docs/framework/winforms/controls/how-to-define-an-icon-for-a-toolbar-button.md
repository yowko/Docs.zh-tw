---
title: "如何：定義工具列按鈕的圖示 | Microsoft Docs"
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
  - "按鈕 [Windows Form], 圖示"
  - "範例 [Windows Form], 工具列"
  - "圖示 [Windows Form], 工具列按鈕"
  - "影像 [Windows Form], 工具列按鈕"
  - "ToolBar 控制項 [Windows Form], 將圖示加入至按鈕"
  - "工具列 [Windows Form], 將圖示加入至按鈕"
ms.assetid: 84db98b4-8566-49ce-b2c8-1fd66a5eb3a0
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：定義工具列按鈕的圖示
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> 控制項會取代 <xref:System.Windows.Forms.ToolBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ToolBar> 控制項，以提供回溯相容性及未來使用。  
  
 <xref:System.Windows.Forms.ToolBar> 按鈕可以在按鈕中顯示圖示，方便使用者識別。  這項功能是經由將影像加入至 [ImageList 元件](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) 元件，然後讓 <xref:System.Windows.Forms.ImageList> 元件與 <xref:System.Windows.Forms.ToolBar> 控制項產生關聯而達成的。  
  
### 若要以程式設計方式設定工具列按鈕的圖示  
  
1.  在程序中，產生 <xref:System.Windows.Forms.ImageList> 元件和 <xref:System.Windows.Forms.ToolBar> 控制項。  
  
2.  在同樣的程序中，將影像指派給 <xref:System.Windows.Forms.ImageList> 元件。  
  
3.  在同樣的程序中，將 <xref:System.Windows.Forms.ImageList> 控制項指派給 <xref:System.Windows.Forms.ToolBar> 控制項，並指派個別工具列按鈕的 <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> 屬性。  
  
     在下列程式碼範例中，影像的位置路徑設定為 \[**我的文件**\] 資料夾。  這是可以做到的，因為您可假設大部分執行 Windows 作業系統的電腦都會包含這個目錄。  這也可讓使用者以最基本的系統存取層級，便可安全執行應用程式。  下列範例假設已將 <xref:System.Windows.Forms.PictureBox> 控制項加入表單。  
  
     依照上述步驟，您的程式碼應像下面這樣。  
  
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
  
## 請參閱  
 <xref:System.Windows.Forms.ToolBar>   
 [如何：觸發工具列按鈕的功能表事件](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)   
 [ToolBar 控制項](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)   
 [ImageList 元件](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
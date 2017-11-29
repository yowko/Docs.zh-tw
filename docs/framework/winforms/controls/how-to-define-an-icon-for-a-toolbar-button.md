---
title: "如何：定義工具列按鈕的圖示"
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
- toolbars [Windows Forms], adding icons to buttons
- buttons [Windows Forms], icons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: 84db98b4-8566-49ce-b2c8-1fd66a5eb3a0
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1d9f1dc73e6a74d8d69fedf6650102b77bd4f96a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-an-icon-for-a-toolbar-button"></a><span data-ttu-id="a9d04-102">如何：定義工具列按鈕的圖示</span><span class="sxs-lookup"><span data-stu-id="a9d04-102">How to: Define an Icon for a ToolBar Button</span></span>
> [!NOTE]
>  <span data-ttu-id="a9d04-103"><xref:System.Windows.Forms.ToolStrip> 控制項會取代 <xref:System.Windows.Forms.ToolBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ToolBar> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="a9d04-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="a9d04-104"><xref:System.Windows.Forms.ToolBar>按鈕就能夠顯示圖示在其中為了易於識別的使用者。</span><span class="sxs-lookup"><span data-stu-id="a9d04-104"><xref:System.Windows.Forms.ToolBar> buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="a9d04-105">這透過將影像加入至達成[ImageList 元件](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)元件，然後將相關聯<xref:System.Windows.Forms.ImageList>元件<xref:System.Windows.Forms.ToolBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="a9d04-105">This is achieved through adding images to the [ImageList Component](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) component and then associating the <xref:System.Windows.Forms.ImageList> component with the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
### <a name="to-set-an-icon-for-a-toolbar-button-programmatically"></a><span data-ttu-id="a9d04-106">以程式設計方式設定工具列按鈕的圖示</span><span class="sxs-lookup"><span data-stu-id="a9d04-106">To set an icon for a toolbar button programmatically</span></span>  
  
1.  <span data-ttu-id="a9d04-107">在程序，具現化<xref:System.Windows.Forms.ImageList>元件和<xref:System.Windows.Forms.ToolBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="a9d04-107">In a procedure, instantiate an <xref:System.Windows.Forms.ImageList> component and a <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
2.  <span data-ttu-id="a9d04-108">在相同的程序，將指派到映像<xref:System.Windows.Forms.ImageList>元件。</span><span class="sxs-lookup"><span data-stu-id="a9d04-108">In the same procedure, assign an image to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
3.  <span data-ttu-id="a9d04-109">在相同的程序中，指派<xref:System.Windows.Forms.ImageList>控制權傳輸至<xref:System.Windows.Forms.ToolBar>控制，並指派<xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A>個別工具列按鈕的屬性。</span><span class="sxs-lookup"><span data-stu-id="a9d04-109">In the same procedure, assign the <xref:System.Windows.Forms.ImageList> control to the <xref:System.Windows.Forms.ToolBar> control and assign the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of the individual toolbar buttons.</span></span>  
  
     <span data-ttu-id="a9d04-110">在下列程式碼範例中，設定路徑的映像的位置是**我的文件**資料夾。</span><span class="sxs-lookup"><span data-stu-id="a9d04-110">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="a9d04-111">這麼做，因為您可以假設大部分執行 Windows 作業系統的電腦將會包含此目錄。</span><span class="sxs-lookup"><span data-stu-id="a9d04-111">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="a9d04-112">也可讓具備最小系統存取層級的使用者安全地執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a9d04-112">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="a9d04-113">以下範例假設的表單具有<xref:System.Windows.Forms.PictureBox>已經加入的控制項。</span><span class="sxs-lookup"><span data-stu-id="a9d04-113">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
     <span data-ttu-id="a9d04-114">依照上述步驟中，您應該撰寫類似下面顯示的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a9d04-114">Following the steps above, you should have written code similar to that displayed below.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a9d04-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9d04-115">See Also</span></span>  
 <xref:System.Windows.Forms.ToolBar>  
 [<span data-ttu-id="a9d04-116">操作說明：觸發工具列按鈕的功能表事件</span><span class="sxs-lookup"><span data-stu-id="a9d04-116">How to: Trigger Menu Events for Toolbar Buttons</span></span>](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [<span data-ttu-id="a9d04-117">ToolBar 控制項</span><span class="sxs-lookup"><span data-stu-id="a9d04-117">ToolBar Control</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)  
 [<span data-ttu-id="a9d04-118">ImageList 元件</span><span class="sxs-lookup"><span data-stu-id="a9d04-118">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)

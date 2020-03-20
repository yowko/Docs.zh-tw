---
title: 如何：定義工具列按鈕的圖示
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
ms.openlocfilehash: 84c67c7d2584390ba3e48cb83820c65c6bb45d1f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182201"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button"></a><span data-ttu-id="d5313-102">如何：定義工具列按鈕的圖示</span><span class="sxs-lookup"><span data-stu-id="d5313-102">How to: Define an Icon for a ToolBar Button</span></span>
> [!NOTE]
> <span data-ttu-id="d5313-103"><xref:System.Windows.Forms.ToolStrip> 控制項會取代 <xref:System.Windows.Forms.ToolBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ToolBar> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="d5313-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="d5313-104"><xref:System.Windows.Forms.ToolBar>按鈕能夠顯示其中的圖示，以便使用者輕鬆識別。</span><span class="sxs-lookup"><span data-stu-id="d5313-104"><xref:System.Windows.Forms.ToolBar> buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="d5313-105">這是通過向[ImageList 元件](imagelist-component-windows-forms.md)添加圖像，然後將<xref:System.Windows.Forms.ImageList>該元件與控制項相關聯來實現的。 <xref:System.Windows.Forms.ToolBar></span><span class="sxs-lookup"><span data-stu-id="d5313-105">This is achieved through adding images to the [ImageList Component](imagelist-component-windows-forms.md) component and then associating the <xref:System.Windows.Forms.ImageList> component with the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
### <a name="to-set-an-icon-for-a-toolbar-button-programmatically"></a><span data-ttu-id="d5313-106">以程式設計方式設置工具列按鈕的圖示</span><span class="sxs-lookup"><span data-stu-id="d5313-106">To set an icon for a toolbar button programmatically</span></span>  
  
1. <span data-ttu-id="d5313-107">在此過程中，具現化<xref:System.Windows.Forms.ImageList>元件和<xref:System.Windows.Forms.ToolBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="d5313-107">In a procedure, instantiate an <xref:System.Windows.Forms.ImageList> component and a <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
2. <span data-ttu-id="d5313-108">在同一過程中，為<xref:System.Windows.Forms.ImageList>元件分配映射。</span><span class="sxs-lookup"><span data-stu-id="d5313-108">In the same procedure, assign an image to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
3. <span data-ttu-id="d5313-109">在同一過程中，將<xref:System.Windows.Forms.ImageList>控制項分配給<xref:System.Windows.Forms.ToolBar>控制項並分配各個工具列按鈕<xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A>的屬性。</span><span class="sxs-lookup"><span data-stu-id="d5313-109">In the same procedure, assign the <xref:System.Windows.Forms.ImageList> control to the <xref:System.Windows.Forms.ToolBar> control and assign the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of the individual toolbar buttons.</span></span>  
  
     <span data-ttu-id="d5313-110">在下面的代碼示例中，為圖像位置設置的路徑是 **"我的文件"** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="d5313-110">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="d5313-111">此操作已完成，因為您可以假定運行 Windows 作業系統的大多數電腦都將包含此目錄。</span><span class="sxs-lookup"><span data-stu-id="d5313-111">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="d5313-112">也可讓具備最小系統存取層級的使用者安全地執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d5313-112">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="d5313-113">下面的示例假定已添加控制項的<xref:System.Windows.Forms.PictureBox>表單。</span><span class="sxs-lookup"><span data-stu-id="d5313-113">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
     <span data-ttu-id="d5313-114">按照上述步驟，您應該編寫類似于下面顯示的代碼。</span><span class="sxs-lookup"><span data-stu-id="d5313-114">Following the steps above, you should have written code similar to that displayed below.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d5313-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5313-115">See also</span></span>

- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="d5313-116">如何：觸發工具列按鈕的功能表事件</span><span class="sxs-lookup"><span data-stu-id="d5313-116">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [<span data-ttu-id="d5313-117">ToolBar 控制項</span><span class="sxs-lookup"><span data-stu-id="d5313-117">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
- [<span data-ttu-id="d5313-118">ImageList 元件</span><span class="sxs-lookup"><span data-stu-id="d5313-118">ImageList Component</span></span>](imagelist-component-windows-forms.md)

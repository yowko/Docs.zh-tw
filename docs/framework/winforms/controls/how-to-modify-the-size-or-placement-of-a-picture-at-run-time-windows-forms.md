---
title: 如何：於執行階段修改圖片的大小或位置
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], controlling placement in PictureBox control [Windows Forms]
- examples [Windows Forms], PictureBox control
- PictureBox control [Windows Forms], picture size and alignment
- pictures [Windows Forms], controlling placement in PictureBox control [Windows Forms]
ms.assetid: d0b332a3-fae2-4891-957c-dc3e17743326
ms.openlocfilehash: 9bb094ce0b7945f23a2e9b8614e56c9492d5f832
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736032"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a><span data-ttu-id="8b626-102">如何：於執行階段修改圖片的大小或位置 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="8b626-102">How to: Modify the Size or Placement of a Picture at Run Time (Windows Forms)</span></span>
<span data-ttu-id="8b626-103">如果您在表單上使用 [Windows Forms <xref:System.Windows.Forms.PictureBox>] 控制項，您可以將其上的 <xref:System.Windows.Forms.PictureBox.SizeMode%2A> 屬性設定為：</span><span class="sxs-lookup"><span data-stu-id="8b626-103">If you use the Windows Forms <xref:System.Windows.Forms.PictureBox> control on a form, you can set the <xref:System.Windows.Forms.PictureBox.SizeMode%2A> property on it to:</span></span>  
  
- <span data-ttu-id="8b626-104">將圖片的左上角對齊控制項的左上角</span><span class="sxs-lookup"><span data-stu-id="8b626-104">Align the picture's upper left corner with the control's upper left corner</span></span>  
  
- <span data-ttu-id="8b626-105">在控制項中將圖片置中</span><span class="sxs-lookup"><span data-stu-id="8b626-105">Center the picture within the control</span></span>  
  
- <span data-ttu-id="8b626-106">調整控制項的大小以符合它所顯示的圖片</span><span class="sxs-lookup"><span data-stu-id="8b626-106">Adjust the size of the control to fit the picture it displays</span></span>  
  
- <span data-ttu-id="8b626-107">延展顯示的任何圖片以符合控制項</span><span class="sxs-lookup"><span data-stu-id="8b626-107">Stretch any picture it displays to fit the control</span></span>  
  
 <span data-ttu-id="8b626-108">延展圖片（尤其是點陣圖格式的圖片）可能會導致影像品質遺失。</span><span class="sxs-lookup"><span data-stu-id="8b626-108">Stretching a picture (especially one in bitmap format) can produce a loss in image quality.</span></span> <span data-ttu-id="8b626-109">中繼檔，這是在執行時間繪製影像的圖形指示清單，較適合用來延展，而不是點陣圖。</span><span class="sxs-lookup"><span data-stu-id="8b626-109">Metafiles, which are lists of graphics instructions for drawing images at run time, are better suited for stretching than bitmaps are.</span></span>  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a><span data-ttu-id="8b626-110">若要在執行時間設定 SizeMode 屬性</span><span class="sxs-lookup"><span data-stu-id="8b626-110">To set the SizeMode property at run time</span></span>  
  
1. <span data-ttu-id="8b626-111">將 <xref:System.Windows.Forms.PictureBox.SizeMode%2A> 設定為 <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> （預設值）、<xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>、<xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>或 <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>。</span><span class="sxs-lookup"><span data-stu-id="8b626-111">Set <xref:System.Windows.Forms.PictureBox.SizeMode%2A> to <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (the default), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, or <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span></span> <span data-ttu-id="8b626-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal> 表示影像放在控制項的左上角;如果影像大於控制項，則會裁剪其較低和右邊緣。</span><span class="sxs-lookup"><span data-stu-id="8b626-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal> means that the image is placed in the control's upper-left corner; if the image is larger than the control, its lower and right edges are clipped.</span></span> <span data-ttu-id="8b626-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> 表示影像置中在控制項內;如果影像大於控制項，則會裁剪圖片的外部邊緣。</span><span class="sxs-lookup"><span data-stu-id="8b626-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> means that the image is centered within the control; if the image is larger than the control, the picture's outside edges are clipped.</span></span> <span data-ttu-id="8b626-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> 表示控制項的大小會調整為影像的大小。</span><span class="sxs-lookup"><span data-stu-id="8b626-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> means that the size of the control is adjusted to the size of the image.</span></span> <span data-ttu-id="8b626-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> 是相反的，這表示影像大小會調整為控制項的大小。</span><span class="sxs-lookup"><span data-stu-id="8b626-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> is the reverse, and means that the size of the image is adjusted to the size of the control.</span></span>  
  
     <span data-ttu-id="8b626-116">在下列範例中，為影像的位置設定的路徑是 [我的文件] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="8b626-116">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="8b626-117">這是因為您可以假設大部分執行 Windows 作業系統的電腦都包含此目錄。</span><span class="sxs-lookup"><span data-stu-id="8b626-117">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="8b626-118">也可讓具備最小系統存取層級的使用者安全地執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="8b626-118">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="8b626-119">下列範例假設已加入 <xref:System.Windows.Forms.PictureBox> 控制項的表單。</span><span class="sxs-lookup"><span data-stu-id="8b626-119">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
    ```vb  
    Private Sub StretchPic()  
       ' Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage  
       ' Load the picture into the control.  
       ' You should replace the bold image   
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void StretchPic(){  
       // Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage;  
       // Load the picture into the control.  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\Image.gif")  
    }  
    ```  
  
    ```cpp  
    private:  
       void StretchPic()  
       {  
          // Stretch the picture to fit the control.  
          pictureBox1->SizeMode = PictureBoxSizeMode::StretchImage;  
          // Load the picture into the control.  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8b626-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b626-120">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="8b626-121">操作說明：使用設計工具載入圖片</span><span class="sxs-lookup"><span data-stu-id="8b626-121">How to: Load a Picture Using the Designer</span></span>](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [<span data-ttu-id="8b626-122">PictureBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="8b626-122">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="8b626-123">操作說明：在執行階段設定圖案</span><span class="sxs-lookup"><span data-stu-id="8b626-123">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="8b626-124">PictureBox 控制項</span><span class="sxs-lookup"><span data-stu-id="8b626-124">PictureBox Control</span></span>](picturebox-control-windows-forms.md)

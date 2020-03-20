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
ms.openlocfilehash: fea813d7b9fe585e35b729b8b64e3a5f414ef76d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141962"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a><span data-ttu-id="bbcf1-102">如何：於執行階段修改圖片的大小或位置 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="bbcf1-102">How to: Modify the Size or Placement of a Picture at Run Time (Windows Forms)</span></span>
<span data-ttu-id="bbcf1-103">如果在表單上使用 Windows<xref:System.Windows.Forms.PictureBox>表單控制項，則可以將表單上<xref:System.Windows.Forms.PictureBox.SizeMode%2A>的屬性設置為：</span><span class="sxs-lookup"><span data-stu-id="bbcf1-103">If you use the Windows Forms <xref:System.Windows.Forms.PictureBox> control on a form, you can set the <xref:System.Windows.Forms.PictureBox.SizeMode%2A> property on it to:</span></span>  
  
- <span data-ttu-id="bbcf1-104">將圖片的左上角與控制項的左上角對齊</span><span class="sxs-lookup"><span data-stu-id="bbcf1-104">Align the picture's upper left corner with the control's upper left corner</span></span>  
  
- <span data-ttu-id="bbcf1-105">將圖片居中</span><span class="sxs-lookup"><span data-stu-id="bbcf1-105">Center the picture within the control</span></span>  
  
- <span data-ttu-id="bbcf1-106">調整控制項的大小以適合顯示的圖片</span><span class="sxs-lookup"><span data-stu-id="bbcf1-106">Adjust the size of the control to fit the picture it displays</span></span>  
  
- <span data-ttu-id="bbcf1-107">拉伸它顯示的任何圖片以適合控制項</span><span class="sxs-lookup"><span data-stu-id="bbcf1-107">Stretch any picture it displays to fit the control</span></span>  
  
 <span data-ttu-id="bbcf1-108">拉伸圖片（尤其是點陣圖格式）可能會損失圖像品質。</span><span class="sxs-lookup"><span data-stu-id="bbcf1-108">Stretching a picture (especially one in bitmap format) can produce a loss in image quality.</span></span> <span data-ttu-id="bbcf1-109">中繼檔是運行時繪製圖像的圖形說明清單，比點陣圖更適合拉伸。</span><span class="sxs-lookup"><span data-stu-id="bbcf1-109">Metafiles, which are lists of graphics instructions for drawing images at run time, are better suited for stretching than bitmaps are.</span></span>  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a><span data-ttu-id="bbcf1-110">在運行時設置 SizeMode 屬性</span><span class="sxs-lookup"><span data-stu-id="bbcf1-110">To set the SizeMode property at run time</span></span>  
  
1. <span data-ttu-id="bbcf1-111">設置為<xref:System.Windows.Forms.PictureBox.SizeMode%2A><xref:System.Windows.Forms.PictureBoxSizeMode.Normal>（預設值）、<xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>或<xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>。</span><span class="sxs-lookup"><span data-stu-id="bbcf1-111">Set <xref:System.Windows.Forms.PictureBox.SizeMode%2A> to <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (the default), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, or <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span></span> <span data-ttu-id="bbcf1-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal>表示圖像放置在控制項的左上角;如果圖像大於控制項，則其下邊緣和右邊緣將剪切。</span><span class="sxs-lookup"><span data-stu-id="bbcf1-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal> means that the image is placed in the control's upper-left corner; if the image is larger than the control, its lower and right edges are clipped.</span></span> <span data-ttu-id="bbcf1-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>表示圖像居中，在控制項中居中;如果圖像大於控制項，則剪切圖片的外邊緣。</span><span class="sxs-lookup"><span data-stu-id="bbcf1-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> means that the image is centered within the control; if the image is larger than the control, the picture's outside edges are clipped.</span></span> <span data-ttu-id="bbcf1-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>表示控制項的大小會調整為圖像的大小。</span><span class="sxs-lookup"><span data-stu-id="bbcf1-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> means that the size of the control is adjusted to the size of the image.</span></span> <span data-ttu-id="bbcf1-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>是相反的，表示圖像的大小會調整到控制項的大小。</span><span class="sxs-lookup"><span data-stu-id="bbcf1-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> is the reverse, and means that the size of the image is adjusted to the size of the control.</span></span>  
  
     <span data-ttu-id="bbcf1-116">在下面的示例中，為圖像位置設置的路徑是"我的文件"資料夾。</span><span class="sxs-lookup"><span data-stu-id="bbcf1-116">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="bbcf1-117">此操作已完成，因為您可以假定運行 Windows 作業系統的大多數電腦都將包含此目錄。</span><span class="sxs-lookup"><span data-stu-id="bbcf1-117">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="bbcf1-118">也可讓具備最小系統存取層級的使用者安全地執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="bbcf1-118">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="bbcf1-119">下面的示例假定已添加控制項的<xref:System.Windows.Forms.PictureBox>表單。</span><span class="sxs-lookup"><span data-stu-id="bbcf1-119">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bbcf1-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbcf1-120">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="bbcf1-121">如何：使用設計工具載入圖片</span><span class="sxs-lookup"><span data-stu-id="bbcf1-121">How to: Load a Picture Using the Designer</span></span>](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [<span data-ttu-id="bbcf1-122">PictureBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="bbcf1-122">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="bbcf1-123">操作說明：在執行階段設定圖案</span><span class="sxs-lookup"><span data-stu-id="bbcf1-123">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="bbcf1-124">PictureBox 控制項</span><span class="sxs-lookup"><span data-stu-id="bbcf1-124">PictureBox Control</span></span>](picturebox-control-windows-forms.md)

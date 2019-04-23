---
title: HOW TO：修改的大小或位置的圖片，在執行階段 (Windows Form)
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
ms.openlocfilehash: d0a86d7fe53dba3da6bd63587561f82877bc2f06
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59328331"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a><span data-ttu-id="09a86-102">HOW TO：修改的大小或位置的圖片，在執行階段 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="09a86-102">How to: Modify the Size or Placement of a Picture at Run Time (Windows Forms)</span></span>
<span data-ttu-id="09a86-103">如果您使用 Windows Form<xref:System.Windows.Forms.PictureBox>控制項在表單中，您可以設定<xref:System.Windows.Forms.PictureBox.SizeMode%2A>上它的屬性：</span><span class="sxs-lookup"><span data-stu-id="09a86-103">If you use the Windows Forms <xref:System.Windows.Forms.PictureBox> control on a form, you can set the <xref:System.Windows.Forms.PictureBox.SizeMode%2A> property on it to:</span></span>  
  
-   <span data-ttu-id="09a86-104">對齊圖片的左上的角的控制項的左上角</span><span class="sxs-lookup"><span data-stu-id="09a86-104">Align the picture's upper left corner with the control's upper left corner</span></span>  
  
-   <span data-ttu-id="09a86-105">在控制項中將圖片置中</span><span class="sxs-lookup"><span data-stu-id="09a86-105">Center the picture within the control</span></span>  
  
-   <span data-ttu-id="09a86-106">調整以符合它顯示的圖片控制項的大小</span><span class="sxs-lookup"><span data-stu-id="09a86-106">Adjust the size of the control to fit the picture it displays</span></span>  
  
-   <span data-ttu-id="09a86-107">自動縮放以符合控制項顯示的任何圖片</span><span class="sxs-lookup"><span data-stu-id="09a86-107">Stretch any picture it displays to fit the control</span></span>  
  
 <span data-ttu-id="09a86-108">自動縮放的圖片 （尤其是一個以點陣圖格式），可以產生遺失的影像品質。</span><span class="sxs-lookup"><span data-stu-id="09a86-108">Stretching a picture (especially one in bitmap format) can produce a loss in image quality.</span></span> <span data-ttu-id="09a86-109">中繼檔，也就是在執行階段繪製影像的圖形指示清單、 計較適合用來自動縮放比點陣圖。</span><span class="sxs-lookup"><span data-stu-id="09a86-109">Metafiles, which are lists of graphics instructions for drawing images at run time, are better suited for stretching than bitmaps are.</span></span>  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a><span data-ttu-id="09a86-110">若要在執行階段設定的大小模式屬性</span><span class="sxs-lookup"><span data-stu-id="09a86-110">To set the SizeMode property at run time</span></span>  
  
1. <span data-ttu-id="09a86-111">設定<xref:System.Windows.Forms.PictureBox.SizeMode%2A>要<xref:System.Windows.Forms.PictureBoxSizeMode.Normal>（預設值）， <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>， <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>，或<xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>。</span><span class="sxs-lookup"><span data-stu-id="09a86-111">Set <xref:System.Windows.Forms.PictureBox.SizeMode%2A> to <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (the default), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, or <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span></span> <span data-ttu-id="09a86-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal> 表示影像置於控制項的左上角。如果影像大於此控制項，其低和右緣被裁剪。</span><span class="sxs-lookup"><span data-stu-id="09a86-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal> means that the image is placed in the control's upper-left corner; if the image is larger than the control, its lower and right edges are clipped.</span></span> <span data-ttu-id="09a86-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> 表示影像置於控制項中，如果影像大於此控制項，則會裁剪圖片的外邊緣。</span><span class="sxs-lookup"><span data-stu-id="09a86-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> means that the image is centered within the control; if the image is larger than the control, the picture's outside edges are clipped.</span></span> <span data-ttu-id="09a86-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> 表示控制項的大小會調整為影像的大小。</span><span class="sxs-lookup"><span data-stu-id="09a86-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> means that the size of the control is adjusted to the size of the image.</span></span> <span data-ttu-id="09a86-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> 相反地，，表示影像的大小調整控制項大小的。</span><span class="sxs-lookup"><span data-stu-id="09a86-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> is the reverse, and means that the size of the image is adjusted to the size of the control.</span></span>  
  
     <span data-ttu-id="09a86-116">在下列範例中，映像的位置所設定的路徑會是 [我的文件] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="09a86-116">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="09a86-117">這麼做，因為您可以假設大部分執行 Windows 作業系統的電腦都會包含這個目錄。</span><span class="sxs-lookup"><span data-stu-id="09a86-117">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="09a86-118">也可讓具備最小系統存取層級的使用者安全地執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="09a86-118">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="09a86-119">下列範例假設表單<xref:System.Windows.Forms.PictureBox>已經加入的控制項。</span><span class="sxs-lookup"><span data-stu-id="09a86-119">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="09a86-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09a86-120">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="09a86-121">如何：使用設計工具載入圖片</span><span class="sxs-lookup"><span data-stu-id="09a86-121">How to: Load a Picture Using the Designer</span></span>](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [<span data-ttu-id="09a86-122">PictureBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="09a86-122">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="09a86-123">如何：在執行階段設定圖案</span><span class="sxs-lookup"><span data-stu-id="09a86-123">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="09a86-124">PictureBox 控制項</span><span class="sxs-lookup"><span data-stu-id="09a86-124">PictureBox Control</span></span>](picturebox-control-windows-forms.md)

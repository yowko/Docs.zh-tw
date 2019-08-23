---
title: 作法：在執行時間設定圖片 (Windows Forms)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- pictures [Windows Forms], setting display
- examples [Windows Forms], PictureBox control
- bitmaps [Windows Forms], displaying in PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding images
- images [Windows Forms], adding with PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 18ca41d0-68a5-4660-985e-a6c1fbc01d76
ms.openlocfilehash: 99d78a275c8ad8f55d9b0832a794545b65da7e20
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917533"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a><span data-ttu-id="df749-102">HOW TO：在執行時間設定圖片 (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="df749-102">How to: Set Pictures at Run Time (Windows Forms)</span></span>
<span data-ttu-id="df749-103">您可以透過程式設計方式設定 Windows Forms <xref:System.Windows.Forms.PictureBox>控制項所顯示的影像。</span><span class="sxs-lookup"><span data-stu-id="df749-103">You can programmatically set the image displayed by a Windows Forms <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-set-a-picture-programmatically"></a><span data-ttu-id="df749-104">以程式設計方式設定圖片</span><span class="sxs-lookup"><span data-stu-id="df749-104">To set a picture programmatically</span></span>  
  
- <span data-ttu-id="df749-105">使用類別的<xref:System.Windows.Forms.PictureBox.Image%2A> <xref:System.Drawing.Image>方法來設定屬性。 <xref:System.Drawing.Image.FromFile%2A></span><span class="sxs-lookup"><span data-stu-id="df749-105">Set the <xref:System.Windows.Forms.PictureBox.Image%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image> class.</span></span>  
  
     <span data-ttu-id="df749-106">在下列範例中, 為影像的位置設定的路徑是 [我的文件] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="df749-106">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="df749-107">這是因為您可以假設大部分執行 Windows 作業系統的電腦都包含此目錄。</span><span class="sxs-lookup"><span data-stu-id="df749-107">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="df749-108">也可讓具備最小系統存取層級的使用者安全地執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="df749-108">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="df749-109">下列範例假設已加入<xref:System.Windows.Forms.PictureBox>控制項的表單。</span><span class="sxs-lookup"><span data-stu-id="df749-109">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
    ```vb  
    Private Sub LoadNewPict()  
       ' You should replace the bold image   
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadNewPict(){  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    }  
    ```  
  
    ```cpp  
    private:  
       void LoadNewPict()  
       {  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
### <a name="to-clear-a-graphic"></a><span data-ttu-id="df749-110">若要清除圖形</span><span class="sxs-lookup"><span data-stu-id="df749-110">To clear a graphic</span></span>  
  
- <span data-ttu-id="df749-111">首先, 釋放影像所使用的記憶體, 然後清除圖形。</span><span class="sxs-lookup"><span data-stu-id="df749-111">First, release the memory being used by the image, and then clear the graphic.</span></span> <span data-ttu-id="df749-112">如果記憶體管理變成問題, 垃圾收集將會在稍後釋放記憶體。</span><span class="sxs-lookup"><span data-stu-id="df749-112">Garbage collection will free up the memory later if memory management becomes a problem.</span></span>  
  
    ```vb  
    If Not (PictureBox1.Image Is Nothing) Then  
       PictureBox1.Image.Dispose()  
       PictureBox1.Image = Nothing  
    End If  
    ```  
  
    ```csharp  
    if (pictureBox1.Image != null)   
    {  
       pictureBox1.Image.Dispose();  
       pictureBox1.Image = null;  
    }  
    ```  
  
    ```cpp  
    if (pictureBox1->Image != nullptr)  
    {  
       pictureBox1->Image->Dispose();  
       pictureBox1->Image = nullptr;  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="df749-113">如需有關為何應該以這種方式<xref:System.Drawing.Image.Dispose%2A>使用方法的詳細資訊, 請參閱[清除非受控資源](../../../standard/garbage-collection/unmanaged.md)。</span><span class="sxs-lookup"><span data-stu-id="df749-113">For more information on why you should use the <xref:System.Drawing.Image.Dispose%2A> method in this way, see [Cleaning Up Unmanaged Resources](../../../standard/garbage-collection/unmanaged.md).</span></span>  
  
     <span data-ttu-id="df749-114">即使在設計階段將圖形載入至控制項, 此程式碼也會清除影像。</span><span class="sxs-lookup"><span data-stu-id="df749-114">This code will clear the image even if a graphic was loaded into the control at design time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df749-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df749-115">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [<span data-ttu-id="df749-116">PictureBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="df749-116">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="df749-117">如何：使用設計工具載入圖片</span><span class="sxs-lookup"><span data-stu-id="df749-117">How to: Load a Picture Using the Designer</span></span>](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [<span data-ttu-id="df749-118">如何：在執行時間修改圖片的大小或位置</span><span class="sxs-lookup"><span data-stu-id="df749-118">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="df749-119">PictureBox 控制項</span><span class="sxs-lookup"><span data-stu-id="df749-119">PictureBox Control</span></span>](picturebox-control-windows-forms.md)

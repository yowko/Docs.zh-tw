---
title: "如何：在執行階段設定圖片 (Windows Form)"
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
- pictures [Windows Forms], setting display
- examples [Windows Forms], PictureBox control
- bitmaps [Windows Forms], displaying in PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding images
- images [Windows Forms], adding with PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 18ca41d0-68a5-4660-985e-a6c1fbc01d76
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 429c0c928d8bff4f837186040288d9447fc18687
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a><span data-ttu-id="4086f-102">如何：在執行階段設定圖片 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="4086f-102">How to: Set Pictures at Run Time (Windows Forms)</span></span>
<span data-ttu-id="4086f-103">您可以透過程式設計方式設定 Windows Form 所顯示的影像<xref:System.Windows.Forms.PictureBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="4086f-103">You can programmatically set the image displayed by a Windows Forms <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-set-a-picture-programmatically"></a><span data-ttu-id="4086f-104">以程式設計方式設定圖片</span><span class="sxs-lookup"><span data-stu-id="4086f-104">To set a picture programmatically</span></span>  
  
-   <span data-ttu-id="4086f-105">設定<xref:System.Windows.Forms.PictureBox.Image%2A>屬性使用<xref:System.Drawing.Image.FromFile%2A>方法<xref:System.Drawing.Image>類別。</span><span class="sxs-lookup"><span data-stu-id="4086f-105">Set the <xref:System.Windows.Forms.PictureBox.Image%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image> class.</span></span>  
  
     <span data-ttu-id="4086f-106">下列範例中，在映像的位置所設定的路徑會是 [我的文件] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4086f-106">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="4086f-107">這麼做，因為您可以假設大部分執行 Windows 作業系統的電腦將會包含此目錄。</span><span class="sxs-lookup"><span data-stu-id="4086f-107">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="4086f-108">也可讓具備最小系統存取層級的使用者安全地執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="4086f-108">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="4086f-109">以下範例假設的表單具有<xref:System.Windows.Forms.PictureBox>已經加入的控制項。</span><span class="sxs-lookup"><span data-stu-id="4086f-109">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
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
  
### <a name="to-clear-a-graphic"></a><span data-ttu-id="4086f-110">若要清除圖形</span><span class="sxs-lookup"><span data-stu-id="4086f-110">To clear a graphic</span></span>  
  
-   <span data-ttu-id="4086f-111">首先，釋放記憶體正在使用映像，並再清除圖形。</span><span class="sxs-lookup"><span data-stu-id="4086f-111">First, release the memory being used by the image, and then clear the graphic.</span></span> <span data-ttu-id="4086f-112">記憶體回收會釋出記憶體稍後如果記憶體管理變得有問題。</span><span class="sxs-lookup"><span data-stu-id="4086f-112">Garbage collection will free up the memory later if memory management becomes a problem.</span></span>  
  
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
    >  <span data-ttu-id="4086f-113">如需有關為什麼您應該使用<xref:System.Drawing.Image.Dispose%2A>方法，如此一來，請參閱[清除 Unmanaged 資源上](../../../../docs/standard/garbage-collection/unmanaged.md)。</span><span class="sxs-lookup"><span data-stu-id="4086f-113">For more information on why you should use the <xref:System.Drawing.Image.Dispose%2A> method in this way, see [Cleaning Up Unmanaged Resources](../../../../docs/standard/garbage-collection/unmanaged.md).</span></span>  
  
     <span data-ttu-id="4086f-114">此程式碼將會清除映像，即使圖形在設計階段時載入控制項。</span><span class="sxs-lookup"><span data-stu-id="4086f-114">This code will clear the image even if a graphic was loaded into the control at design time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4086f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4086f-115">See Also</span></span>  
 <xref:System.Windows.Forms.PictureBox>  
 <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="4086f-116">PictureBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="4086f-116">PictureBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [<span data-ttu-id="4086f-117">操作說明：使用設計工具載入圖片</span><span class="sxs-lookup"><span data-stu-id="4086f-117">How to: Load a Picture Using the Designer</span></span>](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)  
 [<span data-ttu-id="4086f-118">操作說明：於執行階段修改圖片的大小或位置</span><span class="sxs-lookup"><span data-stu-id="4086f-118">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)  
 [<span data-ttu-id="4086f-119">PictureBox 控制項</span><span class="sxs-lookup"><span data-stu-id="4086f-119">PictureBox Control</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)

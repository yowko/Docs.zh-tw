---
title: HOW TO：設定 Windows Forms 控制項所顯示的影像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
ms.openlocfilehash: 031ddcb3b852e75353fed7420735350e79f23df3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085086"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a><span data-ttu-id="99629-102">HOW TO：設定 Windows Forms 控制項所顯示的影像</span><span class="sxs-lookup"><span data-stu-id="99629-102">How to: Set the Image Displayed by a Windows Forms Control</span></span>
<span data-ttu-id="99629-103">數個 Windows Form 控制項來顯示影像。</span><span class="sxs-lookup"><span data-stu-id="99629-103">Several Windows Forms controls can display images.</span></span> <span data-ttu-id="99629-104">這些映像可以是用途的控制項，例如按鈕，表示磁碟片圖示的圖示**儲存**命令。</span><span class="sxs-lookup"><span data-stu-id="99629-104">These images can be icons that clarify the purpose of the control, such as a diskette icon on a button denoting the **Save** command.</span></span> <span data-ttu-id="99629-105">或者，圖示可以提供給控制項的外觀和行為，您想要的背景影像。</span><span class="sxs-lookup"><span data-stu-id="99629-105">Alternatively, the icons can be background images to give the control the appearance and behavior you want.</span></span>  
  
### <a name="to-set-the-image-displayed-by-a-control"></a><span data-ttu-id="99629-106">若要設定控制項所顯示的影像</span><span class="sxs-lookup"><span data-stu-id="99629-106">To set the image displayed by a control</span></span>  
  
1.  <span data-ttu-id="99629-107">將控制項的`Image`或是`BackgroundImage`型別的物件的屬性<xref:System.Drawing.Image>。</span><span class="sxs-lookup"><span data-stu-id="99629-107">Set the control's `Image` or `BackgroundImage` property to an object of type <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="99629-108">一般而言，您將會載入映像從檔案使用<xref:System.Drawing.Image.FromFile%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="99629-108">Generally, you will be loading the image from a file by using the <xref:System.Drawing.Image.FromFile%2A> method.</span></span>  
  
     <span data-ttu-id="99629-109">在下列程式碼範例中，將路徑設為映像的位置**My Pictures**資料夾。</span><span class="sxs-lookup"><span data-stu-id="99629-109">In the following code example, the path set for the location of the image is the **My Pictures** folder.</span></span> <span data-ttu-id="99629-110">執行 Windows 作業系統的大部分電腦都會包含此目錄。</span><span class="sxs-lookup"><span data-stu-id="99629-110">Most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="99629-111">這也可讓具有最少的系統存取層級的使用者安全地執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="99629-111">This also enables users with minimal system access levels to run the application safely.</span></span> <span data-ttu-id="99629-112">下列程式碼範例需要您已有表單<xref:System.Windows.Forms.PictureBox>加入控制項。</span><span class="sxs-lookup"><span data-stu-id="99629-112">The following code example requires that you already have a form with a <xref:System.Windows.Forms.PictureBox> control added.</span></span>  
  
    ```vb  
    ' Replace the image named below  
    ' with an icon of your own choosing.  
    PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.MyPictures) _  
       & "\Image.gif")  
    ```  
  
    ```csharp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.MyPictures)  
       + @"\Image.gif");  
    ```  
  
    ```cpp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    pictureBox1->Image = Image::FromFile(String::Concat  
       (System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::MyPictures),  
       "\\Image.gif"));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="99629-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99629-113">See also</span></span>

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>

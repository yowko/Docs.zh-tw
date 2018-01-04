---
title: "如何：設定由 Windows Form 控制項所顯示的影像"
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
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4bf42fc90e19cbac0f165b59c0c6d3dfb7456b5a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a><span data-ttu-id="2cabf-102">如何：設定由 Windows Form 控制項所顯示的影像</span><span class="sxs-lookup"><span data-stu-id="2cabf-102">How to: Set the Image Displayed by a Windows Forms Control</span></span>
<span data-ttu-id="2cabf-103">數個 Windows Form 控制項可以顯示影像。</span><span class="sxs-lookup"><span data-stu-id="2cabf-103">Several Windows Forms controls can display images.</span></span> <span data-ttu-id="2cabf-104">這些映像可以是用途的控制項，例如按鈕，表示磁碟片圖示的圖示**儲存**命令。</span><span class="sxs-lookup"><span data-stu-id="2cabf-104">These images can be icons that clarify the purpose of the control, such as a diskette icon on a button denoting the **Save** command.</span></span> <span data-ttu-id="2cabf-105">或者，圖示可以提供控制項的外觀和行為，您想要的背景影像。</span><span class="sxs-lookup"><span data-stu-id="2cabf-105">Alternatively, the icons can be background images to give the control the appearance and behavior you want.</span></span>  
  
### <a name="to-set-the-image-displayed-by-a-control"></a><span data-ttu-id="2cabf-106">若要設定控制項所顯示的影像</span><span class="sxs-lookup"><span data-stu-id="2cabf-106">To set the image displayed by a control</span></span>  
  
1.  <span data-ttu-id="2cabf-107">將控制項的`Image`或`BackgroundImage`屬性型別的物件<xref:System.Drawing.Image>。</span><span class="sxs-lookup"><span data-stu-id="2cabf-107">Set the control's `Image` or `BackgroundImage` property to an object of type <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="2cabf-108">一般而言，您將會映像從檔案載入使用<xref:System.Drawing.Image.FromFile%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="2cabf-108">Generally, you will be loading the image from a file by using the <xref:System.Drawing.Image.FromFile%2A> method.</span></span>  
  
     <span data-ttu-id="2cabf-109">在下列程式碼範例中，設定路徑的映像的位置是**我的圖片**資料夾。</span><span class="sxs-lookup"><span data-stu-id="2cabf-109">In the following code example, the path set for the location of the image is the **My Pictures** folder.</span></span> <span data-ttu-id="2cabf-110">執行 Windows 作業系統的大部分電腦都會包含此目錄。</span><span class="sxs-lookup"><span data-stu-id="2cabf-110">Most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="2cabf-111">這也讓使用者以最少的系統存取層級可安全地執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="2cabf-111">This also enables users with minimal system access levels to run the application safely.</span></span> <span data-ttu-id="2cabf-112">下列程式碼範例需要您已經有的表單具有<xref:System.Windows.Forms.PictureBox>加入控制項。</span><span class="sxs-lookup"><span data-stu-id="2cabf-112">The following code example requires that you already have a form with a <xref:System.Windows.Forms.PictureBox> control added.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2cabf-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="2cabf-113">See Also</span></span>  
 <xref:System.Drawing.Image.FromFile%2A>  
 <xref:System.Drawing.Image>  
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>

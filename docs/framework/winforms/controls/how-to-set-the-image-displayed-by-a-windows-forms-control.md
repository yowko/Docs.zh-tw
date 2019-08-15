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
ms.openlocfilehash: 99bde4fac7b3057358c7e6a8550efdb4cc351eb0
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037873"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a><span data-ttu-id="15216-102">作法：設定 Windows Forms 控制項所顯示的影像</span><span class="sxs-lookup"><span data-stu-id="15216-102">How to: Set the image displayed by a Windows Forms control</span></span>

<span data-ttu-id="15216-103">數個 Windows Forms 控制項可以顯示影像。</span><span class="sxs-lookup"><span data-stu-id="15216-103">Several Windows Forms controls can display images.</span></span> <span data-ttu-id="15216-104">這些影像可以是用來闡明控制項用途的圖示, 例如代表**儲存**命令的按鈕上的磁片圖示。</span><span class="sxs-lookup"><span data-stu-id="15216-104">These images can be icons that clarify the purpose of the control, such as a diskette icon on a button denoting the **Save** command.</span></span> <span data-ttu-id="15216-105">或者, 圖示可以是背景影像, 為控制項提供您想要的外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="15216-105">Alternatively, the icons can be background images to give the control the appearance and behavior you want.</span></span>

## <a name="to-set-the-image-displayed-by-a-control"></a><span data-ttu-id="15216-106">若要設定控制項所顯示的影像</span><span class="sxs-lookup"><span data-stu-id="15216-106">To set the image displayed by a control</span></span>

1. <span data-ttu-id="15216-107">將控制項的`Image`或`BackgroundImage`屬性設定為類型<xref:System.Drawing.Image>的物件。</span><span class="sxs-lookup"><span data-stu-id="15216-107">Set the control's `Image` or `BackgroundImage` property to an object of type <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="15216-108">一般來說, 您會使用<xref:System.Drawing.Image.FromFile%2A>方法從檔案載入影像。</span><span class="sxs-lookup"><span data-stu-id="15216-108">Generally, you will be loading the image from a file by using the <xref:System.Drawing.Image.FromFile%2A> method.</span></span>

     <span data-ttu-id="15216-109">在下列程式碼範例中, 為影像位置設定的路徑是 [我的**圖片**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="15216-109">In the following code example, the path set for the location of the image is the **My Pictures** folder.</span></span> <span data-ttu-id="15216-110">大部分執行 Windows 作業系統的電腦都會包含此目錄。</span><span class="sxs-lookup"><span data-stu-id="15216-110">Most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="15216-111">這也可讓具有最低系統存取層級的使用者安全地執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="15216-111">This also enables users with minimal system access levels to run the application safely.</span></span> <span data-ttu-id="15216-112">下列程式碼範例要求您已經有已加入<xref:System.Windows.Forms.PictureBox>控制項的表單。</span><span class="sxs-lookup"><span data-stu-id="15216-112">The following code example requires that you already have a form with a <xref:System.Windows.Forms.PictureBox> control added.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="15216-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15216-113">See also</span></span>

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>

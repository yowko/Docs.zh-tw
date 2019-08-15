---
title: 作法：使用設計工具載入圖片 (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 818bc63b5b3bea6c73804f716a72ba3cd1a62b4c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039685"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a><span data-ttu-id="d5455-102">作法：使用設計工具載入圖片 (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="d5455-102">How to: Load a Picture Using the Designer (Windows Forms)</span></span>

<span data-ttu-id="d5455-103">您可以使用<xref:System.Windows.Forms.PictureBox> Windows Forms 控制項, <xref:System.Windows.Forms.PictureBox.Image%2A>將屬性設定為有效的圖片, 在設計階段載入和顯示表單上的圖片。</span><span class="sxs-lookup"><span data-stu-id="d5455-103">With the Windows Forms <xref:System.Windows.Forms.PictureBox> control, you can load and display a picture on a form at design time by setting the <xref:System.Windows.Forms.PictureBox.Image%2A> property to a valid picture.</span></span> <span data-ttu-id="d5455-104">下表顯示可接受的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="d5455-104">The following table shows the acceptable file types.</span></span>

|<span data-ttu-id="d5455-105">類型</span><span class="sxs-lookup"><span data-stu-id="d5455-105">Type</span></span>|<span data-ttu-id="d5455-106">副檔名</span><span class="sxs-lookup"><span data-stu-id="d5455-106">File name extension</span></span>|
|---|---|
|<span data-ttu-id="d5455-107">Bitmap</span><span class="sxs-lookup"><span data-stu-id="d5455-107">Bitmap</span></span>|<span data-ttu-id="d5455-108">.bmp</span><span class="sxs-lookup"><span data-stu-id="d5455-108">.bmp</span></span>|
|<span data-ttu-id="d5455-109">圖示</span><span class="sxs-lookup"><span data-stu-id="d5455-109">Icon</span></span>|<span data-ttu-id="d5455-110">.ico</span><span class="sxs-lookup"><span data-stu-id="d5455-110">.ico</span></span>|
|<span data-ttu-id="d5455-111">GIF</span><span class="sxs-lookup"><span data-stu-id="d5455-111">GIF</span></span>|<span data-ttu-id="d5455-112">.gif</span><span class="sxs-lookup"><span data-stu-id="d5455-112">.gif</span></span>|
|<span data-ttu-id="d5455-113">中繼檔</span><span class="sxs-lookup"><span data-stu-id="d5455-113">Metafile</span></span>|<span data-ttu-id="d5455-114">.wmf</span><span class="sxs-lookup"><span data-stu-id="d5455-114">.wmf</span></span>|
|<span data-ttu-id="d5455-115">JPEG</span><span class="sxs-lookup"><span data-stu-id="d5455-115">JPEG</span></span>|<span data-ttu-id="d5455-116">.jpg</span><span class="sxs-lookup"><span data-stu-id="d5455-116">.jpg</span></span>|

## <a name="to-display-a-picture-at-design-time"></a><span data-ttu-id="d5455-117">在設計階段顯示圖片</span><span class="sxs-lookup"><span data-stu-id="d5455-117">To display a picture at design time</span></span>

1. <span data-ttu-id="d5455-118">在表單上繪製控制項。<xref:System.Windows.Forms.PictureBox></span><span class="sxs-lookup"><span data-stu-id="d5455-118">Draw a <xref:System.Windows.Forms.PictureBox> control on a form.</span></span>

2. <span data-ttu-id="d5455-119">在 [**屬性**] 視窗中, <xref:System.Windows.Forms.PictureBox.Image%2A>選取屬性, 然後選取省略號按鈕以顯示 [**開啟**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d5455-119">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property, then select the ellipsis button to display the **Open** dialog box.</span></span>

3. <span data-ttu-id="d5455-120">如果您要尋找特定的檔案類型 (例如 .gif 檔案), 請在 [**檔案類型**] 方塊中選取它。</span><span class="sxs-lookup"><span data-stu-id="d5455-120">If you're looking for a specific file type (for example, .gif files), select it in the **Files of type** box.</span></span>

4. <span data-ttu-id="d5455-121">選取您要顯示的檔案。</span><span class="sxs-lookup"><span data-stu-id="d5455-121">Select the file you want to display.</span></span>

## <a name="to-clear-the-picture-at-design-time"></a><span data-ttu-id="d5455-122">若要在設計階段清除圖片</span><span class="sxs-lookup"><span data-stu-id="d5455-122">To clear the picture at design time</span></span>

1. <span data-ttu-id="d5455-123">在 [**屬性**] 視窗中, <xref:System.Windows.Forms.PictureBox.Image%2A>選取屬性。</span><span class="sxs-lookup"><span data-stu-id="d5455-123">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property.</span></span> <span data-ttu-id="d5455-124">以滑鼠右鍵按一下影像物件名稱左側的小型縮圖影像, 然後選擇 [**重設**]。</span><span class="sxs-lookup"><span data-stu-id="d5455-124">Right-click the small thumbnail image that appears to the left of the name of the image object, and then choose **Reset**.</span></span>

## <a name="see-also"></a><span data-ttu-id="d5455-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5455-125">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="d5455-126">PictureBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="d5455-126">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="d5455-127">如何：在執行時間修改圖片的大小或位置</span><span class="sxs-lookup"><span data-stu-id="d5455-127">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="d5455-128">如何：在執行時間設定圖片</span><span class="sxs-lookup"><span data-stu-id="d5455-128">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="d5455-129">PictureBox 控制項</span><span class="sxs-lookup"><span data-stu-id="d5455-129">PictureBox Control</span></span>](picturebox-control-windows-forms.md)

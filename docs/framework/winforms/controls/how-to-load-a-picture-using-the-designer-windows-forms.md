---
title: 如何：使用設計工具載入圖片
description: 瞭解如何使用 [Windows Forms PictureBox] 控制項在設計階段載入和顯示表單上的圖片。
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: a05ffe19412fc7a4e3e02f01336d89cce39fac8a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325593"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a><span data-ttu-id="fcde3-103">如何：使用設計工具載入圖片 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="fcde3-103">How to: Load a Picture Using the Designer (Windows Forms)</span></span>

<span data-ttu-id="fcde3-104"><xref:System.Windows.Forms.PictureBox>您可以使用 Windows Forms 控制項，將屬性設定為有效的圖片，在設計階段載入和顯示表單上的圖片 <xref:System.Windows.Forms.PictureBox.Image%2A> 。</span><span class="sxs-lookup"><span data-stu-id="fcde3-104">With the Windows Forms <xref:System.Windows.Forms.PictureBox> control, you can load and display a picture on a form at design time by setting the <xref:System.Windows.Forms.PictureBox.Image%2A> property to a valid picture.</span></span> <span data-ttu-id="fcde3-105">下表顯示可接受的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="fcde3-105">The following table shows the acceptable file types.</span></span>

|<span data-ttu-id="fcde3-106">類型</span><span class="sxs-lookup"><span data-stu-id="fcde3-106">Type</span></span>|<span data-ttu-id="fcde3-107">副檔名</span><span class="sxs-lookup"><span data-stu-id="fcde3-107">File name extension</span></span>|
|---|---|
|<span data-ttu-id="fcde3-108">點陣圖</span><span class="sxs-lookup"><span data-stu-id="fcde3-108">Bitmap</span></span>|<span data-ttu-id="fcde3-109">.bmp</span><span class="sxs-lookup"><span data-stu-id="fcde3-109">.bmp</span></span>|
|<span data-ttu-id="fcde3-110">圖示</span><span class="sxs-lookup"><span data-stu-id="fcde3-110">Icon</span></span>|<span data-ttu-id="fcde3-111">.ico</span><span class="sxs-lookup"><span data-stu-id="fcde3-111">.ico</span></span>|
|<span data-ttu-id="fcde3-112">GIF</span><span class="sxs-lookup"><span data-stu-id="fcde3-112">GIF</span></span>|<span data-ttu-id="fcde3-113">.gif</span><span class="sxs-lookup"><span data-stu-id="fcde3-113">.gif</span></span>|
|<span data-ttu-id="fcde3-114"> 中繼檔</span><span class="sxs-lookup"><span data-stu-id="fcde3-114">Metafile</span></span>|<span data-ttu-id="fcde3-115">.wmf</span><span class="sxs-lookup"><span data-stu-id="fcde3-115">.wmf</span></span>|
|<span data-ttu-id="fcde3-116">JPEG</span><span class="sxs-lookup"><span data-stu-id="fcde3-116">JPEG</span></span>|<span data-ttu-id="fcde3-117">.jpg</span><span class="sxs-lookup"><span data-stu-id="fcde3-117">.jpg</span></span>|

## <a name="to-display-a-picture-at-design-time"></a><span data-ttu-id="fcde3-118">在設計階段顯示圖片</span><span class="sxs-lookup"><span data-stu-id="fcde3-118">To display a picture at design time</span></span>

1. <span data-ttu-id="fcde3-119"><xref:System.Windows.Forms.PictureBox>在表單上繪製控制項。</span><span class="sxs-lookup"><span data-stu-id="fcde3-119">Draw a <xref:System.Windows.Forms.PictureBox> control on a form.</span></span>

2. <span data-ttu-id="fcde3-120">在 [**屬性**] 視窗中，選取 <xref:System.Windows.Forms.PictureBox.Image%2A> 屬性，然後選取省略號按鈕以顯示 [**開啟**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="fcde3-120">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property, then select the ellipsis button to display the **Open** dialog box.</span></span>

3. <span data-ttu-id="fcde3-121">如果您要尋找特定的檔案類型（例如 .gif 檔案），請在 [**檔案類型**] 方塊中選取它。</span><span class="sxs-lookup"><span data-stu-id="fcde3-121">If you're looking for a specific file type (for example, .gif files), select it in the **Files of type** box.</span></span>

4. <span data-ttu-id="fcde3-122">選取您要顯示的檔案。</span><span class="sxs-lookup"><span data-stu-id="fcde3-122">Select the file you want to display.</span></span>

## <a name="to-clear-the-picture-at-design-time"></a><span data-ttu-id="fcde3-123">若要在設計階段清除圖片</span><span class="sxs-lookup"><span data-stu-id="fcde3-123">To clear the picture at design time</span></span>

1. <span data-ttu-id="fcde3-124">在 [**屬性**] 視窗中，選取 <xref:System.Windows.Forms.PictureBox.Image%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="fcde3-124">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property.</span></span> <span data-ttu-id="fcde3-125">以滑鼠右鍵按一下影像物件名稱左側的小型縮圖影像，然後選擇 [**重設**]。</span><span class="sxs-lookup"><span data-stu-id="fcde3-125">Right-click the small thumbnail image that appears to the left of the name of the image object, and then choose **Reset**.</span></span>

## <a name="see-also"></a><span data-ttu-id="fcde3-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcde3-126">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="fcde3-127">PictureBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="fcde3-127">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="fcde3-128">操作說明：於執行階段修改圖片的大小或位置</span><span class="sxs-lookup"><span data-stu-id="fcde3-128">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="fcde3-129">操作說明：在執行階段設定圖案</span><span class="sxs-lookup"><span data-stu-id="fcde3-129">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="fcde3-130">PictureBox 控制項</span><span class="sxs-lookup"><span data-stu-id="fcde3-130">PictureBox Control</span></span>](picturebox-control-windows-forms.md)

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
ms.openlocfilehash: 1d95d5baafa42c7dea40933ba837b684d90b7b2b
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972377"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a><span data-ttu-id="596a3-102">作法：使用設計工具載入圖片 (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="596a3-102">How to: Load a Picture Using the Designer (Windows Forms)</span></span>

<span data-ttu-id="596a3-103">您可以使用<xref:System.Windows.Forms.PictureBox> Windows Forms 控制項, <xref:System.Windows.Forms.PictureBox.Image%2A>將屬性設定為有效的圖片, 在設計階段載入和顯示表單上的圖片。</span><span class="sxs-lookup"><span data-stu-id="596a3-103">With the Windows Forms <xref:System.Windows.Forms.PictureBox> control, you can load and display a picture on a form at design time by setting the <xref:System.Windows.Forms.PictureBox.Image%2A> property to a valid picture.</span></span> <span data-ttu-id="596a3-104">下表顯示可接受的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="596a3-104">The following table shows the acceptable file types.</span></span>

|<span data-ttu-id="596a3-105">類型</span><span class="sxs-lookup"><span data-stu-id="596a3-105">Type</span></span>|<span data-ttu-id="596a3-106">副檔名</span><span class="sxs-lookup"><span data-stu-id="596a3-106">File name extension</span></span>|
|----------|-------------------------|
|<span data-ttu-id="596a3-107">Bitmap</span><span class="sxs-lookup"><span data-stu-id="596a3-107">Bitmap</span></span>|<span data-ttu-id="596a3-108">.bmp</span><span class="sxs-lookup"><span data-stu-id="596a3-108">.bmp</span></span>|
|<span data-ttu-id="596a3-109">圖示</span><span class="sxs-lookup"><span data-stu-id="596a3-109">Icon</span></span>|<span data-ttu-id="596a3-110">.ico</span><span class="sxs-lookup"><span data-stu-id="596a3-110">.ico</span></span>|
|<span data-ttu-id="596a3-111">GIF</span><span class="sxs-lookup"><span data-stu-id="596a3-111">GIF</span></span>|<span data-ttu-id="596a3-112">.gif</span><span class="sxs-lookup"><span data-stu-id="596a3-112">.gif</span></span>|
|<span data-ttu-id="596a3-113">中繼檔</span><span class="sxs-lookup"><span data-stu-id="596a3-113">Metafile</span></span>|<span data-ttu-id="596a3-114">.wmf</span><span class="sxs-lookup"><span data-stu-id="596a3-114">.wmf</span></span>|
|<span data-ttu-id="596a3-115">JPEG</span><span class="sxs-lookup"><span data-stu-id="596a3-115">JPEG</span></span>|<span data-ttu-id="596a3-116">.jpg</span><span class="sxs-lookup"><span data-stu-id="596a3-116">.jpg</span></span>|

> [!NOTE]
>  <span data-ttu-id="596a3-117">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="596a3-117">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="596a3-118">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="596a3-118">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="596a3-119">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="596a3-119">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>

## <a name="to-display-a-picture-at-design-time"></a><span data-ttu-id="596a3-120">在設計階段顯示圖片</span><span class="sxs-lookup"><span data-stu-id="596a3-120">To display a picture at design time</span></span>

1. <span data-ttu-id="596a3-121">在表單上繪製控制項。<xref:System.Windows.Forms.PictureBox></span><span class="sxs-lookup"><span data-stu-id="596a3-121">Draw a <xref:System.Windows.Forms.PictureBox> control on a form.</span></span>

2. <span data-ttu-id="596a3-122">在 屬性視窗上, 選取<xref:System.Windows.Forms.PictureBox.Image%2A>屬性, 然後按一下省略號按鈕以顯示 **開啟** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="596a3-122">On the Properties window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property, then click the ellipsis button to display the **Open** dialog box.</span></span>

3. <span data-ttu-id="596a3-123">如果您要尋找特定的檔案類型 (例如 .gif 檔案), 請在 [**檔案類型**] 方塊中選取它。</span><span class="sxs-lookup"><span data-stu-id="596a3-123">If you are looking for a specific file type (for example, .gif files), select it in the **Files of type** box.</span></span>

4. <span data-ttu-id="596a3-124">選取您要顯示的檔案。</span><span class="sxs-lookup"><span data-stu-id="596a3-124">Select the file you want to display.</span></span>

## <a name="to-clear-the-picture-at-design-time"></a><span data-ttu-id="596a3-125">若要在設計階段清除圖片</span><span class="sxs-lookup"><span data-stu-id="596a3-125">To clear the picture at design time</span></span>

1. <span data-ttu-id="596a3-126">在 [**屬性**] 視窗中, <xref:System.Windows.Forms.PictureBox.Image%2A>選取屬性, 然後以滑鼠右鍵按一下影像物件名稱左邊的小型縮圖影像。</span><span class="sxs-lookup"><span data-stu-id="596a3-126">On the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property and right-click the small thumbnail image that appears to the left of the name of the image object.</span></span> <span data-ttu-id="596a3-127">選擇 [**重設**]。</span><span class="sxs-lookup"><span data-stu-id="596a3-127">Choose **Reset**.</span></span>

## <a name="see-also"></a><span data-ttu-id="596a3-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="596a3-128">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="596a3-129">PictureBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="596a3-129">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="596a3-130">如何：在執行時間修改圖片的大小或位置</span><span class="sxs-lookup"><span data-stu-id="596a3-130">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="596a3-131">如何：在執行時間設定圖片</span><span class="sxs-lookup"><span data-stu-id="596a3-131">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="596a3-132">PictureBox 控制項</span><span class="sxs-lookup"><span data-stu-id="596a3-132">PictureBox Control</span></span>](picturebox-control-windows-forms.md)

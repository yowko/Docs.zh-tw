---
title: 如何：使用設計工具載入圖片
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 12b90d561a18fcffaafb9c45b7fa6be6dd060215
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736323"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>如何：使用設計工具載入圖片 (Windows Form)

您可以使用 Windows Forms <xref:System.Windows.Forms.PictureBox> 控制項，將 <xref:System.Windows.Forms.PictureBox.Image%2A> 屬性設為有效的圖片，在設計階段將圖片載入並顯示在表單上。 下表顯示可接受的檔案類型。

|類型|副檔名|
|---|---|
|點陣圖|.bmp|
|圖示|.ico|
|GIF|.gif|
|中繼檔|.wmf|
|JPEG|.jpg|

## <a name="to-display-a-picture-at-design-time"></a>在設計階段顯示圖片

1. 在表單上繪製 <xref:System.Windows.Forms.PictureBox> 控制項。

2. 在 [**屬性**] 視窗中，選取 [<xref:System.Windows.Forms.PictureBox.Image%2A>] 屬性，然後選取省略號按鈕以顯示 [**開啟**] 對話方塊。

3. 如果您要尋找特定的檔案類型（例如 .gif 檔案），請在 [**檔案類型**] 方塊中選取它。

4. 選取您要顯示的檔案。

## <a name="to-clear-the-picture-at-design-time"></a>若要在設計階段清除圖片

1. 在 [**屬性**] 視窗中，選取 [<xref:System.Windows.Forms.PictureBox.Image%2A>] 屬性。 以滑鼠右鍵按一下影像物件名稱左側的小型縮圖影像，然後選擇 [**重設**]。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.PictureBox>
- [PictureBox 控制項概觀](picturebox-control-overview-windows-forms.md)
- [操作說明：於執行階段修改圖片的大小或位置](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [操作說明：在執行階段設定圖案](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox 控制項](picturebox-control-windows-forms.md)

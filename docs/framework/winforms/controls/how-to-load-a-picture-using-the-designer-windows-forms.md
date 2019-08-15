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
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>作法：使用設計工具載入圖片 (Windows Forms)

您可以使用<xref:System.Windows.Forms.PictureBox> Windows Forms 控制項, <xref:System.Windows.Forms.PictureBox.Image%2A>將屬性設定為有效的圖片, 在設計階段載入和顯示表單上的圖片。 下表顯示可接受的檔案類型。

|類型|副檔名|
|---|---|
|Bitmap|.bmp|
|圖示|.ico|
|GIF|.gif|
|中繼檔|.wmf|
|JPEG|.jpg|

## <a name="to-display-a-picture-at-design-time"></a>在設計階段顯示圖片

1. 在表單上繪製控制項。<xref:System.Windows.Forms.PictureBox>

2. 在 [**屬性**] 視窗中, <xref:System.Windows.Forms.PictureBox.Image%2A>選取屬性, 然後選取省略號按鈕以顯示 [**開啟**] 對話方塊。

3. 如果您要尋找特定的檔案類型 (例如 .gif 檔案), 請在 [**檔案類型**] 方塊中選取它。

4. 選取您要顯示的檔案。

## <a name="to-clear-the-picture-at-design-time"></a>若要在設計階段清除圖片

1. 在 [**屬性**] 視窗中, <xref:System.Windows.Forms.PictureBox.Image%2A>選取屬性。 以滑鼠右鍵按一下影像物件名稱左側的小型縮圖影像, 然後選擇 [**重設**]。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.PictureBox>
- [PictureBox 控制項概觀](picturebox-control-overview-windows-forms.md)
- [如何：在執行時間修改圖片的大小或位置](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [如何：在執行時間設定圖片](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox 控制項](picturebox-control-windows-forms.md)

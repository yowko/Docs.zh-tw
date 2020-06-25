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
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>如何：使用設計工具載入圖片 (Windows Form)

<xref:System.Windows.Forms.PictureBox>您可以使用 Windows Forms 控制項，將屬性設定為有效的圖片，在設計階段載入和顯示表單上的圖片 <xref:System.Windows.Forms.PictureBox.Image%2A> 。 下表顯示可接受的檔案類型。

|類型|副檔名|
|---|---|
|點陣圖|.bmp|
|圖示|.ico|
|GIF|.gif|
| 中繼檔|.wmf|
|JPEG|.jpg|

## <a name="to-display-a-picture-at-design-time"></a>在設計階段顯示圖片

1. <xref:System.Windows.Forms.PictureBox>在表單上繪製控制項。

2. 在 [**屬性**] 視窗中，選取 <xref:System.Windows.Forms.PictureBox.Image%2A> 屬性，然後選取省略號按鈕以顯示 [**開啟**] 對話方塊。

3. 如果您要尋找特定的檔案類型（例如 .gif 檔案），請在 [**檔案類型**] 方塊中選取它。

4. 選取您要顯示的檔案。

## <a name="to-clear-the-picture-at-design-time"></a>若要在設計階段清除圖片

1. 在 [**屬性**] 視窗中，選取 <xref:System.Windows.Forms.PictureBox.Image%2A> 屬性。 以滑鼠右鍵按一下影像物件名稱左側的小型縮圖影像，然後選擇 [**重設**]。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.PictureBox>
- [PictureBox 控制項概觀](picturebox-control-overview-windows-forms.md)
- [操作說明：於執行階段修改圖片的大小或位置](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [操作說明：在執行階段設定圖案](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox 控制項](picturebox-control-windows-forms.md)

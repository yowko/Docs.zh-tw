---
title: HOW TO：使用設計工具 (Windows Form) 載入圖片
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 6bdf7c3df0ffd97dd88a4c442a8a73593a0447ee
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59336378"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>HOW TO：使用設計工具 (Windows Form) 載入圖片
使用 Windows Form<xref:System.Windows.Forms.PictureBox>控制項，您可以載入並設定表單上顯示一張圖片在設計階段<xref:System.Windows.Forms.PictureBox.Image%2A>屬性，以有效的圖片。 下表顯示可接受的檔案類型。  
  
|類型|副檔名|  
|----------|-------------------------|  
|Bitmap|.bmp|  
|圖示|.ico|  
|GIF|.gif|  
|中繼檔|.wmf|  
|JPEG|.jpg|  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-display-a-picture-at-design-time"></a>若要在設計階段顯示的圖片  
  
1. 繪製<xref:System.Windows.Forms.PictureBox>表單上的控制項。  
  
2. 在 屬性 視窗中，選取<xref:System.Windows.Forms.PictureBox.Image%2A>屬性，然後按一下省略符號按鈕，顯示**開啟** 對話方塊。  
  
3. 如果您要尋找特定檔案類型 （例如，.gif 檔案），選取 [在**類型的檔案**] 方塊中。  
  
4. 選取您想要顯示的檔案。  
  
### <a name="to-clear-the-picture-at-design-time"></a>若要在設計階段清除圖片  
  
1. 在 **屬性**視窗中，選取<xref:System.Windows.Forms.PictureBox.Image%2A>屬性並以滑鼠右鍵按一下左邊的映像物件的名稱會出現的小型縮圖影像。 選擇**重設**。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.PictureBox>
- [PictureBox 控制項概觀](picturebox-control-overview-windows-forms.md)
- [如何：在執行階段修改的大小或位置的圖片](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [如何：在執行階段設定圖案](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox 控制項](picturebox-control-windows-forms.md)

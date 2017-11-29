---
title: "如何：使用設計工具載入圖片 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9049bf5f9467401bff098459b8f5ed55c1ee1975
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>如何：使用設計工具載入圖片 (Windows Form)
使用 Windows Form<xref:System.Windows.Forms.PictureBox>控制項，您可以載入並設定在表單上顯示圖片在設計階段<xref:System.Windows.Forms.PictureBox.Image%2A>有效圖片的屬性。 下表顯示可接受的檔案類型。  
  
|類型|檔案名稱副檔名|  
|----------|-------------------------|  
|Bitmap|.bmp|  
|圖示|.ico|  
|GIF|.gif|  
|中繼檔|.wmf|  
|JPEG|.jpg|  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### <a name="to-display-a-picture-at-design-time"></a>若要在設計階段顯示的圖片  
  
1.  繪製<xref:System.Windows.Forms.PictureBox>控制項在表單上的。  
  
2.  在 屬性 視窗中，選取<xref:System.Windows.Forms.PictureBox.Image%2A>屬性，然後按一下省略符號按鈕，以顯示**開啟** 對話方塊。  
  
3.  如果您要尋找特定檔案類型 （例如，.gif 檔案），請選取在**檔案類型**方塊。  
  
4.  選取您想要顯示的檔案。  
  
### <a name="to-clear-the-picture-at-design-time"></a>若要在設計階段清除圖片  
  
1.  在**屬性**視窗中，選取<xref:System.Windows.Forms.PictureBox.Image%2A>屬性，以滑鼠右鍵按一下映像物件的名稱左邊的小型縮圖影像。 選擇**重設**。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.PictureBox>  
 [PictureBox 控制項概觀](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [操作說明：於執行階段修改圖片的大小或位置](../../../../docs/framework/winforms/controls/how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)  
 [操作說明：在執行階段設定圖案](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)  
 [PictureBox 控制項](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)

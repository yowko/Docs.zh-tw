---
title: 作法：建立縮圖影像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thumbnail images [Windows Forms], creating
- images [Windows Forms], creating thumbnails
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
ms.openlocfilehash: 786a92d99f5e7a0c27f502efa9a5fe617ac4d4d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923745"
---
# <a name="how-to-create-thumbnail-images"></a>作法：建立縮圖影像
縮圖影像是影像的小型版本。 您可以藉由呼叫<xref:System.Drawing.Image.GetThumbnailImage%2A> <xref:System.Drawing.Image>物件的方法來建立縮圖影像。  
  
## <a name="example"></a>範例  
 下列範例<xref:System.Drawing.Image>會從 JPG 檔案中建立物件。 原始影像的寬度為640圖元, 而高度為479圖元。 程式碼會建立寬度為100圖元且高度為100圖元的縮圖影像。  
  
 下圖顯示縮圖影像:  
  
 ![顯示輸出縮圖的螢幕擷取畫面。](./media/how-to-create-thumbnail-images/construct-thumbnail-image.png)  
  
> [!NOTE]
> 在此範例中, 回呼方法已宣告, 但從未使用過。 這支援所有的 GDI + 版本。  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是針對與 Windows Forms 搭配使用所設計, 而且它<xref:System.Windows.Forms.PaintEventArgs>需要`e`, 這<xref:System.Windows.Forms.Control.Paint>是事件處理常式的參數。 若要執行範例, 請遵循下列步驟:  
  
1. 新建 Windows Forms 應用程式  
  
2. 將範例程式碼新增至表單。  
  
3. 建立表單<xref:System.Windows.Forms.Control.Paint>事件的處理常式  
  
4. 在處理常式中, `GetThumbnail`呼叫方法並傳遞給<xref:System.Windows.Forms.PaintEventArgs>。 `e` <xref:System.Windows.Forms.Control.Paint>  
  
5. 尋找您要做為縮圖的影像檔案。  
  
6. `GetThumbnail`在方法中, 指定影像的路徑和檔案名。  
  
7. 按 F5 執行範例。  
  
     100 x 100 縮圖影像會出現在表單上。  
  
## <a name="see-also"></a>另請參閱

- [影像、點陣圖和中繼檔](images-bitmaps-and-metafiles.md)
- [使用影像、點陣圖、圖示和中繼檔](working-with-images-bitmaps-icons-and-metafiles.md)

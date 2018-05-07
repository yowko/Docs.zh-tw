---
title: 如何：建立縮圖影像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thumbnail images [Windows Forms], creating
- images [Windows Forms], creating thumbnails
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
ms.openlocfilehash: 870ea223698e48438bd4dd08597d0a6ab79cec27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-thumbnail-images"></a>如何：建立縮圖影像
縮圖影像是小型版本的映像。 您可以藉由呼叫建立縮圖影像<xref:System.Drawing.Image.GetThumbnailImage%2A>方法<xref:System.Drawing.Image>物件。  
  
## <a name="example"></a>範例  
 下列範例會建構<xref:System.Drawing.Image>物件從 JPG 檔案。 原始影像的寬度為 640 像素和 479 個像素的高度。 程式碼會建立有 100 像素寬度和高度為 100 像素的縮圖影像。  
  
 下圖顯示的縮圖影像。  
  
 ![縮圖影像](../../../../docs/framework/winforms/advanced/media/thumbnail1.png "Thumbnail1")  
  
> [!NOTE]
>  在此範例中，回呼方法已宣告，但從未使用。 這可支援所有版本的 GDI +。  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。 若要執行此範例，請遵循下列步驟：  
  
1.  新建 Windows Forms 應用程式  
  
2.  將範例程式碼加入至表單。  
  
3.  建立表單的處理常式<xref:System.Windows.Forms.Control.Paint>事件  
  
4.  在<xref:System.Windows.Forms.Control.Paint>處理常式，此時會呼叫`GetThumbnail`方法並傳入`e`如<xref:System.Windows.Forms.PaintEventArgs>。  
  
5.  尋找您想要的縮圖的影像檔。  
  
6.  在`GetThumbnail`方法，指定的路徑和檔案名稱以您的映像。  
  
7.  按 F5 執行範例。  
  
     100 x 100 的縮圖影像會出現在表單上。  
  
## <a name="see-also"></a>另請參閱  
 [影像、點陣圖和中繼檔](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [使用影像、點陣圖、圖示和中繼檔](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)

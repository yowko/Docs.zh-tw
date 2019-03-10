---
title: HOW TO：建立縮圖影像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thumbnail images [Windows Forms], creating
- images [Windows Forms], creating thumbnails
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
ms.openlocfilehash: 3ed1fb6a9a7fc8e7ded6ae0e124ca7dcbf0f3c98
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716955"
---
# <a name="how-to-create-thumbnail-images"></a>HOW TO：建立縮圖影像
縮圖的影像是影像的縮小版本。 您可以藉由呼叫建立縮圖影像<xref:System.Drawing.Image.GetThumbnailImage%2A>方法的<xref:System.Drawing.Image>物件。  
  
## <a name="example"></a>範例  
 下列範例會建構<xref:System.Drawing.Image>JPG 檔案中的物件。 原始的映像有 640 像素的寬度和高度為 479 個像素。 程式碼會建立具有 100 像素的寬度和高度為 100 像素的縮圖影像。  
  
 下圖顯示的縮圖影像。  
  
 ![縮圖影像](./media/thumbnail1.png "Thumbnail1")  
  
> [!NOTE]
>  在此範例中，回呼方法已宣告但從未使用。 這可支援所有版本的 GDI +。  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。 若要執行此範例，請遵循下列步驟：  
  
1.  新建 Windows Forms 應用程式  
  
2.  將範例程式碼加入至表單。  
  
3.  建立表單的處理常式<xref:System.Windows.Forms.Control.Paint>事件  
  
4.  在 <xref:System.Windows.Forms.Control.Paint>處理常式中，呼叫`GetThumbnail`方法並傳遞`e`如<xref:System.Windows.Forms.PaintEventArgs>。  
  
5.  尋找您想要的縮圖的影像檔。  
  
6.  在 `GetThumbnail`方法指定的路徑和檔案加入至映像的名稱。  
  
7.  按 F5 執行範例。  
  
     100 x 100 的縮圖影像會出現在表單上。  
  
## <a name="see-also"></a>另請參閱
- [影像、點陣圖和中繼檔](images-bitmaps-and-metafiles.md)
- [使用影像、點陣圖、圖示和中繼檔](working-with-images-bitmaps-icons-and-metafiles.md)

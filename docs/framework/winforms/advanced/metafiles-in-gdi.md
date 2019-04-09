---
title: GDI+ 中的中繼檔
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], metafiles
- GDI+, metafiles
- metafiles
ms.assetid: 51da872c-c783-440f-8bf6-1e580a966c31
ms.openlocfilehash: bb972f158496192aa38f10564209bb2781837414
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119856"
---
# <a name="metafiles-in-gdi"></a>GDI+ 中的中繼檔
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供<xref:System.Drawing.Imaging.Metafile>類別，使您可以記錄並顯示中繼檔。 中繼檔，也稱為向量映像中，是儲存為一連串的繪圖命令和設定的映像。 命令和設定記錄在<xref:System.Drawing.Imaging.Metafile>可以儲存在記憶體中或儲存至檔案或資料流物件。  
  
## <a name="metafile-formats"></a>中繼檔格式  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 可以顯示已儲存在下列格式的中繼檔：  
  
-   Windows Metafile (WMF)  
  
-   加強型中繼檔 (EMF)   
  
-   EMF+  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] EMF 和 EMF + 格式中，但不是在 WMF 格式時，就可以記錄的中繼檔。  
  
 EMF + 是擴充功能，可讓 EMF[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]儲存的記錄。 有兩種變化 EMF + 格式：EMF + 只和 EMF + Dual。 EMF + 僅中繼檔只包含[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]記錄。 這類中繼檔可以藉由顯示[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]但不是[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]。 EMF + Dual 中繼檔包含[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]和[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]記錄。 每個[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]EMF + Dual 記錄中繼檔搭配替代[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]記錄。 這類中繼檔可以藉由顯示[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]或由[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]。  
  
 下列範例會顯示先前為檔案儲存在中繼檔。 在其左上角會顯示中繼檔 （100，100）。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>另請參閱

- [影像、點陣圖和中繼檔](images-bitmaps-and-metafiles.md)

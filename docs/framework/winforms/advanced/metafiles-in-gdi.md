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
ms.openlocfilehash: 73cacb7f701768b42121c31cfbc4f26905961231
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525086"
---
# <a name="metafiles-in-gdi"></a>GDI+ 中的中繼檔
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供<xref:System.Drawing.Imaging.Metafile>類別，因此您可以記錄，並顯示中繼檔。 中繼檔，也稱為向量映像，是儲存為一連串的繪圖命令和設定映像。 命令和設定記錄在<xref:System.Drawing.Imaging.Metafile>可以儲存在記憶體中或儲存到檔案或資料流物件。  
  
## <a name="metafile-formats"></a>中繼檔格式  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 可以顯示已儲存在下列格式的中繼檔：  
  
-   Windows 中繼檔 (WMF)  
  
-   加強型中繼檔 (EMF)   
  
-   EMF +  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] EMF 和 EMF + 格式，但不是在 WMF 格式，則可以錄製中繼檔。  
  
 EMF + 是擴充功能，可讓 EMF[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]来儲存的記錄。 有兩種變化 EMF + 格式： EMF + 只有和 EMF + 雙重。 EMF + 僅中繼檔只包含[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]記錄。 這類中繼檔可以顯示[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]不[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]。 EMF + 雙重中繼檔包含[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]和[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]記錄。 每個[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]記錄 EMF + 雙重中繼檔搭配替代[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]記錄。 這類中繼檔可以顯示[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]或[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]。  
  
 下列範例會顯示先前為檔案儲存在中繼檔。 中繼檔就會顯示在其左上角 （100，100）。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>另請參閱  
 [影像、點陣圖和中繼檔](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)

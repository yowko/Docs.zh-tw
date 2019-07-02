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
ms.openlocfilehash: df54289722cf12bad840722c6eafdaa43279a5dc
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504581"
---
# <a name="metafiles-in-gdi"></a>GDI+ 中的中繼檔
GDI + 提供<xref:System.Drawing.Imaging.Metafile>類別，使您可以記錄並顯示中繼檔。 中繼檔，也稱為向量映像中，是儲存為一連串的繪圖命令和設定的映像。 命令和設定記錄在<xref:System.Drawing.Imaging.Metafile>可以儲存在記憶體中或儲存至檔案或資料流物件。  
  
## <a name="metafile-formats"></a>中繼檔格式  
 GDI + 可以顯示已儲存在下列格式的中繼檔：  
  
- Windows Metafile (WMF)  
  
- 加強型中繼檔 (EMF)  
  
- EMF+  
  
 GDI + 可以記錄的中繼檔的 EMF 和 EMF + 格式，但不是在 WMF 格式。  
  
 EMF + 是允許 GDI + 記錄来儲存的 EMF 的擴充功能。 有兩種變化 EMF + 格式：EMF + 只和 EMF + Dual。 EMF + 僅中繼檔僅包含 GDI + 記錄。 這類中繼檔可以在 GDI + 中，但不是由 GDI 顯示。 EMF + Dual 中繼檔含有 GDI + 和 GDI 記錄。 EMF + Dual 中繼檔中的每個 GDI + 記錄會與替代的 GDI 記錄配對。 GDI 或 GDI + 時，會顯示這類中繼檔。  
  
 下列範例會顯示先前為檔案儲存在中繼檔。 在其左上角會顯示中繼檔 （100，100）。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>另請參閱

- [影像、點陣圖和中繼檔](images-bitmaps-and-metafiles.md)

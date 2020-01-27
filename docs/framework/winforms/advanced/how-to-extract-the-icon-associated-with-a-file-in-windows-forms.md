---
title: 如何：解壓縮與檔案相關聯的圖示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: 28769144b0e1c631a31c3c541747a6215f861d0e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742537"
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a>如何：擷取與 Windows Form 中檔案相關的圖示
許多檔案都有內嵌的圖示，可提供相關聯檔案類型的視覺標記法。 例如，Microsoft Word 檔包含將其識別為 Word 檔的圖示。 在清單控制項或表格控制項中顯示檔案時，您可能會想要顯示代表每個檔案名旁邊之檔案類型的圖示。 您可以使用 <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> 方法輕鬆地執行這項操作。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何將與檔案相關聯的圖示解壓縮，並在 <xref:System.Windows.Forms.ListView> 控制項中顯示檔案名和其相關聯的圖示。  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要編譯範例：  
  
- 將上述程式碼貼入 Windows Form，並從表單的函式或 <xref:System.Windows.Forms.Form.Load> 事件處理方法呼叫 `ExtractAssociatedIconExample` 方法。  
  
     您必須確定表單會匯入 <xref:System.IO> 命名空間。  
  
## <a name="see-also"></a>請參閱

- [影像、點陣圖和中繼檔](images-bitmaps-and-metafiles.md)
- [ListView 控制項](../controls/listview-control-windows-forms.md)

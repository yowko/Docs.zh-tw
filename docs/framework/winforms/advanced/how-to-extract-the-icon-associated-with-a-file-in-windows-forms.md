---
title: HOW TO：擷取與 Windows Forms 中檔案相關的圖示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: d754dc5e8a57b3c4e2e5439bb2524a22d44813c6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59112550"
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a>HOW TO：擷取與 Windows Forms 中檔案相關的圖示
許多檔案有內嵌提供相關聯的檔案類型的視覺表示法的圖示。 比方說，Microsoft Word 文件會包含其識別為 Word 文件的圖示。 當清單控制項或資料表控制項中顯示的檔案，您可能想要顯示代表每個檔案名稱旁邊的檔案類型的圖示。 您可以輕鬆地使用<xref:System.Drawing.Icon.ExtractAssociatedIcon%2A>方法。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何擷取與檔案相關聯的圖示，並顯示檔案名稱和其相關聯的圖示中<xref:System.Windows.Forms.ListView>控制項。  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要編譯範例：  
  
-   將上述程式碼貼到 Windows Form，並呼叫`ExtractAssociatedIconExample`從表單的建構函式的方法或<xref:System.Windows.Forms.Form.Load>事件處理方法。  
  
     您必須先確定您的表單匯入<xref:System.IO>命名空間。  
  
## <a name="see-also"></a>另請參閱

- [影像、點陣圖和中繼檔](images-bitmaps-and-metafiles.md)
- [ListView 控制項](../controls/listview-control-windows-forms.md)

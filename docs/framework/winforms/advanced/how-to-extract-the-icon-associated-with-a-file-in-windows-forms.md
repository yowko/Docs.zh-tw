---
title: 如何：擷取與 Windows Form 中檔案相關的圖示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: 21bce2f630649afb59272362a7f40055855ed512
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a>如何：擷取與 Windows Form 中檔案相關的圖示
許多檔案都已內嵌提供相關聯的檔案類型的視覺表示法的圖示。 例如，Microsoft Word 文件包含它們識別為 Word 文件的圖示。 當清單控制項或資料表控制項中顯示檔案，您可能要顯示的檔案類型，每個檔案名稱旁邊的圖示。 您可以輕鬆地使用<xref:System.Drawing.Icon.ExtractAssociatedIcon%2A>方法。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何擷取與檔案相關聯的圖示，並顯示檔案名稱和其相關聯的圖示中<xref:System.Windows.Forms.ListView>控制項。  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要編譯範例：  
  
-   將上述程式碼貼到 Windows Form 和呼叫`ExtractAssociatedIconExample`從表單的建構函式的方法或<xref:System.Windows.Forms.Form.Load>事件處理方法。  
  
     您必須先確定您的表單匯入<xref:System.IO>命名空間。  
  
## <a name="see-also"></a>另請參閱  
 [影像、點陣圖和中繼檔](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [ListView 控制項](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)

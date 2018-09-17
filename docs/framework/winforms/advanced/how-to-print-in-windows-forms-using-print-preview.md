---
title: 如何：使用預覽列印在 Windows Form 中進行列印
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
ms.openlocfilehash: ff113b3abfb8363e65d7ccb101973b6821d97262
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45698191"
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a>如何：使用預覽列印在 Windows Form 中進行列印
這在 Windows Forms 程式設計中很常見，除了列印服務，還提供預覽列印。 若要將預覽列印服務加入您的應用程式，有一個簡單的方法，那就是使用 <xref:System.Windows.Forms.PrintPreviewDialog> 控制項結合 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件處理邏輯來列印檔案。  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a>使用 PrintPreviewDialog 控制項來預覽文字文件  
  
1.  將 <xref:System.Windows.Forms.PrintPreviewDialog>、 <xref:System.Drawing.Printing.PrintDocument>和兩個字串加入您的表單。  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2.  將 <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> 屬性設定為您想要列印的文件，開啟文件，並將文件內容讀取至您之前加入的字串。  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3.  就像平常在列印文件一樣，在 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件處理常式中，使用 <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> 類別的 <xref:System.Drawing.Printing.PrintPageEventArgs> 屬性以及檔案內容來計算每一頁的行數，並轉譯文件的內容。 在繪製每一頁之後，請檢查該頁面是否為最後一頁，並且據此設定 <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> 的 <xref:System.Drawing.Printing.PrintPageEventArgs> 屬性。 在 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 成為 <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> 之前，會持續引發 `false`事件。 當文件已完成轉譯時，重設要轉譯的字串。 此外，也請確定 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件與其事件處理方法相關聯。  
  
    > [!NOTE]
    >  如果您已經在應用程式中實作列印，可能已經完成步驟 2 和 3。  
  
     在下列程式碼範例中，會使用事件處理常式，以表單上使用的相同字型來列印 "testPage.txt" 檔案。  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4.  將 <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> 控制項的 <xref:System.Windows.Forms.PrintPreviewDialog> 屬性設為表單上的 <xref:System.Drawing.Printing.PrintDocument> 元件。  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5.  在 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 控制項上呼叫 <xref:System.Windows.Forms.PrintPreviewDialog> 方法。 您通常會從按鈕的 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 事件處理方法來呼叫 <xref:System.Windows.Forms.Control.Click> 。 呼叫 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 會引發 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件，並將輸出轉譯至 <xref:System.Windows.Forms.PrintPreviewDialog> 控制項。 當使用者按一下對話方塊中的列印圖示，就會再引發一次 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件，將輸出傳送至印表機，而不是預覽對話方塊。 這就是為什麼在步驟 3 中轉譯程序的最後會重設字串的原因。  
  
     下列程式碼範例顯示針對表單上的按鈕所使用的 <xref:System.Windows.Forms.Control.Click> 事件處理方法。 這個事件處理方法會呼叫方法來讀取文件，並顯示預覽列印對話方塊。  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System、System.Windows.Forms、System.Drawing 組件的參考。  
  
-   Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Forms 程式碼範例](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## <a name="see-also"></a>另請參閱  
 [如何：在 Windows Forms 中列印多頁文字檔](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 [Windows Forms 列印支援](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [Windows Forms 中更安全的列印](../../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)

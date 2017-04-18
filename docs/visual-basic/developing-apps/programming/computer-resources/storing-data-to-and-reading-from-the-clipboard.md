---
title: "在剪貼簿儲存和讀取資料 (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a8580acf6fd23f9de264d3fed47d268898d498a6
ms.lasthandoff: 03/13/2017

---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a>在剪貼簿儲存和讀取資料 (Visual Basic)
剪貼簿可以用來儲存資料，例如文字和影像。 因為所有使用中處理序都共用剪貼簿，所以可以使用它在這兩者之間傳輸資料。 `My.Computer.Clipboard` 物件可讓您輕鬆地存取剪貼簿，以及讀取和寫入它。  
  
## <a name="reading-from-the-clipboard"></a>從剪貼簿讀取  
 使用 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> 方法來讀取剪貼簿中的文字。 下列程式碼會讀取文字，並將它顯示在訊息方塊中。 必須要有文字儲存在剪貼簿上，範例才能正確執行。  
  
 [!code-vb[VbVbcnMyClipboard#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_1.vb)]  
  
 這個程式碼範例也可作為 IntelliSense 程式碼片段。 在程式碼片段選擇器中，它位於 [Windows Forms 應用程式] > [剪貼簿]**** 中。 如需詳細資訊，請參閱[程式碼片段](https://docs.microsoft.com/visualstudio/ide/code-snippets)。  
  
 使用 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> 方法來擷取剪貼簿中的影像。 這個範例會先確認剪貼簿上是否有影像，再擷取它，並將它指派給 `PictureBox1`。  
  
 [!code-vb[VbResourceTasks#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_2.vb)]  
  
 這個程式碼範例也可作為 IntelliSense 程式碼片段。 在程式碼片段選擇器中，它位於 [Windows Forms 應用程式] > [剪貼簿]**** 中。如需詳細資訊，請參閱[程式碼片段](https://docs.microsoft.com/visualstudio/ide/code-snippets)。  
  
 即使在關閉應用程式之後，還是會保留放在剪貼簿上的項目。  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a>判斷儲存在剪貼簿中的檔案類型  
 剪貼簿上的資料可能會有數種不同的格式，例如文字、音訊檔或影像。 若要判斷哪一種檔案位於剪貼簿上，您可以使用 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>、<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>、<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A> 和 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A> 這類方法。 如果您有想要檢查的自訂格式，則可以使用 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> 方法。  
  
 使用 `ContainsImage` 函式來判斷剪貼簿上所包含的資料是否為影像。 下列程式碼會確認資料是否為影像，並據此進行報告。  
  
 [!code-vb[VbResourceTasks#13](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_3.vb)]  
  
## <a name="clearing-the-clipboard"></a>清除剪貼簿  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> 方法會清除剪貼簿。 因為其他處理序會共用剪貼簿，所以清除它可能會影響這些處理序。  
  
 下列程式碼將示範如何使用 `Clear` 方法。  
  
 [!code-vb[VbVbcnMyClipboard#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_4.vb)]  
  
## <a name="writing-to-the-clipboard"></a>寫入至剪貼簿  
 使用 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> 方法，將文字寫入至剪貼簿。 下列程式碼會將 "This is a test string" 字串寫入至剪貼簿。  
  
 [!code-vb[VbVbcnMyClipboard#1](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_5.vb)]  
  
 `SetText` 方法可以接受的格式參數包含 <xref:System.Windows.Forms.TextDataFormat> 的類型。 下列程式碼會以 RTF 文字將 "This is a test string" 字串寫入至剪貼簿。  
  
 [!code-vb[VbVbcnMyClipboard#2](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_6.vb)]  
  
 使用 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> 方法，將資料寫入至剪貼簿。 這個範例會以自訂格式 `specialFormat`，將 `DataObject``dataChunk` 寫入至剪貼簿。  
  
 [!code-vb[VbVbcnMyClipboard#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_7.vb)]  
  
 使用 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> 方法，將音訊資料寫入至剪貼簿。 這個範例會建立位元組陣列 `musicReader`，並在其中讀入檔案 `cool.wav`，然後將其寫入至剪貼簿。  
  
 [!code-vb[VbResourceTasks#5](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_8.vb)]  
  
> [!IMPORTANT]
>  因為其他使用者可以存取剪貼簿，所以請不要使用它來儲存機密資訊，例如密碼或機密資料。  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>   
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>   
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>   
 [如何：從 XML 檔案讀取物件資料](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)   
 [如何：將物件資料寫入 XML 檔案](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)

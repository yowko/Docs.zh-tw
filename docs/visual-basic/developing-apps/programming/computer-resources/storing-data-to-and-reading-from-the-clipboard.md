---
title: "Storing Data to and Reading from the Clipboard (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Clipboard, storing data to (My.Computer.Clipboard)"
  - "Clipboard, reading from (My.Computer.Clipboard)"
  - "Clipboard"
  - "My.Computer.Clipboard object, tasks"
  - "data [Visual Basic], Clipboard"
  - "reading data, from Clipboard"
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Storing Data to and Reading from the Clipboard (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

剪貼簿可以用來存放資料，例如文字和影像。  因為所有使用中處理序都共用剪貼簿，所以剪貼簿可用於在它們之間傳輸資料。  `My.Computer.Clipboard`物件可讓您輕鬆地存取 \[剪貼簿，以及讀取或寫入它。  
  
## 讀取 \[剪貼簿\]  
 使用<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A>方法來讀取 \[剪貼簿\] 中的文字。  下列程式碼會讀取文字，並顯示於訊息方塊中。  必須有文字儲存在剪貼簿，範例才能正確地執行。  
  
 [!code-vb[VbVbcnMyClipboard#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_1.vb)]  
  
 這個程式碼範例也可做為 IntelliSense 程式碼片段。  在程式碼片段選擇器中，這個程式碼片段位於 \[**Windows Form 應用程式 \> 剪貼簿**\] 中。  如需詳細資訊，請參閱 [程式碼片段](/visual-studio/ide/code-snippets)。  
  
 使用 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> 方法，從剪貼簿擷取影像。  這個範例會先查看剪貼簿上是否有影像，然後再加以擷取並指派至  `PictureBox1`。  
  
 [!code-vb[VbResourceTasks#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_2.vb)]  
  
 這個程式碼範例也可做為 IntelliSense 程式碼片段。  在程式碼片段選擇器中，這個程式碼片段位於 \[**Windows Form 應用程式 \> 剪貼簿**\] 中。如需詳細資訊，請參閱 [程式碼片段](/visual-studio/ide/code-snippets)。  
  
 即使在應用程式關閉之後，仍會保存放在剪貼簿上的項目。  
  
## 判斷檔案儲存在剪貼簿中的型別  
 剪貼簿上的資料可以採用許多不同的形式，如文字、音訊檔或影像。  為了判斷剪貼簿上的是哪種檔案，您可以使用諸如 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>、<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>、<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A> 和 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A> 的方法。  如果具有您要檢查的自訂格式，則可使用 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> 方法。  
  
 使用 `ContainsImage` 函式，判斷剪貼簿上所含的資料是否為影像。  下列程式碼會查看資料是否為影像並根據實際狀況提出報告。  
  
 [!code-vb[VbResourceTasks#13](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_3.vb)]  
  
## 清除 \[剪貼簿\]  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> 方法會清除剪貼簿。  因為其他處理序 \(Process\) 會共用剪貼簿，所以清除剪貼簿可能會對那些處理序產生影響。  
  
 下列程式碼將示範如何使用 `Clear` 方法。  
  
 [!code-vb[VbVbcnMyClipboard#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_4.vb)]  
  
## 寫入 \[剪貼簿\]  
 使用 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> 方法，將文字寫入剪貼簿。  下列程式碼會將字串 "This is a test string" 寫入剪貼簿。  
  
 [!code-vb[VbVbcnMyClipboard#1](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_5.vb)]  
  
 `SetText`方法接受格式參數，其中包含一種<xref:System.Windows.Forms.TextDataFormat>。  下列程式碼會將字串 "This is a test string" 寫入剪貼簿成為 RTF 文字。  
  
 [!code-vb[VbVbcnMyClipboard#2](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_6.vb)]  
  
 使用 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> 方法，將資料寫入剪貼簿。  這個範例會以自訂格式 `specialFormat`，將 `DataObject` `dataChunk` 寫入剪貼簿。  
  
 [!code-vb[VbVbcnMyClipboard#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_7.vb)]  
  
 使用 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> 方法，將音訊資料寫入剪貼簿。  這個範例會建立位元組陣列 `musicReader`、讀取檔案 `cool.wav` 並放入其中，然後將它寫入剪貼簿。  
  
 [!code-vb[VbResourceTasks#5](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_8.vb)]  
  
> [!IMPORTANT]
>  因為其他使用者也可以存取剪貼簿，所以請勿使用剪貼簿存放敏感資訊，例如密碼或機密資料。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>   
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>   
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>   
 [如何：從 XML 檔案讀取物件資料](../Topic/How%20to:%20Read%20Object%20Data%20from%20an%20XML%20File%20\(C%23%20and%20Visual%20Basic\).md)   
 [如何：將物件資料寫入 XML 檔案](../Topic/How%20to:%20Write%20Object%20Data%20to%20an%20XML%20File%20\(C%23%20and%20Visual%20Basic\).md)
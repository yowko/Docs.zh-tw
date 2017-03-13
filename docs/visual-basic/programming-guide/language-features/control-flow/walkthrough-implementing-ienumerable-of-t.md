---
title: "Walkthrough: Implementing IEnumerable(Of T) in Visual Basic | Microsoft Docs"
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
  - "control flow [Visual Basic]"
  - "enumerable interfaces"
  - "loop structures, optimizing performance"
  - "control flow"
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Walkthrough: Implementing IEnumerable(Of T) in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

<xref:System.Collections.Generic.IEnumerable%601> 介面是由能夠一次一個項目傳回值序列的類別所實作。  一次傳回一個資料項目的優點是您不必將整組資料載入記憶體後才來使用資料，  而是只需使用足夠的記憶體從資料中載入單一項目即可。  實作 `IEnumerable(T)` 介面的類別可以和 `For Each` 迴圈或 LINQ 查詢搭配使用。  
  
 例如，試想一個應用程式，其必須讀取大型文字檔並從該檔案傳回每一行符合特定搜尋準則的文字。  此應用程式使用 LINQ 查詢，從檔案傳回符合指定準則的文字行。  為了使用 LINQ 查詢來查詢檔案內容，應用程式可以將檔案內容載入至陣列或集合。  但是將整個檔案載入至陣列或集合，將會使用遠超過實際所需的記憶體。  LINQ 查詢可以改用可列舉類別來查詢檔案內容，只傳回符合搜尋準則的值。  相較之下，只傳回少數相符值的查詢佔用的記憶體非常少。  
  
 您可以建立實作 <xref:System.Collections.Generic.IEnumerable%601> 介面的類別，將來源資料公開為可列舉的資料。  這個實作 `IEnumerable(T)` 介面的類別將需要另一個實作 <xref:System.Collections.Generic.IEnumerator%601> 介面的類別來逐一查看來源資料。  這兩個類別可讓您循序地將資料項目傳回做為特定型別。  
  
 在本逐步解說中，您將建立實作 `IEnumerable(Of String)` 介面的類別和實作 `IEnumerator(Of String)` 介面的類別，一次讀取一行文字檔。  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
## 建立可列舉的類別  
  
||  
|-|  
|若要建立可列舉類別專案|  
|1.  在 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中的 \[**檔案**\] 功能表上，指向 \[**新增**\] 然後按一下 \[**專案**\]。<br />2.  在 \[**新增專案**\] 對話方塊的 \[**專案類型**\] 窗格中，確定已選取 \[**Windows**\]。  選取 \[**範本**\] 窗格中的 \[**類別庫**\]。  在 \[**名稱**\] 方塊中，輸入 `StreamReaderEnumerable`，然後按一下 \[**確定**\]。  接著會出現新專案。<br />3.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 Class1.vb 檔，然後按一下 \[**重新命名**\]。  將檔案重新命名為 `StreamReaderEnumerable.vb`，並按下 ENTER。  重新命名檔案時也會將類別重新命名為 `StreamReaderEnumerable`。  這個類別會實作 `IEnumerable(Of String)` 介面。<br />4.  以滑鼠右鍵按一下 \[StreamReaderEnumerable\] 專案，然後指向 \[**新增**\]，再按一下 \[**新增項目**\]。  選取 \[**類別**\] 範本。  在 \[**名稱**\] 方塊中輸入 `StreamReaderEnumerator.vb`，再按一下 \[**確定**\]。|  
  
 此專案中的第一個類別是可列舉的類別，將會實作 `IEnumerable(Of String)` 介面。  這個泛型介面會實作 <xref:System.Collections.IEnumerable> 介面，並保證這個類別的消費者可以存取型別為 `String` 的值。  
  
||  
|-|  
|若要加入程式碼以實作 IEnumerable|  
|1.  開啟 StreamReaderEnumerable.vb 檔。<br />2.  在 `Public Class StreamReaderEnumerable` 的下一行輸入下列程式碼，並按下 ENTER。<br />     [!code-vb[VbVbalrIteratorWalkthrough#1](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_1.vb)]<br />     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會自動將 `IEnumerable(Of String)` 介面所需的成員填入類別。<br />3.  這個可列舉類別將會從文字檔一次讀取一行文字。  將下列程式碼加入至類別，以公開會接受檔案路徑做為輸入參數的公用建構函式。<br />     [!code-vb[VbVbalrIteratorWalkthrough#2](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_2.vb)]<br />4.  `IEnumerable(Of String)` 介面的這個 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> 方法實作將會傳回 `StreamReaderEnumerator` 類別的新執行個體。  `IEnumerable` 介面的 `GetEnumerator` 方法實作可以設定為 `Private`，因為您必須只公開 `IEnumerable(Of String)` 介面的成員。  請以下列程式碼取代 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 為 `GetEnumerator` 方法產生的程式碼。<br />     [!code-vb[VbVbalrIteratorWalkthrough#3](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_3.vb)]|  
  
||  
|-|  
|若要加入程式碼以實作 IEnumerator|  
|1.  開啟 StreamReaderEnumerator.vb 檔。<br />2.  在 `Public Class StreamReaderEnumerator` 的下一行輸入下列程式碼，並按下 ENTER。<br />     [!code-vb[VbVbalrIteratorWalkthrough#4](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_4.vb)]<br />     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會自動將 `IEnumerator(Of String)` 介面所需的成員填入類別。<br />3.  這個列舉程式類別會開啟文字檔，並執行檔案 I\/O 以讀取檔案中的文字行。  將下列程式碼加入至類別，以公開會接受檔案路徑做為輸入參數、而且會開啟文字檔進行讀取的公用建構函式。<br />     [!code-vb[VbVbalrIteratorWalkthrough#5](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_5.vb)]<br />4.  `IEnumerator(Of String)` 及 `IEnumerator` 介面的 `Current` 屬性都會從文字檔將目前項目傳回為 `String`。  `IEnumerator` 介面的 `Current` 屬性實作可以設定為 `Private`，因為您必須只公開 `IEnumerator(Of String)` 介面的成員。  請以下列程式碼取代 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 為 `Current` 屬性產生的程式碼。<br />     [!code-vb[VbVbalrIteratorWalkthrough#6](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_6.vb)]<br />5.  `IEnumerator` 介面的 `MoveNext` 方法會巡覽至文字檔中的下一個項目，並更新 `Current` 屬性傳回的值。  如果沒有其他要讀取的項目，`MoveNext` 方法會傳回 `False`，否則 `MoveNext` 方法會傳回 `True`。  將下列程式碼加入至 `MoveNext` 方法中。<br />     [!code-vb[VbVbalrIteratorWalkthrough#7](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_7.vb)]<br />6.  `IEnumerator` 介面的 `Reset` 方法會指示 Iterator 指向文字檔開頭並清除目前的項目值。  將下列程式碼加入至 `Reset` 方法中。<br />     [!code-vb[VbVbalrIteratorWalkthrough#8](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_8.vb)]<br />7.  `IEnumerator` 介面的 `Dispose` 方法保證會在終結 Iterator 之前釋放所有的 Unmanaged 資源。  `StreamReader` 物件使用的檔案控制代碼為 Unmanaged 資源，必須在終結 Iterator 執行個體之前關閉。  請以下列程式碼取代 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 為 `Dispose` 方法產生的程式碼。<br />     [!code-vb[VbVbalrIteratorWalkthrough#9](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_9.vb)]|  
  
## 使用範例 Iterator  
 您可以在程式碼中使用可列舉的類別並搭配實作 `IEnumerable` 之物件所需的控制結構 \(例如，`For Next` 迴圈或 LINQ 查詢\)。  下列範例示範 LINQ 查詢中的 `StreamReaderEnumerable`。  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_10.vb)]  
  
## 請參閱  
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [For Each...Next 陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
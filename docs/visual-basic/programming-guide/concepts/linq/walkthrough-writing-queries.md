---
title: "逐步解說：在 Visual Basic 中撰寫查詢 | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "查詢 [Visual Basic 中的 LINQ]，撰寫"
  - "LINQ [Visual Basic]，逐步解說"
  - "LINQ [Visual Basic]，撰寫查詢"
  - "撰寫 LINQ 查詢 [Visual Basic]"
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
caps.latest.revision: 70
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 68
---
# 逐步解說：在 Visual Basic 中撰寫查詢
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

本逐步解說示範如何使用 Visual Basic 語言功能來撰寫 [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext-md.md)] 查詢運算式。  其中會示範如何在 Student 物件清單上建立查詢、如何執行這些查詢，以及如何加以修改。  這些查詢加入了 Visual Basic 2008 的幾項新功能，包括物件初始設定式、區域型別推斷和匿名型別。  
  
 當您完成本逐步解說之後，便可繼續參閱您想了解的特定 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] 提供者的範例和文件。  [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] 提供者包括 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq-md.md)]、[!INCLUDE[linq_dataset](../../../../csharp/programming-guide/linq-query-expressions/includes/linq-dataset-md.md)] 和 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)]。  
  
## 建立專案  
  
#### 若要建立主控台應用程式專案  
  
1.  啟動 Visual Studio。  
  
2.  在 \[**檔案**\] 功能表上，指向 \[**新增**\]，然後按一下 \[**專案**\]。  
  
3.  按一下 \[**已安裝的範本**\] 清單中的 \[**Visual Basic**\]。  
  
4.  在專案類型清單中，按一下 \[**主控台應用程式**\]。  在 \[**名稱**\] 方塊中輸入專案的名稱，然後按一下 \[**確定**\]。  
  
     專案隨即建立。  根據預設，專案中包含 System.Core.dll 的參考。  另外，[專案設計工具，參考頁 \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic) 上的 \[**匯入的命名空間**\] 清單包含了 <xref:System.Linq?displayProperty=fullName> 命名空間。  
  
5.  在 [專案設計工具、編譯頁 \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic)中，確定 \[**Option Infer**\] 設定為 \[**在**\]。  
  
## 加入記憶體中資料來源  
 這個逐步解說中的查詢資料來源是一份 `Student` 物件清單。  每個 `Student` 物件的學生主體都包含名字、姓氏、年級和學術排名。  
  
#### 若要加入資料來源  
  
-   定義 `Student` 類別 \(Class\)，並建立這個類別的執行個體 \(Instance\) 清單。  
  
    > [!IMPORTANT]
    >  [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)提供了定義 `Student` 類別和建立這個逐步解說範例所用清單時所需的程式碼。  您可以將該處的複製程式碼複製並貼上至專案中。  新的程式碼會取代在建立專案時出現的程式碼。  
  
#### 若要將新的學生加入至學生清單  
  
-   依照 `getStudents` 方法中的模式，將另一個 `Student` 類別執行個體加入至清單。  加入學生時會導入物件初始設定式。  如需詳細資訊，請參閱[Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)。  
  
## 建立查詢  
 執行本節加入的查詢時，會產生學術排名在前十名的學生的清單。  因為查詢每次都會選取完整的 `Student` 物件，所以查詢結果的型別是 `IEnumerable(Of Student)`。  不過，在查詢定義中通常不會指定查詢型別。  相反地，編譯器 \(Compiler\) 會使用區域型別推斷來判斷型別。  如需詳細資訊，請參閱[Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。  查詢的範圍變數 `currentStudent` 會做為 `students` 來源中之每個 `Student` 執行個體的參考，可以用來存取 `students` 中之每個物件的屬性。  
  
#### 若要建立簡單的查詢  
  
1.  在專案的 `Main` 方法中找到具有下列標記的位置：  
  
     [!code-vb[VbLINQWalkthrough#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_1.vb)]  
  
     複製並貼上下列程式碼。  
  
     [!code-vb[VbLINQWalkthrough#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_2.vb)]  
  
2.  將滑鼠指標放在程式碼的 `studentQuery` 上，以確認編譯器指派的型別是 `IEnumerable(Of Student)`。  
  
## 執行查詢  
 `studentQuery` 變數包含的是查詢的定義，而不是執行查詢的結果。  執行查詢的機制通常是 `For Each` 迴圈 \(Loop\)。  在傳回的序列中，每個項目都是透過迴圈的反覆運算變數進行存取。  如需查詢執行的詳細資訊，請參閱[撰寫第一個 LINQ 查詢](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)。  
  
#### 若要執行查詢  
  
1.  在專案的查詢下方加入下列 `For Each` 迴圈。  
  
     [!code-vb[VbLINQWalkthrough#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_3.vb)]  
  
2.  將滑鼠指標放在迴圈的控制項變數 `studentRecord` 上，以查看其資料型別。  因為 `studentQuery` 會傳回 `Student` 執行個體的集合，所以 `studentRecord` 的型別會推斷為 `Student`。  
  
3.  按下 CTRL\+F5 以建置和執行應用程式。  請注意主控台視窗中的結果。  
  
## 修改查詢  
 如果查詢結果是根據指定的順序排列，則掃描查詢結果會比較容易。  您可以根據任何可用的欄位來排序傳回的序列。  
  
#### 若要排序結果  
  
1.  在查詢的 `Where` 陳述式與 `Select` 陳述式之間加入下列 `Order By` 子句。  `Order By` 子句會依據每個學生的姓氏，按照字母順序從 A 到 Z 排序結果。  
  
    ```  
    Order By currentStudent.Last Ascending   
    ```  
  
2.  若要先依照姓氏排序，再依照名字排序，請同時將這兩個欄位加入至查詢：  
  
    ```  
    Order By currentStudent.Last Ascending, currentStudent.First Ascending   
    ```  
  
     您也可以指定 `Descending`，以從 Z 到 A 進行排序。  
  
3.  按下 CTRL\+F5 以建置和執行應用程式。  請注意主控台視窗中的結果。  
  
#### 若要引入區域識別項  
  
1.  加入本節中的程式碼，以在查詢運算式中引入區域識別項。  區域識別項會保留中繼結果。  在下列範例中，`name` 這個識別項會保留學生名稱和姓氏的串連結果。  區域識別項的使用十分方便，也可以儲存運算式的結果，省去多次進行計算的需要，藉以提高效能。  
  
     [!code-vb[VbLINQWalkthrough#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_4.vb)]  
  
2.  按下 CTRL\+F5 以建置和執行應用程式。  請注意主控台視窗中的結果。  
  
#### 若要在 Select 子句中規劃一個欄位  
  
1.  加入本節中的查詢和 `For Each` 迴圈來建立查詢，以產生所含項目與來源中的項目不同的序列。  在下列範例中，來源是 `Student` 物件的集合，但是每個物件只會傳回一個成員：姓 Garcia 的學生的名字。  因為 `currentStudent.First` 是字串，所以 `studentQuery3` 所傳回序列的資料型別是 `IEnumerable(Of String)`，即字串的序列。  如先前的範例所示，指派給 `studentQuery3` 的資料型別會由編譯器使用區域型別推斷來決定。  
  
     [!code-vb[VbLINQWalkthrough#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_5.vb)]  
  
2.  將滑鼠指標放在程式碼的 `studentQuery3` 上，以確認指派的型別是 `IEnumerable(Of String)`。  
  
3.  按下 CTRL\+F5 以建置和執行應用程式。  請注意主控台視窗中的結果。  
  
#### 若要在 Select 子句中建立匿名型別  
  
1.  加入本節中的程式碼，以查看如何在查詢中使用匿名型別。  當您想要傳回資料來源中的數個欄位，而不是完整記錄 \(上一個範例中的 `currentStudent` 記錄\) 或單一欄位 \(上一節中的 `First`\)，就可以在查詢中使用匿名型別。  而不是定義新的具名輸入內含您在結果要包含的欄位，您可以指定欄位在 `Select` 子句，讓編譯器建立匿名型別並使用這些欄位的匿名型別做為它的屬性。如需詳細資訊，請參閱[Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
     下列範例建立的查詢會傳回學術排名在 1 與 10 之間的高年級生的姓名和排名，依學術排名進行排序。  在這個範例中，因為 `Select` 子句會傳回匿名型別的執行個體，而匿名型別是沒有名稱的，所以必須推斷 `studentQuery4` 的型別。  
  
     [!code-vb[VbLINQWalkthrough#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_6.vb)]  
  
2.  按下 CTRL\+F5 以建置和執行應用程式。  請注意主控台視窗中的結果。  
  
## 其他範例  
 現在您已了解基本概念，下面將列出其他範例，以說明 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] 查詢的彈性和強大威力。  每個範例的前面都會簡短說明該範例的用途。  放在的查詢結果變數的滑鼠指標放在每項查詢的檢視推斷的型別。使用 `For Each` 迴圈來產生結果。  
  
 [!code-vb[VbLINQWalkthrough#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_7.vb)]  
  
## 其他資訊  
 在您熟悉查詢的基本使用概念之後，便可開始閱讀您想了解之特定 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] 提供者類型的文件和範例：  
  
 [LINQ to Objects](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
  
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)  
  
 [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md)  
  
## 請參閱  
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Supplementary LINQ Resources](../Topic/Supplementary%20LINQ%20Resources.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)   
 [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)   
 [Walkthrough: Writing Queries in C\#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
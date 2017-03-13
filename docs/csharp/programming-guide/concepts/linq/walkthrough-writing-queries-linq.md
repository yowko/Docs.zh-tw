---
title: "Walkthrough: Writing Queries in C# (LINQ) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.topic: "get-started-article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "LINQ [C#], walkthroughs"
  - "LINQ [C#], writing queries"
  - "queries [LINQ in C#], writing"
  - "writing LINQ queries"
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
caps.latest.revision: 32
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 30
---
# Walkthrough: Writing Queries in C# (LINQ)
本逐步解說示範用來撰寫 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] 查詢運算式的 C\# 語言功能。  當您完成本逐步解說之後，便可繼續參閱您想了解的特定 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] 提供者 \(Provider\) 的範例和文件，例如 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq-md.md)]、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] to DataSet 或 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)]。  
  
## 必要條件  
 這個逐步解說需要在 Visual Studio 2008 中加入的功能。  
  
 ![視訊的連結](../../../../csharp/programming-guide/concepts/linq/media/playvideo.png "PlayVideo") 如需本主題的影片版本，請參閱[影片 HOW TO：在 C\# 中撰寫查詢 \(LINQ\)](http://go.microsoft.com/fwlink/?LinkId=100393) \(英文\)。  
  
## 建立 C\# 專案  
  
#### 若要建立專案  
  
1.  啟動 Visual Studio。  
  
2.  在功能表列上，選擇 \[**檔案**\]、\[**新增**\]、\[**專案**\]。  
  
     \[**新增專案**\] 對話方塊隨即開啟。  
  
3.  展開 \[**安裝**\]，展開 \[**範本**\]，展開 \[**Visual C\#**\]，然後選取 \[**主控台應用程式**\]。  
  
4.  在 \[**名稱**\] 文字方塊中，輸入不同的名稱或接受預設名稱，然後選擇 \[**OK**\] 按鈕。  
  
     新專案即會出現於 \[**方案總管**\] 中。  
  
5.  請注意，您的專案具有 System.Core.dll 參考，以及 <xref:System.Linq?displayProperty=fullName> 命名空間的 `using` 指示詞。  
  
## 建立記憶體中資料來源  
 查詢的資料來源是一份簡單的 `Student` 物件清單。  每一筆 `Student` 記錄都有名字、姓氏，以及代表學生考試分數的整數陣列。  請將這段程式碼複製到您的專案，  並注意下列特性：  
  
-   `Student` 類別是由自動實作的屬性組成。  
  
-   清單中的每個學生都是使用物件初始設定式來初始化。  
  
-   清單本身是使用集合初始設定式來初始化。  
  
 這套完整的資料結構將在不會明確呼叫任何建構函式或明確成員存取的情況下進行初始化和具現化。  如需這些新功能的詳細資訊，請參閱[自動實作的屬性](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) 和[物件和集合初始設定式](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)。  
  
#### 若要加入資料來源  
  
-   將 `Student` 類別和已初始化的學生名單加入至專案中的 `Program` 類別。  
  
     [!code-cs[CsLinqGettingStarted#11](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_1.cs)]  
  
#### 若要將新 Student 加入至 Students 清單  
  
1.  將新的 `Student` 加入至 `Students` 清單，並使用您選擇的名稱和考試分數。  請嘗試輸入所有的新學生資訊，以深入了解物件初始設定式的語法。  
  
## 建立查詢  
  
#### 若要建立簡單的查詢  
  
-   在應用程式的 `Main` 方法中建立簡單的查詢，此查詢會在執行後產生一份學生名單，列出第一次考試分數高於 90 分的學生。  請注意，因為選取的是整個 `Student` 物件，所以查詢的型別是 `IEnumerable<Student>`。  雖然程式碼也可以透過 [var](../../../../csharp/language-reference/keywords/var.md) 關鍵字使用隱含型別，但是這裡會使用明確型別清楚說明結果   \(如需 `var` 的詳細資訊，請參閱[隱含類型區域變數](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)\)。  
  
     請注意，查詢的範圍變數 `student` 是做為來源中各個 `Student` 的參考，以提供每個物件的成員存取權。  
  
 [!code-cs[CsLINQGettingStarted#12](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_2.cs)]  
  
## 執行查詢  
  
#### 若要執行查詢  
  
1.  現在，請撰寫可以讓查詢開始執行的 `foreach` 迴圈。  請注意與程式碼有關的下列事項：  
  
    -   傳回的序列中，每個項目都是透過 `foreach` 迴圈中的反覆運算變數來存取。  
  
    -   這個變數的型別是 `Student`，而查詢變數的型別則是相容的 `IEnumerable<Student>`。  
  
2.  在您加入這段程式碼之後，請按 Ctrl \+ F5 以建置並執行應用程式，並在 \[**主控台**\] 視窗中查看結果。  
  
 [!code-cs[CsLINQGettingStarted#13](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_3.cs)]  
  
#### 若要加入其他篩選條件  
  
1.  您可以在 `where` 子句中合併多個布林值條件，進一步限定查詢範圍。  下列程式碼會加入條件，讓查詢傳回第一次分數高於 90 分和最後一次成績低於 80 分的學生。  `where` 子句應該與下列程式碼類似。  
  
    ```  
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     如需詳細資訊，請參閱[where 子句](../../../../csharp/language-reference/keywords/where-clause.md)。  
  
## 修改查詢  
  
#### 若要排序結果  
  
1.  當結果按照某種順序排列時，會比較好瀏覽。  您可以依照來源項目中可供存取的任何欄位來排序傳回的序列。  例如，下列 `orderby` 子句是依據每個學生的姓氏，按照字母順序由 A 到 Z 排序結果。  請緊接著 `where` 陳述式後面以及 `select` 陳述式前面，將下列 `orderby` 子句加入到您的查詢中：  
  
    ```  
    orderby student.Last ascending  
    ```  
  
2.  現在，請變更 `orderby` 子句，讓它根據第一次考試的分數，按照由分數最高到最低的相反順序來排序結果。  
  
    ```  
    orderby student.Scores[0] descending  
    ```  
  
3.  變更 `WriteLine` 格式字串，以便您檢視分數。  
  
    ```  
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     如需詳細資訊，請參閱[orderby 子句](../../../../csharp/language-reference/keywords/orderby-clause.md)。  
  
#### 若要將結果分組  
  
1.  群組是查詢運算式中非常強大的一項功能。  內含 group 子句的查詢會產生群組序列，而且每個群組本身都包含 `Key`，以及由該群組所有成員組成的序列。  下面的新查詢使用學生姓氏的第一個字母當做索引鍵，將學生分組。  
  
     [!code-cs[CsLINQGettingStarted#14](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_4.cs)]  
  
2.  請注意，查詢的型別現在已經變更。  它現在會產生使用 `char` 型別做為索引鍵的群組序列，以及 `Student` 物件的序列。  由於查詢的型別已經變更，因此下列程式碼也會變更 `foreach` 執行迴圈：  
  
     [!code-cs[CsLINQGettingStarted#15](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_5.cs)]  
  
3.  按 Ctrl \+ F5 執行應用程式，並於 \[**主控台**\] 視窗檢視結果。  
  
     如需詳細資訊，請參閱[group 子句](../../../../csharp/language-reference/keywords/group-clause.md)。  
  
#### 若要讓變數變成隱含型別  
  
1.  明確撰寫 `IGroupings` 的 `IEnumerables` 程式碼可能很快就會變得非常瑣碎無聊。  這時候，您可以改用 `var`，以更便利的方式撰寫相同的查詢和 `foreach` 迴圈。  `var` 關鍵字不會變更物件的型別，只會指示編譯器推斷型別。  變更 `studentQuery` 的型別和反覆運算變數 `group`到 `var` 並重新執行查詢。  請注意，在內部 `foreach` 迴圈中，反覆運算變數的型別仍然是 `Student`，而且查詢的運作方式也和以前完全一樣。  請將 `s` 反覆運算變數變更為 `var`，然後重新執行查詢。  您將取得完全相同的結果。  
  
     [!code-cs[CsLINQGettingStarted#16](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_6.cs)]  
  
     如需 [var](../../../../csharp/language-reference/keywords/var.md) 的詳細資訊，請參閱 [隱含類型區域變數](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)。  
  
#### 若要依索引鍵值排序群組  
  
1.  執行前述查詢時，您應該會注意到群組並未依字母順序排列。  如果要變更這個狀況，您必須在 `group` 子句後面提供 `orderby` 子句。  但是您必須先取得識別項做為 `group` 子句所建立之群組的參考，才能使用 `orderby` 子句。  請使用 `into` 關鍵字提供這個識別項，如下所示：  
  
     [!code-cs[csLINQGettingStarted#17](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_7.cs)]  
  
     執行這項查詢時，您會發現群組現在已經按照字母順序排序。  
  
#### 若要使用 let 引入識別項  
  
1.  您可以使用 `let` 關鍵字，在查詢運算式中引入任何運算式結果的識別項。  如下列範例所示，這個識別項十分方便，它也可以儲存運算式的結果，如此一來就不需要進行多次計算，藉以提高效能。  
  
     [!code-cs[csLINQGettingStarted#18](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_8.cs)]  
  
     如需詳細資訊，請參閱[let 子句](../../../../csharp/language-reference/keywords/let-clause.md)。  
  
#### 若要在查詢運算式中使用方法語法  
  
1.  如[Query Syntax and Method Syntax in LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md) 所述，某些查詢作業只能使用方法語法來表示。  下列程式碼範例會計算來源序列中每個 `Student` 的總分數，然後對該項查詢的結果呼叫 `Average()` 方法，以計算該班級的平均分數。  請注意查詢運算式前後的括號位置。  
  
     [!code-cs[csLINQGettingStarted#19](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_9.cs)]  
  
#### 若要在 select 子句中進行轉換或投影  
  
1.  在查詢所產生的序列中，其項目經常與來源序列中的項目不同。  請刪除先前的查詢和執行迴圈標記或為它們加上註解，然後使用下列程式碼取代。  請注意，查詢會傳回字串序列 \(不是 `Students`\)，而且 `foreach` 迴圈中也會反映這個情況。  
  
     [!code-cs[csLINQGettingStarted#20](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_10.cs)]  
  
2.  本逐步解說前面的程式碼指出班級平均成績約為 334 分。  若要產生總分數高於班級平均的 `Students` 序列以及其 `Student ID`，您可以在 `select` 陳述式中使用匿名型別：  
  
     [!code-cs[csLINQGettingStarted#21](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_11.cs)]  
  
## 後續步驟  
 在您熟悉於 C\# 中使用查詢的基本概念之後，便可開始閱讀您想了解的特定 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] 提供者類型的文件和範例。  
  
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)  
  
 [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md)  
  
 [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [LINQ to Objects](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
  
## 請參閱  
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [Getting Started with LINQ in C\#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [LINQ 查詢運算式](../../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Supplementary LINQ Resources](../Topic/Supplementary%20LINQ%20Resources.md)   
 [逐步解說：在 Visual Basic 中撰寫查詢](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)
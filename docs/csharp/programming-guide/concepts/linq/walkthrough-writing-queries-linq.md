---
title: "逐步解說：在 C# 中撰寫查詢 (LINQ) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: get-started-article
dev_langs:
- CSharp
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
caps.latest.revision: 32
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 5692bd4b2fae4c5e17d48c12e98eb2e18523ba61
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---
# <a name="walkthrough-writing-queries-in-c-linq"></a>逐步解說：在 C# 中撰寫查詢 (LINQ)
本逐步解說示範用以撰寫 LINQ 查詢運算式的 C# 語言功能。  
  
## <a name="create-a-c-project"></a>建立 C# 專案  
  
> [!NOTE]
>  下列指示適用於 Visual Studio。 如果您使用不同的開發環境，可搭配 System.Core.dll 的參考和 <xref:System.Linq?displayProperty=fullName> 命名空間的 `using` 指示詞來建立主控台專案。  
  
#### <a name="to-create-a-project-in-visual-studio"></a>若要在 Visual Studio 中建立專案  
  
1.  啟動 Visual Studio。  
  
2.  在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。  
  
     [ **新增專案** ] 對話方塊隨即開啟。  
  
3.  依序展開 [已安裝]、[範本] 和 [Visual C#]，然後選擇 [主控台應用程式]。  
  
4.  在 [名稱] 文字方塊中，輸入不同的名稱或接受預設名稱，然後按一下 [確定] 按鈕。  
  
     新的專案隨即會出現在方案總管中。  
  
5.  您會發現專案具有 System.Core.dll 的參考和 <xref:System.Linq?displayProperty=fullName> 命名空間的 `using` 指示詞。  
  
## <a name="create-an-in-memory-data-source"></a>建立記憶體內部資料來源  
 查詢的資料來源是 `Student` 物件的簡單清單。 每個 `Student` 記錄都有名字、姓氏和整數的陣列，表示其在班級上的測驗分數。 將此程式碼複製到您的專案中。 並注意下列特性：  
  
-   `Student` 類別是由自動實作的屬性所組成。  
  
-   使用物件初始設定式，初始化清單中的每一位學生。  
  
-   系統會使用集合初始設定式，來初始化清單本身。  
  
 系統會初始化整個資料結構，並將其具現化，而不需要明確呼叫任何建構函式，亦不需明確的成員存取。 如需這些新功能的詳細資訊，請參閱[自動實作的屬性](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)以及[物件和集合初始設定式](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)。  
  
#### <a name="to-add-the-data-source"></a>若要新增資料來源  
  
-   將 `Student` 類別和學生的初始化清單，新增至專案中的 `Program` 類別。  
  
     [!code-cs[CsLinqGettingStarted#11](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_1.cs)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>若要將新的學生新增至學生清單  
  
1.  將新的 `Student` 新增至 `Students` 清單，並使用您所選擇的名稱和測驗分數。 請嘗試輸入新的學生資訊，以便進一步了解物件初始設定式語法。  
  
## <a name="create-the-query"></a>建立查詢  
  
#### <a name="to-create-a-simple-query"></a>建立簡單查詢  
  
-   在應用程式的 `Main` 方法中，建立簡單的查詢，即可在執行查詢時產生第一次測驗分數超過 90 分之所有學生的清單。 請注意，因為已選取整個 `Student` 物件，所以查詢的類型是 `IEnumerable<Student>`。 雖然程式碼也可以藉由 [var](../../../../csharp/language-reference/keywords/var.md) 關鍵字來使用隱含類型，但需使用明確類型來清楚說明結果  (如需 `var` 的詳細資訊，請參閱[隱含類型區域變數](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md))。  
  
     另請注意，查詢的範圍變數 `student` 可作為來源中每個 `Student` 的參考，並提供每個物件的成員存取。  
  
 [!code-cs[CsLINQGettingStarted#12](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_2.cs)]  
  
## <a name="execute-the-query"></a>執行查詢  
  
#### <a name="to-execute-the-query"></a>查詢查詢  
  
1.  現在，請撰寫 `foreach` 迴圈以執行查詢。 請注意下列程式碼的相關重點：  
  
    -   您可透過 `foreach` 迴圈中的反覆運算變數，存取傳回序列中的每個項目。  
  
    -   此變數的類型是 `Student`，其與 `IEnumerable<Student>` 查詢變數類型相容。  
  
2.  加入此程式碼之後，建置並執行應用程式，即可在 [主控台] 視窗中查看結果。  
  
 [!code-cs[CsLINQGettingStarted#13](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_3.cs)]  
  
#### <a name="to-add-another-filter-condition"></a>若要新增其他篩選條件  
  
1.  您可以在 `where` 中結合多個布林條件，以進一步精簡查詢子句。 下列程式碼會新增條件，讓查詢傳回第一次分數高於 90 分，但最後一次的分數低於 80 分的學生。 `where` 子句應類似於下列程式碼。  
  
    ```  
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     如需詳細資訊，請參閱 [where 子句](../../../../csharp/language-reference/keywords/where-clause.md)。  
  
## <a name="modify-the-query"></a>修改查詢  
  
#### <a name="to-order-the-results"></a>若要排序結果  
  
1.  如果結果有依照某種順序排列，會比較容易進行掃描。 您可以依據來源項目中任何可存取的欄位，來排序傳回的序列。 例如，下列 `orderby` 子句會根據每個學生的姓氏，依字母 A 到 Z 順序，來排序結果。 請在 `where` 陳述式正後方、`select` 陳述式正前方，將下列 `orderby` 子句新增至查詢：  
  
    ```  
    orderby student.Last ascending  
    ```  
  
2.  現在，變更 `orderby` 子句，以根據第一個測驗，依最低分到最高分的相反順序來排序結果。  
  
    ```  
    orderby student.Scores[0] descending  
    ```  
  
3.  變更 `WriteLine` 格式字串，以便查看分數：  
  
    ```  
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     如需詳細資訊，請參閱 [orderby 子句](../../../../csharp/language-reference/keywords/orderby-clause.md)。  
  
#### <a name="to-group-the-results"></a>若要將結果分組  
  
1.  查詢運算式中提供分組這項強大的功能。 使用 group 子句進行查詢時，會產生一個群組序列，且每個群組本身會包含 `Key` 以及組成該群組之所有成員的序列。 下列新查詢會以學生姓氏的第一個字母作為索引鍵，來進行分組。  
  
     [!code-cs[CsLINQGettingStarted#14](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_4.cs)]  
  
2.  請注意，查詢類型現在已變更。 現在，即會產生具有 `char` 類型索引鍵的群組序列，以及 `Student` 物件的序列。 由於查詢類型已變更，因此下列程式碼也會變更 `foreach` 執行迴圈：  
  
     [!code-cs[CsLINQGettingStarted#15](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_5.cs)]  
  
3.  執行應用程式，並在 [主控台] 視窗中檢視結果。  
  
     如需詳細資訊，請參閱 [group 子句](../../../../csharp/language-reference/keywords/group-clause.md)。  
  
#### <a name="to-make-the-variables-implicitly-typed"></a>若要將變數設為隱含類型  
  
1.  在明確撰寫 `IGroupings` 的 `IEnumerables` 程式碼時，可能很快就會感到枯燥乏味。 為了方便起見，您可以使用 `var` 來撰寫相同的查詢和 `foreach` 迴圈。 `var` 關鍵字不會變更物件的類型，而只會指示編譯器推斷類型。 將 `studentQuery` 類型和反覆運算變數 `group` 變更為 `var`，然後重新執行查詢。 請注意，在內部 `foreach` 迴圈中，反覆運算變數類型仍為 `Student`，查詢亦會如往常般運作。 將 `s` 反覆運算變數變更為 `var`，然後再次執行查詢。 您會發現結果完全相同。  
  
     [!code-cs[CsLINQGettingStarted#16](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_6.cs)]  
  
     如需 [var](../../../../csharp/language-reference/keywords/var.md) 的詳細資訊，請參閱[隱含類型區域變數](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)。  
  
#### <a name="to-order-the-groups-by-their-key-value"></a>若要依索引鍵值排序群組  
  
1.  當您執行上述查詢時，您會發現群組不是依字母順序排列。 若要變更這種情況，您必須在 `group` 子句之後提供 `orderby` 子句。 不過，若要使用 `orderby` 子句，您必須先取得識別項，以作為 `group` 子句所建立的群組參考。 您可以使用 `into` 關鍵字來提供識別項，如下所示：  
  
     [!code-cs[csLINQGettingStarted#17](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_7.cs)]  
  
     在您執行此查詢時，會發現群組現已依照字母順序排列。  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a>若要使用 let 引進識別項  
  
1.  針對查詢運算式中的任何運算式結果，您可以使用 `let` 關鍵字引進識別項。 如下列範例所示，此識別項非常方便，它也可以儲存運算式的結果，而不需進行多次計算，藉此提高效能。  
  
     [!code-cs[csLINQGettingStarted#18](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_8.cs)]  
  
     如需詳細資訊，請參閱 [let 子句](../../../../csharp/language-reference/keywords/let-clause.md)。  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a>若要在查詢運算式中使用方法語法  
  
1.  如 [LINQ 中的查詢語法及方法語法](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)中所述，某些查詢作業只能使用方法語法來表示。 下列程式碼會針對來源序列中的每個 `Student` 計算總分，然後在該查詢結果上呼叫 `Average()` 方法以計算班級的平均分數。 請注意查詢運算式前後的括弧位置。  
  
     [!code-cs[csLINQGettingStarted#19](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_9.cs)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a>若要在 select 子句中轉換或投影  
  
1.  這是一種非常普遍的查詢，產生的序列項目與來源序列中的項目不同。 刪除或註解您先前的查詢和執行迴圈，並將其取代為下列程式碼。 請注意，查詢會傳回一個字串序列 (而不是 `Students`)，且這項事實會反映在 `foreach` 迴圈中。  
  
     [!code-cs[csLINQGettingStarted#20](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_10.cs)]  
  
2.  此逐步解說中稍早的程式碼指出，班級平均成績約 334 分。 若要產生一個總分高於班級平均分數並包含 `Student ID` 的 `Students` 序列，您可以使用 `select` 陳述式中的匿名型別：  
  
     [!code-cs[csLINQGettingStarted#21](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_11.cs)]  
  
## <a name="next-steps"></a>後續步驟  
 熟悉使用 C# 進行查詢的基本概念之後，您即可開始閱讀自己感興趣之特定類型 LINQ 提供者的相關文件和範例：  
  
 [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)  
  
 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a>另請參閱  
 [Language-Integrated Query (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)   
 [開始使用 C# 中的 LINQ](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [LINQ 查詢運算式](../../../../csharp/programming-guide/linq-query-expressions/index.md)

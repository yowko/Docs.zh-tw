---
title: 在 Visual Basic 中撰寫查詢
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
ms.openlocfilehash: 6c5f7d288d805a6a25afa9a5b32a4550aaa76ec3
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45677262"
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a>逐步解說：在 Visual Basic 中撰寫查詢
本逐步解說示範如何使用 Visual Basic 語言功能，以及在寫入[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]查詢運算式。 逐步解說示範如何建立一份學生物件上的查詢、 如何執行查詢，以及如何修改它們。 查詢會將數個功能，包括物件初始設定式、 區域類型推斷和匿名型別。  
  
 完成本逐步解說之後, 您就可以移至特定的文件與範例[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]您感興趣的提供者。 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 提供者包括[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]， [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)]，和[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]。  
  
## <a name="create-a-project"></a>建立專案  
  
#### <a name="to-create-a-console-application-project"></a>若要建立主控台應用程式專案  
  
1.  啟動 Visual Studio。  
  
2.  在 [檔案]  功能表中，指向 [新增] ，然後按一下 [專案] 。  
  
3.  在 **已安裝的範本**清單中，按一下**Visual Basic**。  
  
4.  在專案類型清單中，按一下**主控台應用程式**。 在 **名稱**方塊中，輸入專案的名稱，然後按一下**確定**。  
  
     建立專案。 根據預設，它包含對 System.Core.dll 的參考。 此外，**匯入命名空間**上列出[專案設計工具 (Visual Basic)、 參考頁](/visualstudio/ide/reference/references-page-project-designer-visual-basic)包含<xref:System.Linq?displayProperty=nameWithType>命名空間。  
  
5.  在上[編譯的 Page，Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)，請確認**Option infer**設定為**上**。  
  
## <a name="add-an-in-memory-data-source"></a>加入記憶體中的資料來源  
 本逐步解說中的查詢的資料來源是一份`Student`物件。 每個`Student`物件包含名字、 姓氏、 一類別，以及 academic 學生主體中的陣序規範。  
  
#### <a name="to-add-the-data-source"></a>若要新增資料來源  
  
-   定義`Student`類別，並建立一份類別的執行個體。  
  
    > [!IMPORTANT]
    >  定義所需的程式碼`Student`類別，並建立使用的清單中的逐步解說中提供範例[如何： 建立項目的清單](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)。 您可以從該處複製，並將它貼到您的專案。 新的程式碼取代您在建立專案時出現的程式碼。  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>若要將新的學生新增至學生清單  
  
-   請依照下列中的模式`getStudents`方法，以新增另一個執行個體`Student`類別清單。 加入學生將為您介紹物件初始設定式。 如需詳細資訊，請參閱 <<c0> [ 物件初始設定式： 具名和匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)。  
  
## <a name="create-a-query"></a>建立查詢  
 在執行時，在這一節中新增此查詢會產生學術排名將它們放入前十名學生的清單。 因為此查詢會選取完整`Student`物件每次查詢結果的型別是`IEnumerable(Of Student)`。 不過，查詢類型通常是未指定查詢定義中。 相反地，編譯器會使用區域類型推斷來判斷型別。 如需詳細資訊，請參閱 <<c0> [ 區域型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。 查詢的範圍變數`currentStudent`，做為每個參考`Student`在來源中，執行個體`students`，提供存取權的每個物件在屬性`students`。  
  
#### <a name="to-create-a-simple-query"></a>建立簡單查詢  
  
1.  尋找在處`Main`方法之專案的標記，如下所示：  
  
     [!code-vb[VbLINQWalkthrough#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_1.vb)]  
  
     下列程式碼複製並貼入。  
  
     [!code-vb[VbLINQWalkthrough#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_2.vb)]  
  
2.  將滑鼠指標停留`studentQuery`在您的程式碼，若要確認編譯器指派的類型為`IEnumerable(Of Student)`。  
  
## <a name="run-the-query"></a>執行查詢  
 變數`studentQuery`包含定義的查詢，而不執行查詢的結果。 執行查詢的一般機制是`For Each`迴圈。 透過迴圈反覆項目變數來存取傳回序列中的每個項目。 如需有關查詢執行的詳細資訊，請參閱[撰寫您的第一個 LINQ 查詢](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)。  
  
#### <a name="to-run-the-query"></a>若要執行查詢  
  
1.  新增下列`For Each`迴圈下您的專案中的查詢。  
  
     [!code-vb[VbLINQWalkthrough#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_3.vb)]  
  
2.  將滑鼠指標停留在迴圈控制變數`studentRecord`以查看其資料類型。 型別`studentRecord`就會推斷`Student`，因為`studentQuery`傳回的集合`Student`執行個體。  
  
3.  建置並按下 CTRL + F5 執行應用程式。 請注意 [主控台] 視窗中的結果。  
  
## <a name="modify-the-query"></a>修改查詢  
 很容易就能掃描查詢結果，如果它們是在指定的順序。 您可以排序所傳回的序列，根據任何可用的欄位。  
  
#### <a name="to-order-the-results"></a>若要排序結果  
  
1.  新增下列`Order By`子句之間`Where`陳述式和`Select`查詢陳述式。 `Order By`子句會排序結果依字母順序從 A 到 Z，到最後一個根據每個學生的名稱。  
  
    ```  
    Order By currentStudent.Last Ascending   
    ```  
  
2.  若要排序姓氏及名字，加入查詢中的兩個欄位：  
  
    ```  
    Order By currentStudent.Last Ascending, currentStudent.First Ascending   
    ```  
  
     您也可以指定`Descending`從 Z 到 a。 的順序  
  
3.  建置並按下 CTRL + F5 執行應用程式。 請注意 [主控台] 視窗中的結果。  
  
#### <a name="to-introduce-a-local-identifier"></a>若要導入的本機識別碼  
  
1.  在本節中導入了查詢運算式中的本機識別碼加入程式碼。 本機識別碼會保留中繼結果。 在下列範例中，`name`是保存的學生串連的識別項的名字和姓氏。 為了方便起見，可用的本機識別碼或透過儲存運算式，否則會計算數次的結果，它可以提升效能。  
  
     [!code-vb[VbLINQWalkthrough#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_4.vb)]  
  
2.  建置並按下 CTRL + F5 執行應用程式。 請注意 [主控台] 視窗中的結果。  
  
#### <a name="to-project-one-field-in-the-select-clause"></a>Project Select 子句中的一個欄位  
  
1.  加入查詢和`For Each`此區段來建立可產生的一連串的項目不同於來源中的項目查詢中的迴圈。 在下列範例中，來源是一堆`Student`物件，而每個物件的成員只有一個會傳回： 姓氏是牙哥加西亞島的學生的名字。 因為`currentStudent.First`是一個字串，所傳回的序列的資料型別`studentQuery3`是`IEnumerable(Of String)`，一系列的字串。 如先前範例所示的資料指派輸入`studentQuery3`留給編譯器使用區域型別推斷來判斷。  
  
     [!code-vb[VbLINQWalkthrough#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_5.vb)]  
  
2.  將滑鼠指標停留`studentQuery3`在您的程式碼，以確認指派的類型為`IEnumerable(Of String)`。  
  
3.  建置並按下 CTRL + F5 執行應用程式。 請注意 [主控台] 視窗中的結果。  
  
#### <a name="to-create-an-anonymous-type-in-the-select-clause"></a>若要建立 Select 子句中的匿名型別  
  
1.  加入此區段可查看如何匿名型別中的程式碼會在查詢中使用。 您它們在查詢中使用當您想要傳回的數個欄位從資料來源，而不是完整記錄 (`currentStudent`先前範例中的記錄) 或單一欄位 (`First`上一節)。 而不是定義新的具名型別，其中包含您想要包含在結果中的欄位，您可以指定中的欄位`Select`子句和編譯器建立匿名型別為其屬性的這些欄位。 如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
     下列範例會建立查詢，傳回的名稱和陣序規範的前輩學術排名是介於 1 到 10，學術排名的順序。 在此範例中的型別`studentQuery4`必須推斷，因為`Select`子句會傳回匿名類型的執行個體和匿名型別已經沒有可用的名稱。  
  
     [!code-vb[VbLINQWalkthrough#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_6.vb)]  
  
2.  建置並按下 CTRL + F5 執行應用程式。 請注意 [主控台] 視窗中的結果。  
  
## <a name="additional-examples"></a>其他範例  
 既然您了解基本概念，以下是清單中的其他範例，以說明彈性和能力[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢。 每個範例會加上其用途的簡短描述。 將滑鼠指標停留在查詢結果變數的每個查詢都看到 推斷的型別。 使用`For Each`迴圈來產生結果。  
  
 [!code-vb[VbLINQWalkthrough#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_7.vb)]  
  
## <a name="additional-information"></a>其他資訊  
 您已熟悉使用查詢的基本概念之後，您就可以讀取的特定類型的文件和範例[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]您感興趣的提供者：  
  
 [LINQ to Objects](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
## <a name="see-also"></a>另請參閱

- [Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
- [使用 Visual Basic 撰寫 LINQ 入門](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
- [區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
- [物件初始設定式：具名和匿名類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
- [匿名類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
- [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
- [查詢](../../../../visual-basic/language-reference/queries/index.md)

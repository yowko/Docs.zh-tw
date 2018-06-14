---
title: LINQ 查詢作業中的類型關聯性 (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- inferring type information [LINQ in C#]
- data sources [LINQ in C#], type relationships
- queries [LINQ in C#], type relationships
- relationships [LINQ in C#]
- type relationships [LINQ in C#]
- variable relationships [LINQ in C#]
- type information inferred [LINQ in C#]
- data transformations [LINQ in C#]
- LINQ [C#], type relationships
ms.assetid: 99118938-d47c-4d7e-bb22-2657a9f95268
ms.openlocfilehash: 274c5eaee2b4bf0e1331fb7a4a1a89a432a567c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339575"
---
# <a name="type-relationships-in-linq-query-operations-c"></a>LINQ 查詢作業中的類型關聯性 (C#)
若要有效地撰寫查詢，您應該了解完整查詢作業中的變數類型如何彼此相關。 如果您了解這些關聯性，則可更輕鬆地理解文件中的 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 範例和程式碼範例。 此外，您將了解使用 `var` 讓變數成為隱含類型時的幕後作業。  
  
 在資料來源、查詢本身和查詢執行中，[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢作業都是強型別。 查詢中的變數類型必須與資料來源中的項目類型以及 `foreach` 陳述式中的反覆運算變數類型相容。 如果類型錯誤可以在使用者遇到它們之前進行更正，則這個強型別可確保在編譯時期攔截到它們。  
  
 為了示範這些類型關聯性，後面的大部分範例都會使用所有變數的明確類型。 最後一個範例示範即使使用隱含類型時，還是如何使用 [var](../../../../csharp/language-reference/keywords/var.md) 來套用相同原則。  
  
## <a name="queries-that-do-not-transform-the-source-data"></a>未轉換來源資料的查詢  
 下圖顯示未對資料執行任何轉換的 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects 查詢作業。 來源包含一系列的字串，而且查詢輸出也是一系列的字串。  
  
 ![LINQ 查詢中資料類型的關聯性](../../../../csharp/programming-guide/concepts/linq/media/linq_flow1.png "LINQ_flow1")  
  
1.  資料來源的類型引數決定範圍變數的類型。  
  
2.  所選取物件的類型會決定查詢變數的類型。 `name` 是字串。 因此，查詢變數是 `IEnumerable`\<字串>。  
  
3.  在 `foreach` 陳述式中，會逐一查看查詢變數。 因為查詢變數是一序列的字串，所以反覆運算變數也是字串。  
  
## <a name="queries-that-transform-the-source-data"></a>轉換來源資料的查詢  
 下圖顯示對資料執行簡單轉換的 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 查詢作業。 查詢會接受一系列的 `Customer` 物件作為輸出，並只選取結果中的 `Name` 屬性。 因為 `Name` 是字串，所以查詢會產生一系列的字串作為輸出。  
  
 ![轉換資料類型的查詢](../../../../csharp/programming-guide/concepts/linq/media/linq_flow2.png "LINQ_flow2")  
  
1.  資料來源的類型引數決定範圍變數的類型。  
  
2.  `select` 陳述式會傳回 `Name` 屬性，而非完整 `Customer` 物件。 因為 `Name` 是字串，所以 `custNameQuery` 的類型引數是 `string`，而非 `Customer`。  
  
3.  因為 `custNameQuery` 是一序列的字串，所以 `foreach` 迴圈的反覆運算變數也必須是 `string`。  
  
 下圖顯示稍微複雜的轉換。 `select` 陳述式會傳回匿名型別，只擷取原始 `Customer` 物件的兩個成員。  
  
 ![轉換資料類型的查詢](../../../../csharp/programming-guide/concepts/linq/media/linq_flow3.png "LINQ_flow3")  
  
1.  資料來源的類型引數一律是查詢中範圍變數的類型。  
  
2.  因為 `select` 陳述式會產生匿名型別，所以必須使用 `var` 讓查詢變數成為隱含類型。  
  
3.  因為查詢變數的類型是隱含的，所以 `foreach` 迴圈中的反覆運算變數也是隱含的。  
  
## <a name="letting-the-compiler-infer-type-information"></a>讓編譯器推斷類型資訊  
 雖然您應該了解查詢作業中的類型關聯性，但可以選擇讓編譯器為您執行所有工作。 [var](../../../../csharp/language-reference/keywords/var.md) 關鍵字可以用於查詢作業中的任何區域變數。 下圖與先前討論的範例 2 類似。 不過，編譯器會提供查詢作業中每個變數的強型別。  
  
 ![具有隱含類型功能的類型流程](../../../../csharp/programming-guide/concepts/linq/media/linq_flow4.png "LINQ_flow4")  
  
 如需 `var` 的詳細資訊，請參閱[隱含類型區域變數](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)。  
  
## <a name="see-also"></a>請參閱  
 [開始使用 C# 中的 LINQ](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)

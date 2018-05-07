---
title: Value Types and Reference Types
ms.date: 07/20/2015
helpviewer_keywords:
- reference data types [Visual Basic]
- reference types [Visual Basic]
- value types [Visual Basic]
- value data types [Visual Basic]
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
ms.openlocfilehash: 9456316f71a213905bcb50336533c4e618f5174a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="value-types-and-reference-types"></a>Value Types and Reference Types
在 Visual Basic 中，資料類型會實作其分類為基礎。 Visual Basic 資料類型可以根據自己的資料或資料指標，特定類型的變數是否儲存分類。 如果它會儲存它自己的資料很*實值型別*; 如果它是的記憶體中其他位置的資料會保留指標*參考型別*。  
  
## <a name="value-types"></a>實值類型  
 資料類型是*實值型別*如果它包含在它自己的記憶體配置中的資料。 實值類型包括：  
  
-   所有的數值資料類型  
  
-   `Boolean`、`Char` 和 `Date`  
  
-   所有的結構，即使它們的成員屬於參考類型  
  
-   列舉型別，因為其基礎類型一律為`SByte`， `Short`， `Integer`， `Long`， `Byte`， `UShort`， `UInteger`，或 `ULong`  
  
 每個結構是實值類型，即使它包含參考類型的成員。 基於這個理由，實值類型例如`Char`和`Integer`.NET Framework 結構來實作。  
  
 您可以使用保留的關鍵字，例如，宣告實值類型`Decimal`。 您也可以使用`New`初始化實值類型的關鍵字。 這是特別有用，如果型別參數的建構函式。 舉例來說，這是<xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29>建構函式，會建置新`Decimal`值從提供的部分。  
  
## <a name="reference-types"></a>參考類型  
 A*參考型別*包含保存資料的另一個記憶體位置的指標。 參考型別包括：  
  
-   `String`  
  
-   所有的陣列，即使其元素為實值類型  
  
-   類別類型例如 <xref:System.Windows.Forms.Form>  
  
-   委派  
  
 類別是*參考型別*。 基於這個理由，參考類型例如`Object`和`String`支援[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]類別。 請注意，每個陣列參考類型，即使其成員都是實值類型。  
  
 由於每個參考型別代表基本的.NET Framework 類別，您必須使用[New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)關鍵字，當您將它初始化。 下列陳述式初始化陣列。  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a>不是類型的項目  
 下列的程式設計項目不符合做為型別，因為您無法將它們其中任何一個指定為資料類型的宣告的項目：  
  
-   命名空間  
  
-   模組  
  
-   事件  
  
-   屬性和程序  
  
-   變數、 常數和欄位  
  
## <a name="working-with-the-object-data-type"></a>使用物件資料類型  
 您可以將參考類型或實值類型指派給變數`Object`資料型別。 `Object`變數一律會保留指標的資料，永遠不會資料本身。 不過，如果您指派至實值類型`Object`變數，其行為就如同它包含它自己的資料。 如需詳細資訊，請參閱[物件資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)。  
  
 您可以找出是否`Object`變數做為參考類型或實值類型傳遞至<xref:Microsoft.VisualBasic.Information.IsReference%2A>方法中的<xref:Microsoft.VisualBasic.Information>類別<xref:Microsoft.VisualBasic?displayProperty=nameWithType>命名空間。 <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> 傳回`True`如果內容`Object`變數代表參考型別。  
  
## <a name="see-also"></a>另請參閱  
 [可為 Null 的值類型](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [在 Visual Basic 中的型別轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Structure 陳述式](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [有效率地使用資料類型](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Object 資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)

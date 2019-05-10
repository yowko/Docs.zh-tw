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
ms.openlocfilehash: f823d9e80eb644487eab1ed84345dd8bdc10efc2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64600948"
---
# <a name="value-types-and-reference-types"></a>Value Types and Reference Types
在 Visual Basic 中的資料類型是根據其分類所實作的。 Visual Basic 資料類型可以根據自己的資料或資料指標，特定類型的變數是否儲存分類。 它會儲存它自己的資料是否*實值型別*; 如果它是的記憶體中其他位置的資料會保留指標*參考型別*。  
  
## <a name="value-types"></a>實值類型  
 資料類型是*實值型別*它存放在自己的記憶體配置中的資料。 實值型別包括下列各項：  
  
- 所有數值資料類型  
  
- `Boolean`、 `Char`和 `Date`  
  
- 所有的結構，即使它們的成員是參考型別  
  
- 列舉型別，因為其基礎類型一律`SByte`， `Short`， `Integer`， `Long`， `Byte`， `UShort`， `UInteger`，或 `ULong`  
  
 每個結構是實值類型，即使它包含參考型別成員。 基於這個理由，實值型別這類`Char`和`Integer`由.NET Framework 結構。  
  
 您可以使用的保留的關鍵字，例如，宣告實值型別`Decimal`。 您也可以使用`New`初始化實值類型的關鍵字。 這是特別有用，如果類型具有參數的建構函式。 舉例來說，這<xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29>建構函式，會建置新`Decimal`從提供的組件的值。  
  
## <a name="reference-types"></a>參考類型  
 A*參考的型別*包含保存資料的另一個記憶體位置的指標。 參考類型包括下列各項：  
  
- `String`  
  
- 所有的陣列，即使其元素為實值類型  
  
- 類別類型例如 <xref:System.Windows.Forms.Form>  
  
- 委派  
  
 類別是*參考的型別*。 基於這個理由，參考類型這類`Object`並`String`受到[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]類別。 請注意，每個陣列參考類型，即使其成員都是實值型別。  
  
 由於每個參考型別代表基本的.NET Framework 類別，您必須使用[New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)關鍵字時將它初始化。 下列陳述式初始化陣列。  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a>不是類型的項目  
 下列的程式設計項目不會限定為型別，因為您無法指定任何一個宣告的項目資料類型為：  
  
- 命名空間  
  
- 模組  
  
- 事件  
  
- 屬性和程序  
  
- 變數、 常數和欄位  
  
## <a name="working-with-the-object-data-type"></a>使用物件資料類型  
 您可以將參考類型或實值型別指派給變數的`Object`資料型別。 `Object`變數一律會保留指標的資料，永遠不會將資料本身。 不過，如果您指派至實值型別`Object`變數，其行為就如同它會保留它自己的資料。 如需詳細資訊，請參閱 < [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)。  
  
 您可以找出是否`Object`變數做為參考型別或實值型別傳遞至<xref:Microsoft.VisualBasic.Information.IsReference%2A>方法中的<xref:Microsoft.VisualBasic.Information>類別的<xref:Microsoft.VisualBasic?displayProperty=nameWithType>命名空間。 <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> 會傳回`True`如果內容`Object`變數代表參考型別。  
  
## <a name="see-also"></a>另請參閱

- [可為 Null 的值類型](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [在 Visual Basic 中的類型轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Structure 陳述式](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [有效率地使用資料類型](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Object 資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)

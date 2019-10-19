---
title: 複合資料類型 (Visual Basic)
ms.date: 04/25/2017
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
ms.openlocfilehash: 768559c7a6caf064f7529786675e51ce19667d6b
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581718"
---
# <a name="composite-data-types-visual-basic"></a>複合資料類型 (Visual Basic)
除了 Visual Basic 提供的基本資料類型之外，您也可以組合不同類型的專案來建立*複合資料型別*，例如結構、陣列和類別。 您可以從基本類型和其他複合類型建立複合資料型別。 例如，您可以定義結構專案的陣列，或是包含陣列成員的結構。  
  
## <a name="data-types"></a>資料類型  
 複合類型與任何元件的資料類型不同。 例如，`Integer` 元素的陣列不是 `Integer` 的資料類型。  
  
 陣列資料類型通常會在必要時使用元素類型、括弧和逗號來表示。 例如，`String` 專案的一維陣列會以 `String()` 表示，而 `Boolean` 元素的二維陣列則會以 `Boolean(,)` 表示。  
  
## <a name="structure-types"></a>結構類型  
 沒有組成所有結構的單一資料類型。 相反地，結構的每個定義都代表唯一的資料類型，即使兩個結構以相同的順序定義相同的元素。 不過，如果您建立相同結構的兩個或多個實例，Visual Basic 會將它們視為相同的資料類型。  
  
## <a name="tuples"></a>Tuple

元組是輕量結構，其中包含兩個或多個預先定義類型的欄位。 從 Visual Basic 2017 開始支援元組。 元組最常用來傳回單一方法呼叫中的多個值，而不需要以傳址方式傳遞引數，或將傳回的欄位封裝在較高的權數類別或結構中。 如需元組的詳細資訊，請參閱[元組](tuples.md)主題。

## <a name="array-types"></a>陣列類型  
 沒有組成所有陣列的單一資料類型。 陣列特定實例的資料類型取決於下列各項：  
  
- 成為陣列的事實  
  
- 陣列的順位（維度數目）  
  
- 陣列的元素類型  
  
 特別是，指定維度的長度不是實例資料類型的一部分。 下列範例將說明這點。  
  
```vb  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 在上述範例中，`arrayA` 和 `arrayB` 的陣列變數會被視為相同的資料類型（`Byte()`），即使它們已初始化為不同的長度也一樣。 @No__t_0 和 `arrayC` 的變數不屬於相同類型，因為它們的元素類型不同。 @No__t_0 和 `arrayD` 的變數不屬於相同類型，因為它們的次序不同。 @No__t_0 和 `arrayE` 的變數具有相同的類型（`Short(,)`），因為它們的次序和元素類型相同，即使 `arrayD` 尚未初始化也一樣。  
  
 如需陣列的詳細資訊，請參閱[陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)。  
  
## <a name="class-types"></a>類別類型  
 沒有組成所有類別的單一資料類型。 雖然一個類別可以繼承自另一個類別，但每個都是不同的資料類型。 相同類別的多個實例屬於相同的資料類型。 如果您將一個類別執行個體變數指派給另一個，不只是它們具有相同的資料類型，而是指向記憶體中的相同類別實例。  
  
 如需類別的詳細資訊，請參閱[物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)。  
  
## <a name="see-also"></a>請參閱

- [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [基礎資料類型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Generic Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Visual Basic 中的類型轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [結構](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [如何：在變數中存放多個值](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)

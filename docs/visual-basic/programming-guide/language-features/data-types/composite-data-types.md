---
title: 複合資料類型 (Visual Basic)
ms.custom: ''
ms.date: 04/25/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: caa832fc191ad925674e21b1237ac98328ce0bd7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="composite-data-types-visual-basic"></a>複合資料類型 (Visual Basic)
除了提供的基本資料型別 Visual Basic，您也可以組合建立不同類型的項目*複合資料類型*例如結構、 陣列和類別。 基本型別和其他複合類型，您可以建置複合資料類型。 例如，您可以定義結構元素的陣列或結構的陣列成員。  
  
## <a name="data-types"></a>資料類型  
 一種複合類型與不同元件的資料類型。 例如，陣列`Integer`項目不是`Integer`資料型別。  
  
 視使用的項目類型、 括號和逗號，通常表示陣列資料類型。 例如的一維陣列`String`項目以`String()`，和的二維陣列`Boolean`項目以`Boolean(,)`。  
  
## <a name="structure-types"></a>結構類型  
 沒有可包含所有結構的單一資料型別。 相反地，結構的每個定義都代表唯一的資料類型，即使兩個結構會定義相同的項目相同的順序。 不過，如果您建立的相同結構的兩個或多個執行個體時，Visual Basic 會將它們視為相同的資料類型。  
  
## <a name="tuples"></a>Tuple

Tuple 是輕量型的結構，包含其類型已預先定義的兩個或多個欄位。 開始 Visual Basic 2017，支援 Tuple。 Tuple 最常用在單一方法呼叫傳回多個值，而不需傳址方式傳遞引數，或封裝更重量類別或結構中傳回的欄位。 請參閱[Tuple](tuples.md)如需有關 tuple 的主題。

## <a name="array-types"></a>陣列類型  
 沒有可包含所有陣列的單一資料型別。 陣列的特定執行個體的資料類型是由以下決定：  
  
-   事實上，在陣列  
  
-   陣列的陣序 （維度數目）  
  
-   陣列的項目類型  
  
 特別是，指定維度的長度不是執行個體的資料類型的一部分。 下列範例將說明這點。  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 在上述範例中，陣列變數`arrayA`和`arrayB`會被視為相同的資料類型的 — `Byte()` — 即使已初始化為不同的長度。 變數`arrayB`和`arrayC`相同類型的不是，因為其項目類型不同。 變數`arrayC`和`arrayD`相同類型的不是，因為其順位不同。 變數`arrayD`和`arrayE`有相同的類型 — `Short(,)` ，因為它們的排列次序和項目型別是相同的即使`arrayD`尚未初始化。  
  
 如需陣列的詳細資訊，請參閱[陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)。  
  
## <a name="class-types"></a>類別類型  
 沒有可包含的所有類別的單一資料型別。 雖然一個類別可以繼承自另一個類別，每一個都是個別的資料類型。 多個相同的類別執行個體都屬於相同的資料類型。 如果您將一個類別的執行個體變數指派給另一個時，不只有相同的資料類型，其指向在記憶體中相同的類別執行個體。  
  
 如需類別的詳細資訊，請參閱[物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)。  
  
## <a name="see-also"></a>另請參閱  
 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [基礎資料類型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Visual Basic 中的泛型型別](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [在 Visual Basic 中的型別轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [結構](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [如何：在變數中存放多個值](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)

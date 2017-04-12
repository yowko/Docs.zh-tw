---
title: "複合資料類型 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types
- composite data types
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures, composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d81b2c08155cb16754e780fdfb341b596322302d
ms.lasthandoff: 03/13/2017

---
# <a name="composite-data-types-visual-basic"></a>複合資料類型 (Visual Basic)
除了基本資料型別[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]供應器，您可以組合建立不同類型的項目*複合資料型別*例如結構、 陣列和類別。 基本型別和其他複合類型，您可以建置複合資料型別。 例如，您可以定義結構元素的陣列或結構的陣列成員。  
  
## <a name="data-types"></a>資料類型  
 一種複合類型是不同於元件的資料型別。 例如，陣列`Integer`項目不是`Integer`資料型別。  
  
 使用所需的項目型別、 括號和逗號，通常表示陣列資料型別。 比方說，一維陣列的`String`項目以`String()`，和一個二維陣列`Boolean`項目以`Boolean(,)`。  
  
## <a name="structure-types"></a>結構化型別  
 沒有可包含所有結構的單一資料型別。 相反地，每個結構的定義都代表唯一的資料類型，即使兩個結構會定義相同的項目會以相同的順序。 不過，如果您建立兩個或多個執行個體相同的結構，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]會考慮它們是相同的資料型別。  
  
## <a name="array-types"></a>陣列型別  
 沒有可包含所有陣列的單一資料型別。 陣列的特定執行個體的資料型別是由下列決定︰  
  
-   根本就屬於陣列  
  
-   陣列的陣序規範 （維度數目）  
  
-   陣列的項目類型  
  
 特別是，指定維度的長度不是執行個體的資料類型的一部分。 下列範例將說明這點。  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 在上述範例中，陣列變數`arrayA`和`arrayB`視為相同的資料類型的 — `Byte()` — 即使它們會初始化為不同的長度。 變數`arrayB`和`arrayC`相同類型的不是，因為其項目型別不同。 變數`arrayC`和`arrayD`相同類型的不是，因為其陣序規範不相同。 變數`arrayD`和`arrayE`有相同的類型 — `Short(,)` ，因為它們的陣序規範和項目類型都相同，即使`arrayD`尚未初始化。  
  
 如需有關陣列的詳細資訊，請參閱[陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)。  
  
## <a name="class-types"></a>類別類型  
 沒有可包含的所有類別的單一資料型別。 雖然一個類別可以繼承自另一個類別，每一個都是個別的資料類型。 多個相同執行個體是類別的相同的資料類型。 如果指派給另一個類別的執行個體變數，不只它們有相同的資料類型，其指向在記憶體中相同的類別執行個體。  
  
 如需類別的詳細資訊，請參閱[物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)。  
  
## <a name="see-also"></a>另請參閱  
 [資料型別](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [基本資料型別](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Visual Basic 中的泛型型別](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [實值型別和參考型別](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [在 Visual Basic 中的型別轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [結構](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [資料類型疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [如何：在變數中存放多個值](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)

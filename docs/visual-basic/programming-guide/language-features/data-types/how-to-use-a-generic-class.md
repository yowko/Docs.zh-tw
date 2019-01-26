---
title: HOW TO：使用泛型類別 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- generic parameters
- data type parameters
- generics [Visual Basic], about generics
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], creating generic types
- data type arguments
- parameters [Visual Basic], data type
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 242dd2a6-86c4-4ce7-83f2-f2661803f752
ms.openlocfilehash: 4f60c0c07c0270b94dbb018b9423e210f16269d6
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55065800"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a>HOW TO：使用泛型類別 (Visual Basic)
採用 *「類型參數」* (type parameter) 的類別稱為 *「泛型類別」*(generic class)。 如果您使用泛型類別，則可以透過它產生 *「建構類別」* (constructed class)，方法是提供所有這些參數的 *「類型引數」* (type argument)。 您接著可以宣告所建構類別類型的變數，而且可以建立所建構類別的執行個體，並將它指派給該變數。  
  
 除了類別之外，您還可以定義和使用泛型結構、介面、程序和委派。  
  
 下列程序會採用 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 中所定義的泛型類別，並透過它建立執行個體。  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a>使用採用類型參數的類別  
  
1.  在原始程式檔的開頭，包含[Imports 陳述式 （.NET 命名空間和類型）](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)匯入<xref:System.Collections.Generic?displayProperty=nameWithType>命名空間。 這可讓您參考 <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> 類別，而不需要完整限定它就區分它與其他佇列類別 (例如 <xref:System.Collections.Queue?displayProperty=nameWithType>)。  
  
2.  以一般方式，建立物件，但新增`(Of type)`後面的類別名稱。  
  
     下列範例使用相同的類別 (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) 來建立保留不同資料類型之項目的兩個佇列物件。 它會將項目新增至每個佇列的結尾，然後移除，並顯示每個佇列前端的項目。  
  
     [!code-vb[VbVbalrDataTypes#9](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-use-a-generic-class_1.vb)]  
  
## <a name="see-also"></a>另請參閱

- [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Generic Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [語言獨立性以及與語言無關的元件](../../../../standard/language-independence-and-language-independent-components.md)
- [Of](../../../../visual-basic/language-reference/statements/of-clause.md)
- [Imports 陳述式 (.NET 命名空間和類型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [如何：定義可以在不同資料類型上提供完全相同功能的類別](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)
- [迭代器](../../../../visual-basic/programming-guide/concepts/iterators.md)

---
title: 作法：使用泛型類別
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
ms.openlocfilehash: 01f1f7ef5963feeb3fe2b5390244e4e516773bad
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393840"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a>如何：使用泛型類別 (Visual Basic)
採用 *「類型參數」* (type parameter) 的類別稱為 *「泛型類別」*(generic class)。 如果您使用泛型類別，則可以透過它產生 *「建構類別」* (constructed class)，方法是提供所有這些參數的 *「類型引數」* (type argument)。 您接著可以宣告所建構類別類型的變數，而且可以建立所建構類別的執行個體，並將它指派給該變數。  
  
 除了類別之外，您還可以定義和使用泛型結構、介面、程序和委派。  
  
 下列程式會採用在 .NET Framework 中定義的泛型類別，並從中建立實例。  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a>使用採用類型參數的類別  
  
1. 在原始程式檔的開頭，加入[Imports 語句（.Net 命名空間和類型）](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)來匯入 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空間。 這可讓您參考 <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> 類別，而不需要完整限定它就區分它與其他佇列類別 (例如 <xref:System.Collections.Queue?displayProperty=nameWithType>)。  
  
2. 以一般方式建立物件，但是在類別名稱之後立即新增 `(Of type)` 。  
  
     下列範例使用相同的類別 (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) 來建立保留不同資料類型之項目的兩個佇列物件。 它會將項目新增至每個佇列的結尾，然後移除，並顯示每個佇列前端的項目。  
  
     [!code-vb[VbVbalrDataTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>另請參閱

- [資料類型](index.md)
- [Generic Types in Visual Basic](generic-types.md)
- [語言獨立性以及與語言無關的元件](../../../../standard/language-independence-and-language-independent-components.md)
- [的](../../../language-reference/statements/of-clause.md)
- [Imports 陳述式 (.NET 命名空間和類型)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [作法：定義可以為不同資料類型提供相同功能的類別](how-to-define-a-class-that-can-provide-identical-functionality.md)
- [迭代器](../../concepts/iterators.md)

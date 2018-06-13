---
title: 如何：定義可以在不同資料類型上提供完全相同功能的類別 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data type arguments [Visual Basic], using
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- data type parameters [Visual Basic], using
- generics [Visual Basic], defining classes with type parameters
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- type arguments
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
- parameters [Visual Basic], data type
- generics [Visual Basic], defining generic types
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: a914adf8-e68f-4819-a6b1-200d1cf1c21c
ms.openlocfilehash: 3570a1c851bb8fead33f4cd208489c4ae087a68d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650344"
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a>如何：定義可以在不同資料類型上提供完全相同功能的類別 (Visual Basic)
您可以定義一個類別，以從中建立可在不同資料類型上提供相同功能的物件。 若要這樣做，請在定義中指定一個或多個 *「類型參數」* (type parameter)。 類別之後可以作為使用各種資料類型之物件的範本。 使用這種方法所定義的類別稱為 *「泛型類別」*(generic class)。  
  
 定義泛型類別的優點是只需要定義一次，而且您的程式碼可以使用它來建立許多使用各種資料類型的物件。 這所導致的效能優於定義具有 `Object` 類型的類別。  
  
 除了類別之外，您還可以定義和使用泛型結構、介面、程序和委派。  
  
### <a name="to-define-a-class-with-a-type-parameter"></a>定義具有類型參數的類別  
  
1.  以一般方式定義類別。  
  
2.  立即在類別名稱後面加入 `(Of` *類型參數*`)` ，以指定類型參數。  
  
3.  如果您有多個類型參數，請在括號內建立以逗號分隔的清單。 請不要重複 `Of` 關鍵字。  
  
4.  如果您的程式碼對類型參數執行簡單指派以外的作業，請在該類型參數後面加上 `As` 子句來加入一個或多個 *「條件約束」*(constraint)。 條件約束保證針對該類型參數所提供的類型符合下列這類需求：  
  
    -   支援您程式碼所執行的作業 (例如 `>`)  
  
    -   支援您程式碼所存取的成員 (例如方法)  
  
    -   公開無參數建構函式  
  
     如果您未指定任何條件約束，則您程式碼可使用的唯一作業和成員是 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)所支援的作業和成員。 如需詳細資訊，請參閱 [Type List](../../../../visual-basic/language-reference/statements/type-list.md)。  
  
5.  識別要宣告所提供類型的每個類別成員，並將它宣告為 `As` `typeparameter`。 這適用於內部儲存體、程序參數和傳回值。  
  
6.  請確定您的程式碼只會使用它可提供給 `itemType`之任何資料類型所支援的作業和方法。  
  
     下列範例定義可管理極簡單清單的類別。 它會將清單保留在內部陣列 `items`中，而 using 程式碼可以宣告清單項目的資料類型。 參數化建構函式可讓 using 程式碼設定 `items`上限，而預設建構函式會將此項目設為 9 (共 10 個項目)。  
  
     [!code-vb[VbVbalrDataTypes#7](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_1.vb)]  
  
     您可以從 `simpleList` 宣告一個類別來保留 `Integer` 值清單、另一個類別來保留 `String` 值清單，以及另一個類別來保留 `Date` 值。 除了清單成員的資料類型之外，從所有這些類別建立之物件的行為都相同。  
  
     using 程式碼提供給 `itemType` 的類型引數可以是內建類型 (例如 `Boolean` 或 `Double`)、結構、列舉值或任何類型的類別 (包括您應用程式所定義的其中一個類別)。  
  
     您可以使用下列程式碼測試 `simpleList` 類別。  
  
     [!code-vb[VbVbalrDataTypes#8](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Visual Basic 中的泛型型別](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [語言獨立性以及與語言無關的元件](../../../../standard/language-independence-and-language-independent-components.md)  
 [Of](../../../../visual-basic/language-reference/statements/of-clause.md)  
 [類型清單](../../../../visual-basic/language-reference/statements/type-list.md)  
 [如何：使用泛型類別](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Object 資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)

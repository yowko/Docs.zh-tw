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
ms.openlocfilehash: 72cb1455300e1ff00d9d558aa5a9df95f32aa7b0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090114"
---
# <a name="value-types-and-reference-types"></a>Value Types and Reference Types

Visual Basic 中有兩種類型：參考型別和實數值型別。 參考類型的變數會儲存期資料 (物件) 的參考，而實值類型的變數則會直接包含其資料。 使用參考類型時，這兩種變數可以參考相同的物件，因此對其中一個變數進行的作業可能會影響另一個變數所參考的物件。 使用實值型別時，每個變數都有自己的資料複本，而且在某個變數上進行的作業不可能會影響其他 (但在參數) 的 [ByRef 修飾](../../../language-reference/modifiers/byref.md) 詞情況下除外。
  
## <a name="value-types"></a>實值類型  

 如果資料類型在它自己的記憶體配置內保存資料，就是實 *值型* 別。 數值型別包括下列各項：  
  
- 所有數值資料類型  
  
- `Boolean`、`Char` 和 `Date`  
  
- 所有結構，即使其成員為參考型別  
  
- 列舉，因為它們的基礎類型一律是、、、、、 `SByte` `Short` `Integer` `Long` `Byte` `UShort` 、 `UInteger` 或 `ULong`  
  
 每個結構都是實值型別，即使它包含參考型別成員也一樣。 基於這個理由，實數值型別（例如 `Char` 和） `Integer` 會由 .NET Framework 結構來執行。  
  
 您可以使用保留關鍵字宣告實值型別，例如， `Decimal` 。 您也可以使用 `New` 關鍵字來初始化實值型別。 如果類型具有接受參數的函式，這會特別有用。 其中一個範例是 <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> 從提供的元件建立新值的函式 `Decimal` 。  
  
## <a name="reference-types"></a>參考類型  

 *參考型*別會儲存其資料的參考。 參考型別包含下列各項：  
  
- `String`  
  
- 所有陣列（即使其元素為實數值型別）  
  
- 類別類型，例如 <xref:System.Windows.Forms.Form>  
  
- 委派  
  
 類別是 *參考型別*。 請注意，每個陣列都是參考型別，即使其成員是實數值型別。  
  
 因為每個參考型別都代表基礎 .NET Framework 類別，所以您必須在初始化時使用 [New Operator](../../../language-reference/operators/new-operator.md) 關鍵字。 下列語句會初始化陣列。  
  
```vb  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a>非類型的元素  

 下列程式設計專案不符合型別資格，因為您不能將它們指定為宣告專案的資料類型：  
  
- 命名空間  
  
- 模組  
  
- 事件  
  
- 屬性和程式  
  
- 變數、常數和欄位  
  
## <a name="working-with-the-object-data-type"></a>使用物件資料類型  

 您可以將參考型別或實值型別指派給 `Object` 資料類型的變數。 `Object`變數一律會保存資料的參考，而不是資料本身。 但是，如果您將實值型別指派給 `Object` 變數，它的行為就像它擁有自己的資料一樣。 如需詳細資訊，請參閱 [物件資料類型](../../../language-reference/data-types/object-data-type.md)。  
  
 您可以藉 `Object` 由將變數傳遞給 <xref:Microsoft.VisualBasic.Information.IsReference%2A> <xref:Microsoft.VisualBasic.Information> 命名空間類別中的方法，找出變數是否做為參考型別或實值型別 <xref:Microsoft.VisualBasic?displayProperty=nameWithType> 。 <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType>`True`如果變數的內容 `Object` 表示參考型別，則傳回。  
  
## <a name="see-also"></a>另請參閱

- [可為 null 的實數值型別](nullable-value-types.md)
- [Visual Basic 中的類型轉換](type-conversions.md)
- [Structure 陳述式](../../../language-reference/statements/structure-statement.md)
- [有效率地使用資料類型](efficient-use-of-data-types.md)
- [Object Data Type](../../../language-reference/data-types/object-data-type.md)
- [Data types (資料類型)](index.md)

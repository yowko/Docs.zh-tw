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
ms.openlocfilehash: 3a1de120f5f97ba93939f332f121d70cd3091216
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392970"
---
# <a name="value-types-and-reference-types"></a>Value Types and Reference Types
Visual Basic 中有兩種類型：參考型別和實數值型別。 參考類型的變數會儲存期資料 (物件) 的參考，而實值類型的變數則會直接包含其資料。 使用參考類型時，這兩種變數可以參考相同的物件，因此對其中一個變數進行的作業可能會影響另一個變數所參考的物件。 使用實值型別時，每個變數都有自己的資料複本，而且一個變數上的作業不可能影響另一個（在[參數上為 ByRef 修飾](../../../language-reference/modifiers/byref.md)詞的情況除外）。
  
## <a name="value-types"></a>實值類型  
 如果資料類型在它自己的記憶體配置中保存資料，就是實*數值型別*。 數值型別包括下列各項：  
  
- 所有數值資料類型  
  
- `Boolean`、`Char` 和 `Date`  
  
- 所有結構，即使它們的成員是參考型別  
  
- 列舉，因為其基礎類型一律為 `SByte` 、 `Short` 、 `Integer` 、 `Long` 、、、 `Byte` `UShort` `UInteger` 或。`ULong`  
  
 每個結構都是實值型別，即使它包含引用型別成員也一樣。 基於這個理由，和之類的實值型別 `Char` `Integer` 都是由 .NET Framework 結構來執行。  
  
 您可以使用 reserved 關鍵字來宣告實值型別，例如 `Decimal` 。 您也可以使用 `New` 關鍵字來初始化實值型別。 如果型別具有接受參數的函式，這會特別有用。 這是一個範例 <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> ，它會 `Decimal` 從提供的元件建立新的值。  
  
## <a name="reference-types"></a>參考類型  
 *參考型*別會儲存其資料的參考。 參考型別包括下列各項：  
  
- `String`  
  
- 所有陣列，即使其元素是實數值型別  
  
- 類別類型，例如<xref:System.Windows.Forms.Form>  
  
- 委派  
  
 類別是*參考型*別。 請注意，每個陣列都是參考型別，即使它的成員是實數值型別也是如此。  
  
 由於每個參考型別都代表一個基礎 .NET Framework 類別，因此當您初始化它時，您必須使用[New Operator](../../../language-reference/operators/new-operator.md)關鍵字。 下列語句會初始化陣列。  
  
```vb  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a>不是類型的元素  
 下列程式設計項目不符合型別的資格，因為您無法將其中任何一個當做宣告專案的資料型別。  
  
- 命名空間  
  
- 單元  
  
- 事件  
  
- 屬性和程式  
  
- 變數、常數和欄位  
  
## <a name="working-with-the-object-data-type"></a>使用 Object 資料類型  
 您可以將參考型別或實數值型別指派給 `Object` 資料類型的變數。 `Object`變數一律會保留資料的參考，而不是資料本身。 不過，如果您將實值型別指派給 `Object` 變數，它的行為就如同它擁有自己的資料一樣。 如需詳細資訊，請參閱[Object Data Type](../../../language-reference/data-types/object-data-type.md)。  
  
 您可以藉 `Object` 由將變數傳遞至 <xref:Microsoft.VisualBasic.Information.IsReference%2A> <xref:Microsoft.VisualBasic.Information> 命名空間之類別中的方法，來找出變數是否做為參考型別或實值型別 <xref:Microsoft.VisualBasic?displayProperty=nameWithType> 。 <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType>`True`如果變數的內容 `Object` 代表參考型別，則傳回。  
  
## <a name="see-also"></a>另請參閱

- [可為 null 的實數值型別](nullable-value-types.md)
- [Visual Basic 中的類型轉換](type-conversions.md)
- [Structure 陳述式](../../../language-reference/statements/structure-statement.md)
- [有效率地使用資料類型](efficient-use-of-data-types.md)
- [Object Data Type](../../../language-reference/data-types/object-data-type.md)
- [資料類型](index.md)

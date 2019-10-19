---
title: 參數清單 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic
- parameters [Visual Basic], lists
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures [Visual Basic], parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
ms.openlocfilehash: 0dded7fd68256b9b9de8ebe4b48073eb40696c12
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582173"
---
# <a name="parameter-list-visual-basic"></a>參數清單 (Visual Basic)

指定程式在呼叫時所預期的參數。 多個參數會以逗號分隔。 以下是一個參數的語法。

## <a name="syntax"></a>語法

```vb
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]
parametername[( )] [ As parametertype ] [ = defaultvalue ]
```

## <a name="parts"></a>組件

`attributelist`  
選擇項。 適用于此參數的屬性清單。 您必須將[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)放在角括弧中（「`<`」和「`>`」）。

`Optional`  
選擇項。 指定在呼叫程式時，不需要這個參數。

`ByVal`  
選擇項。 指定程式無法取代或重新指派呼叫程式碼中對應引數基礎的變數元素。

`ByRef`  
選擇項。 指定程式可以修改呼叫程式碼中的基礎變數元素，方法就和呼叫程式碼本身相同。

`ParamArray`  
選擇項。 指定參數清單中的最後一個參數是指定之資料類型的選擇性元素陣列。 這可讓呼叫程式碼將任意數目的引數傳遞至程式。

`parametername`  
必要項。 代表參數的本機變數名稱。

`parametertype`  
如果 `Option Strict` `On`，則為必要。 代表參數之本機變數的資料類型。

`defaultvalue`  
@No__t_0 參數所需。 評估為參數資料類型的任何常數或常數運算式。 如果類型是 `Object`，或是類別、介面、陣列或結構，則預設值只能 `Nothing`。

## <a name="remarks"></a>備註

參數會以括弧括住，並以逗號分隔。 參數可以使用任何資料類型來宣告。 如果您未指定 `parametertype`，它會預設為 `Object`。

當呼叫程式碼呼叫程式時，它會將*引數*傳遞給每個必要的參數。 如需詳細資訊，請參閱[參數和引數之間的差異](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md)。

呼叫程式碼傳遞至每個參數的引數是呼叫程式碼中基礎元素的指標。 如果這個元素是不*變數*（常數、常值、列舉或運算式），任何程式碼都無法變更它。 如果它是*變數*元素（宣告的變數、field、property、array 元素或 structure 元素），則呼叫程式碼可以變更它。 如需詳細資訊，請參閱可[修改的和不可變引數之間的差異](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)。

如果將變數元素傳遞 `ByRef`，程式也可以變更它。 如需詳細資訊，請參閱[依值和傳址方式傳遞引數之間的差異](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)。

## <a name="rules"></a>規則

- **後.** 如果您指定參數清單，則必須將它括在括弧中。 如果沒有參數，您仍然可以使用括住空白清單的括弧。 這會藉由明確說明元素為程式，來改善程式碼的可讀性。

- **選擇性參數。** 如果您在參數上使用 `Optional` 修飾詞，則清單中的所有後續參數也必須是選擇性的，並且使用 `Optional` 修飾詞進行宣告。

     每個選擇性參數宣告都必須提供 `defaultvalue` 子句。

     如需詳細資訊，請參閱[選擇性參數](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)。

- **參數陣列。** 您必須指定 `ParamArray` 參數的 `ByVal`。

     您不能同時在相同的參數清單中使用 `Optional` 和 `ParamArray`。

     如需詳細資訊，請參閱[參數陣列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)。

- **傳遞機制。** 每個引數的預設機制都是 `ByVal`，這表示程式無法變更基礎變數元素。 不過，如果元素是參考型別，程式可以修改基礎物件的內容或成員，即使它無法取代或重新指派物件本身也一樣。

- **參數名稱。** 如果參數的資料類型是陣列，請依照括弧立即 `parametername`。 如需參數名稱的詳細資訊，請參閱宣告的[元素名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。

## <a name="example"></a>範例

下列範例顯示的 `Function` 程式會定義兩個參數。

[!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]

## <a name="see-also"></a>請參閱

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [屬性概觀](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [操作說明：在程式碼內中斷和合併陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)

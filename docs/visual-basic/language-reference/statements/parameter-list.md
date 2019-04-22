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
ms.openlocfilehash: 651f08812032aa1c5aacc04fdb3d7f491f12b607
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836281"
---
# <a name="parameter-list-visual-basic"></a>參數清單 (Visual Basic)
指定呼叫時，必須要有一個程序的參數。 以逗號分隔多個參數。 以下是一個參數的語法。  
  
## <a name="syntax"></a>語法  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## <a name="parts"></a>組件  
 `attributelist`  
 選擇性。 將套用至這個參數的屬性清單。 您必須將括[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)角括弧 ("`<`"和"`>`")。  
  
 `Optional`  
 選擇性。 指定呼叫程序時不需要此參數。  
  
 `ByVal`  
 選擇性。 指定的程序無法取代或重新指派對應的引數呼叫的程式碼中的變數項目。  
  
 `ByRef`  
 選擇性。 指定程序呼叫的程式碼本身相同的方式可以修改呼叫程式碼中的基礎變數項目。  
  
 `ParamArray`  
 選擇性。 指定的參數清單中的最後一個參數是選擇性的項目指定的資料類型的陣列。 這可讓呼叫的程式碼，將任意數目的引數傳遞至程序。  
  
 `parametername`  
 必要項。 表示參數的本機變數的名稱。  
  
 `parametertype`  
 需要`Option Strict`是`On`。 表示參數的本機變數的資料型別。  
  
 `defaultvalue`  
 所需的`Optional`參數。 任何會評估為參數的資料類型的常數或常數運算式。 如果類型是`Object`，或類別、 介面、 陣列或結構，預設值只能是`Nothing`。  
  
## <a name="remarks"></a>備註  
 參數是以括號括住，並以逗號分隔。 參數可以宣告任何資料類型。 如果您未指定`parametertype`，則會預設為`Object`。  
  
 當呼叫端程式碼會呼叫程序時，會傳遞*引數*至每個必要參數。 如需詳細資訊，請參閱 <<c0> [ 參數之間的差異和引數](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md)。  
  
 呼叫程式碼將傳遞給每個參數的引數是在呼叫程式碼中的基礎項目指標。 如果此項目*非變換*（常數、 常值、 列舉型別或運算式），就無法變更它的任何程式碼。 如果它是*變數*項目 （宣告的變數、 欄位、 屬性、 陣列元素或結構項目），呼叫程式碼可以將它變更。 如需詳細資訊，請參閱 <<c0> [ 修改之間的差異和不可修改引數](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)。  
  
 如果變數的項目都會傳遞`ByRef`，程序可以一併變更它。 如需詳細資訊，請參閱 <<c0> [ 差異之間傳遞的引數的值和傳址](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)。  
  
## <a name="rules"></a>規則  
  
-   **括號。** 如果您指定的參數清單時，您必須將它括在括號中。 如果沒有任何參數，您仍然可以使用括號括住空白清單。 這可以釐清的項目一個程序，以改善您的程式碼的可讀性。  
  
-   **選擇性參數。** 如果您使用`Optional`參數的修飾詞，所有後續的參數清單中必須也是選擇性的並會宣告可透過`Optional`修飾詞。  
  
     每個選擇性參數宣告必須提供`defaultvalue`子句。  
  
     如需詳細資訊，請參閱 <<c0> [ 選擇性參數](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)。  
  
-   **參數陣列。** 您必須指定`ByVal`針對`ParamArray`參數。  
  
     您無法同時使用`Optional`和`ParamArray`相同的參數清單中。  
  
     如需詳細資訊，請參閱 <<c0> [ 參數陣列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)。  
  
-   **傳遞機制。** 每個引數的預設機制是`ByVal`，這表示程序無法變更基礎變數的項目。 不過，如果項目是參考類型，程序可以修改內容或成員的基礎物件，即使它不能取代或重新指派物件本身。  
  
-   **參數名稱。** 如果參數的資料類型是陣列，請遵循`parametername`立即以括號。 如需有關參數名稱的詳細資訊，請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
## <a name="example"></a>範例  
 下列範例所示`Function`定義兩個參數的程序。  
  
 [!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [屬性概觀](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [如何：在程式碼內中斷和合併陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)

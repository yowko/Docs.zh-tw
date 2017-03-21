---
title: "參數清單 (Visual Basic) |Microsoft 文件"
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
- Visual Basic code, procedures
- parameters, Visual Basic
- parameters, lists
- parameter lists
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures, parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
caps.latest.revision: 19
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: abadaa8e035bfa4c92acc30ab633d6a7e958676c
ms.lasthandoff: 03/13/2017

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
 選擇項。 將套用至這個參數的屬性清單。 您必須將[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)角括弧括住 (「`<`"和"`>`")。  
  
 `Optional`  
 選擇項。 指定在呼叫程序時不需要此參數。  
  
 `ByVal`  
 選擇項。 指定的程序無法取代或重新指派對應的引數呼叫的程式碼中的變數項目。  
  
 `ByRef`  
 選擇項。 指定程序呼叫的程式碼本身的相同方式可以修改基礎的變數項目。  
  
 `ParamArray`  
 選擇項。 指定參數清單中的最後一個參數是選擇性的項目指定的資料類型的陣列。 這可讓任意數目的引數傳遞至程序呼叫的程式碼。  
  
 `parametername`  
 必要項。 代表參數的本機變數的名稱。  
  
 `parametertype`  
 只有在`Option Strict`是`On`。 代表參數的本機變數的資料型別。  
  
 `defaultvalue`  
 所需的`Optional`參數。 任何評估為參數的資料類型的常數或常數運算式。 如果類型是`Object`，或類別、 介面、 陣列、 或結構，預設值只能是`Nothing`。  
  
## <a name="remarks"></a>備註  
 參數會以括號括住並以逗號分隔。 參數可以宣告任何資料類型。 如果您未指定`parametertype`，其預設值為`Object`。  
  
 當呼叫程式碼呼叫的程序時，會傳遞*引數*至每個必要參數。 如需詳細資訊，請參閱[參數之間的差異和引數](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md)。  
  
 呼叫的程式碼傳遞至每個參數的引數是在呼叫程式碼中對應項目的指標。 如果此項目是*非變換*（常數、 常值、 列舉型別或運算式），就無法變更它的任何程式碼。 如果是*變數*項目 （宣告的變數、 欄位、 屬性、 陣列元素或結構項目），呼叫程式碼可以變更它。 如需詳細資訊，請參閱[修改之間的差異和不可修改引數](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)。  
  
 如果變數項目傳遞`ByRef`，程序可以變更它。 如需詳細資訊，請參閱[差異之間傳遞引數的值和傳址](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)。  
  
## <a name="rules"></a>規則  
  
-   **括號括住。** 如果您指定的參數清單，您必須將它括在括號中。 如果不有任何參數，您仍然可以使用括號圍住空的清單。 這可以改善程式碼的可讀性釐清的項目是程序。  
  
-   **選擇性參數。** 如果您使用`Optional`參數修飾詞，所有後續的參數清單中必須是選擇性的可以使用宣告`Optional`修飾詞。  
  
     每個選擇性參數宣告必須提供`defaultvalue`子句。  
  
     如需詳細資訊，請參閱[選擇性參數](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)。  
  
-   **參數陣列。** 您必須指定`ByVal`的`ParamArray`參數。  
  
     您無法同時使用`Optional`和`ParamArray`相同的參數清單中。  
  
     如需詳細資訊，請參閱[參數陣列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)。  
  
-   **傳遞機制。** 每個引數的預設機制是`ByVal`，這表示程序無法變更對應的變數項目。 不過，如果項目是參考型別，此程序可以修改內容或成員的基礎物件，即使它無法取代或重新指派物件本身。  
  
-   **參數名稱。** 如果參數的資料型別是陣列，請遵循`parametername`立即以括號。 如需有關參數名稱的詳細資訊，請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
## <a name="example"></a>範例  
 下列範例所示`Function`定義兩個參數的程序。  
  
 [!code-vb[VbVbalrStatements #&2;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-list_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.InteropServices.DllImportAttribute></xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [屬性概觀](../../../visual-basic/programming-guide/concepts/attributes/index.md)   
 [如何：在程式碼內中斷和合併陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)

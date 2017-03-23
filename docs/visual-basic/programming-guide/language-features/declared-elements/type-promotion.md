---
title: "類型提升 (Visual Basic) |Microsoft 文件"
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
- declared elements, scope
- visibility, declared elements
- Partial keyword, unexpected results with type promotion
- scope, declared elements
- scope, Visual Basic
- type promotion
- declared elements, visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
caps.latest.revision: 17
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
ms.openlocfilehash: d732e765fc28eaedc0deab477dbf9955a40e97c9
ms.lasthandoff: 03/13/2017

---
# <a name="type-promotion-visual-basic"></a>類型提升 (Visual Basic)
當您宣告程式設計項目在模組中，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提升其範圍包含模組的命名空間。 這稱為*輸入促銷*。  
  
 下列範例會顯示模組的基本架構定義，該模組的兩個成員。  
  
 [!code-vb[VbVbalrDeclaredElements #&1;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_1.vb)]  
  
 內`projModule`、 程式設計在模組層級宣告的項目會提升至`projNamespace`。 在上述範例中，`basicEnum`和`innerClass`會升級，但`numberSub`不是，因為它不會在模組層級宣告。  
  
## <a name="effect-of-type-promotion"></a>型別提升的效果  
 型別提升的效果是限定性條件字串不需要包含模組名稱。 下列範例會在上述範例中的兩個呼叫程序。  
  
 [!code-vb[VbVbalrDeclaredElements #&2;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_2.vb)]  
  
 在上述範例中，第一次呼叫會使用完整限定性條件字串。 不過，這是不需要因為型別提升。 第二個呼叫，也存取模組成員但不包括`projModule`中限定性條件字串。  
  
## <a name="defeat-of-type-promotion"></a>型別提升失敗  
 如果命名空間已經有具有相同名稱做為模組成員的成員，型別提升將無效的模組成員。 下列範例示範基本架構定義的列舉型別與相同的命名空間內的模組。  
  
 [!code-vb[VbVbalrDeclaredElements #&3;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_3.vb)]  
  
 在上述範例中，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]無法升級類別`abc`至`thisNameSpace`因為已經有具有相同名稱的命名空間層級的列舉。 若要存取`abcSub`，您必須使用完整限定性條件字串`thisNamespace.thisModule.abc.abcSub`。 不過，類別`xyz`仍升級，而且您可以存取`xyzSub`使用較短的限定性條件字串`thisNamespace.xyz.xyzSub`。  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a>部分類型的型別提升失敗  
 如果類別或結構，在模組內使用[部分](../../../../visual-basic/language-reference/modifiers/partial.md)關鍵字、 型別提升會自動失效該類別或結構中，命名空間是否具有相同名稱的成員。 在模組中的其他項目是仍可進行型別提升。  
  
 **結果。** 部分定義的型別提升失敗可能會造成非預期的結果，甚至是編譯器錯誤。 下列範例示範基本架構的部分定義的類別，一個是在模組內。  
  
 [!code-vb[VbVbalrDeclaredElements #&4;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_4.vb)]  
  
 在上述範例中，開發人員可能預期要合併兩個部分定義的編譯器`sampleClass`。 不過，編譯器不會考慮升級部分定義內`sampleModule`。 如此一來，它會嘗試編譯兩個個別且不同的類別，名為`sampleClass`但具有不同的限定性條件路徑。  
  
 只有在完整路徑相同時，編譯器才會合併部分定義。  
  
## <a name="recommendations"></a>建議  
 下列建議表示良好的程式設計作法。  
  
-   **唯一的名稱。** 當您的程式項目命名的完整控制權，永遠是最好各處使用唯一的名稱。 相同的名稱需要額外的限定性條件，而且可以讓您的程式碼更難閱讀。 它們也可能會導致難以察覺的錯誤和非預期的結果。  
  
-   **完整路徑名稱。** 當您正在使用模組和其他項目相同的命名空間中時，最安全的方法就是一律使用完整限定性條件的所有程式設計項目。 如果型別提升將無效的模組成員，且不完整限定該成員，您可能不小心存取不同的程式設計項目。  
  
## <a name="see-also"></a>另請參閱  
 [Module 陳述式](../../../../visual-basic/language-reference/statements/module-statement.md)   
 [Namespace 陳述式](../../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [部分](../../../../visual-basic/language-reference/modifiers/partial.md)   
 [在 Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [如何︰ 控制變數的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)   
 [對已宣告項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

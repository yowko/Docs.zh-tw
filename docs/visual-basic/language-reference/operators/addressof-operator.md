---
title: AddressOf 運算子
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: e88520bd7e731a35b98c1d40c5210dc5d1314911
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350275"
---
# <a name="addressof-operator-visual-basic"></a>AddressOf 運算子 (Visual Basic)
建立參考特定程式的委派實例。  
  
## <a name="syntax"></a>語法  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a>組件  
 `procedurename`  
 必要。 指定新建立的委派所要參考的程式。  
  
## <a name="remarks"></a>備註  
 `AddressOf` 運算子會建立指向 `procedurename`所指定之子函數或函式的委派。 當指定的程式是實例方法時，委派會同時參考實例和方法。 然後，當叫用委派時，會呼叫指定實例的指定方法。  
  
 `AddressOf` 運算子可用來做為委派函式的運算元，或可用於可以由編譯器決定委派類型的內容中。  
  
## <a name="example"></a>範例  
 這個範例會使用 `AddressOf` 運算子來指定委派，以處理按鈕的 `Click` 事件。  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a>範例  
 下列範例會使用 `AddressOf` 運算子來指定執行緒的啟動函數。  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>另請參閱

- [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)
- [委派](../../../visual-basic/programming-guide/language-features/delegates/index.md)

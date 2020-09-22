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
ms.openlocfilehash: edce7d4a2268bd311045ea4972672fe8fd2600ea
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874890"
---
# <a name="addressof-operator-visual-basic"></a>AddressOf 運算子 (Visual Basic)

建立參考特定程式的委派實例。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a>組件  

 `procedurename`  
 必要。 指定新建立之委派所參考的程式。  
  
## <a name="remarks"></a>備註  

 `AddressOf`運算子會建立指向所指定之子函數或函式的委派 `procedurename` 。 當指定的程式是實例方法時，委派會同時參考實例和方法。 然後，當叫用委派時，會呼叫指定實例的指定方法。  
  
 `AddressOf`運算子可以當做委派函式的運算元使用，也可以用在可由編譯器決定委派類型的內容中。  
  
## <a name="example"></a>範例  

 這個範例會使用 `AddressOf` 運算子來指定委派來處理按鈕的 `Click` 事件。  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a>範例  

 下列範例會使用 `AddressOf` 運算子來指定執行緒的啟動函式。  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>另請參閱

- [Declare Statement](../statements/declare-statement.md)
- [Function 陳述式](../statements/function-statement.md)
- [Sub 陳述式](../statements/sub-statement.md)
- [委派](../../programming-guide/language-features/delegates/index.md)

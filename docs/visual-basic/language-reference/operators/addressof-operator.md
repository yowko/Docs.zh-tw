---
title: AddressOf 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: 9d8515b6d5b0caf3552ed05a7e0cd4a271efaf54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608342"
---
# <a name="addressof-operator-visual-basic"></a>AddressOf 運算子 (Visual Basic)
建立參考特定程序的程序委派執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a>組件  
 `procedurename`  
 必要項。 指定新建立的程序委派所要參考的程序。  
  
## <a name="remarks"></a>備註  
 `AddressOf`運算子會建立指向所指定的函式的函式委派`procedurename`。 指定的程序時的執行個體方法然後函式委派是指執行個體和方法。 然後，叫用的函式委派時指定的執行個體的指定的方法呼叫。  
  
 `AddressOf`運算子可用來當做委派建構函式的運算元，或用於可由編譯器決定委派型別所在的內容。  
  
## <a name="example"></a>範例  
 這個範例會使用`AddressOf`運算子來指定委派，以便處理`Click`按鈕的事件。  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a>範例  
 下列範例會使用`AddressOf`運算子來指定在執行緒啟動函式。  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>另請參閱

- [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)
- [委派](../../../visual-basic/programming-guide/language-features/delegates/index.md)

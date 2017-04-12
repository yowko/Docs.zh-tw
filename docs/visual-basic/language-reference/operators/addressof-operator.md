---
title: "AddressOf 運算子 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- AddressOf
- vb.AddressOf
dev_langs:
- VB
helpviewer_keywords:
- AddressOf operator
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 04a7c5be9b890faea561c28715093a271cf9eaa8
ms.lasthandoff: 03/13/2017

---
# <a name="addressof-operator-visual-basic"></a>AddressOf 運算子 (Visual Basic)
建立參考的特定程序的程序委派執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
  
AddressOf procedurename  
```  
  
## <a name="parts"></a>組件  
 `procedurename`  
 必要項。 指定新建立的程序委派所參考的程序。  
  
## <a name="remarks"></a>備註  
 `AddressOf`運算子會建立指向所指定的函式的函式委派`procedurename`。 當指定的程序是執行個體方法然後函式委派參考執行個體和方法。 然後，叫用的函式委派時指定的執行個體的指定的方法呼叫。  
  
 `AddressOf`運算子可用來當做委派建構函式的運算元，或用於可以由編譯器決定委派型別中的內容。  
  
## <a name="example"></a>範例  
 這個範例會使用`AddressOf`運算子來指定委派以處理`Click`按鈕的事件。  
  
 [!code-vb[VbVbalrDelegates #&8;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]  
  
## <a name="example"></a>範例  
 下列範例會使用`AddressOf`運算子來指定在執行緒啟動函式。  
  
 [!code-vb[VbVbalrDelegates #&9;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [委派](../../../visual-basic/programming-guide/language-features/delegates/index.md)

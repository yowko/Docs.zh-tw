---
title: "AddressOf&quot; 運算元必須是 （沒有括號） 的方法名稱 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30577
- bc30577
dev_langs:
- VB
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
caps.latest.revision: 10
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
ms.openlocfilehash: 04103fe23ee55bb751d9604ef74614edeead8886
ms.lasthandoff: 03/13/2017

---
# <a name="39addressof39-operand-must-be-the-name-of-a-method-without-parentheses"></a>AddressOf' 運算元必須是方法的 （沒有括號） 名稱
`AddressOf` 運算子會建立參考特定程序的程序委派執行個體。 語法為，如下所示。  
  
 `AddressOf` `procedurename`  
  
 插入下列引數括`AddressOf`，不需要的地方。  
  
 **錯誤識別碼︰** BC30577  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  移除引數下前後的括號`AddressOf`。  
  
2.  請確定引數是方法名稱。  
  
## <a name="see-also"></a>另請參閱  
 [AddressOf 運算子](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [委派](../../../visual-basic/programming-guide/language-features/delegates/index.md)

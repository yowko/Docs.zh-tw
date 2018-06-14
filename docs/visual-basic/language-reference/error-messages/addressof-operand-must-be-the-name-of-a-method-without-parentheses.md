---
title: '&#39;AddressOf&#39;運算元必須是 （沒有括號） 的方法名稱'
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: 701d86e03d9b14236eec8436d99ec40cebbbcd44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583808"
---
# <a name="39addressof39-operand-must-be-the-name-of-a-method-without-parentheses"></a>&#39;AddressOf&#39;運算元必須是 （沒有括號） 的方法名稱
`AddressOf` 運算子會建立參考特定程序的程序委派執行個體。 語法如下所示。  
  
 `AddressOf` `procedurename`  
  
 插入括弧括住引數下`AddressOf`，沒有任何需要的地方。  
  
 **錯誤 ID:** BC30577  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  移除引數下前後的括號`AddressOf`。  
  
2.  請確定引數是方法名稱。  
  
## <a name="see-also"></a>另請參閱  
 [AddressOf 運算子](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [委派](../../../visual-basic/programming-guide/language-features/delegates/index.md)

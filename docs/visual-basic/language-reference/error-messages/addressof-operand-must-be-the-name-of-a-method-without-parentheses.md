---
title: AddressOf' 運算元必須是方法名稱 (沒有括號)
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: b8c67c2390df91c6a4af66e020365544e6bf369b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59323820"
---
# <a name="addressof-operand-must-be-the-name-of-a-method-without-parentheses"></a>AddressOf' 運算元必須是方法名稱 (沒有括號)
`AddressOf` 運算子會建立參考特定程序的程序委派執行個體。 語法如下所示。  
  
 `AddressOf` `procedurename`  
  
 插入下列引數括`AddressOf`，沒有任何需要的地方。  
  
 **錯誤 ID:** BC30577  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 移除引數下前後的括號`AddressOf`。  
  
2. 請確定引數的方法名稱。  
  
## <a name="see-also"></a>另請參閱

- [AddressOf 運算子](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [委派](../../../visual-basic/programming-guide/language-features/delegates/index.md)

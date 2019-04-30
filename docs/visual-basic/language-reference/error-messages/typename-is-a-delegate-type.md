---
title: "'<typename>' 是委派類型"
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: c308805f5e73d740ff18a40d95b9cc2576ac95fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013591"
---
# <a name="typename-is-a-delegate-type"></a>'\<類型名稱 >' 是委派型別
'\<類型名稱 >' 是委派型別。 委派建構允許只使用單一 AddressOf 運算式做為引數清單。 通常可以使用 AddressOf 運算式，而不是委派建構。  
  
 A`New`子句建立委派類別的執行個體提供無效的引數清單之委派建構函式。  
  
 您可以提供只會有一個`AddressOf`運算式建立新的委派執行個體時。  
  
 如果您沒有傳遞任何引數的委派建構函式，如果傳遞多個引數，或如果您傳遞單一引數，不是有效，此錯誤可能會造成`AddressOf`運算式。  
  
 **錯誤 ID:** BC32008  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 使用單一`AddressOf`委派類別中的引數清單中的運算式`New`子句。  
  
## <a name="see-also"></a>另請參閱

- [New 運算子](../../../visual-basic/language-reference/operators/new-operator.md)
- [AddressOf 運算子](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [委派](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [如何：叫用委派方法](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)

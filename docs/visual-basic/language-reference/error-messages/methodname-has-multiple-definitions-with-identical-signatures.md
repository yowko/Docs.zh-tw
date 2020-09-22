---
title: "'<methodname>' 有多個具相同簽名碼的定義"
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: 2934a5666c55e1ca57b91ab86585261e6d71a2d3
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873734"
---
# <a name="methodname-has-multiple-definitions-with-identical-signatures"></a>'\<methodname>' 有多個具相同簽名碼的定義

`Function`或程式 `Sub` 聲明使用相同的程式名稱和引數清單做為先前的宣告。 其中一個可能的原因是嘗試多載原始程式。 多載程式必須有不同的引數清單。  
  
 **錯誤識別碼：** BC30269  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請變更程式名稱或引數清單，或移除重複的宣告。  
  
## <a name="see-also"></a>另請參閱

- [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [多載化程序的考慮因素](../../programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)

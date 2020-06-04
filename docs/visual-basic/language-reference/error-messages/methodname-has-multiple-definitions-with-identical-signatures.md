---
title: "'<methodname>' 有多個具相同簽名碼的定義"
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: 3b397711cc2fb1fd0c1dfd76899b162ab5fc1542
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397229"
---
# <a name="methodname-has-multiple-definitions-with-identical-signatures"></a>'\<methodname>' 有多個具相同簽名碼的定義
或程式宣告會 `Function` `Sub` 使用與先前宣告相同的程式名稱和引數清單。 其中一個可能的原因是嘗試多載原始程式。 多載程式必須有不同的引數清單。  
  
 **錯誤識別碼：** BC30269  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請變更程式名稱或引數清單，或移除重複的宣告。  
  
## <a name="see-also"></a>另請參閱

- [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [多載化程序的考慮因素](../../programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)

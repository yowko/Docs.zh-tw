---
title: 陳述式在具有多行的方法 lambda 內無效
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: f3c43d640259d5e1af545e2610088aab5d70453d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396242"
---
# <a name="statement-is-not-valid-inside-a-methodmultiline-lambda"></a>陳述式在方法/多行 Lambda 內無效
語句在 `Sub` 、 `Function` 、屬性 `Get` 或屬性程式中無效 `Set` 。 有些語句可以放在模組或類別層級。 其他專案（例如 `Option Strict` ）必須位於命名空間層級，且在其他所有宣告之前。  
  
 **錯誤識別碼：** BC30024  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請移除程式中的語句。  
  
## <a name="see-also"></a>另請參閱

- [Sub 陳述式](../statements/sub-statement.md)
- [Function 陳述式](../statements/function-statement.md)
- [Get 陳述式](../statements/get-statement.md)
- [Set 語句](../statements/set-statement.md)

---
title: 無效的模式字串
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: 7390b9b32eea248969813b52f8d9799798718de0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59298678"
---
# <a name="invalid-pattern-string"></a>無效的模式字串
在搜尋的 `Like` 作業中指定的模式字串無效。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請檢閱清單運算式的有效字元。  
  
2. 在模式範圍中，確定起始範圍字元小於結束範圍字元，如同在 `[a-z]`。  
  
3. 在模式範圍中，確定沒有相鄰的多個連字號，如同在 `[a--z]`。  
  
4. 以右括弧結束模式範圍。  
  
## <a name="see-also"></a>另請參閱

- [Like 運算子](../../visual-basic/language-reference/operators/like-operator.md)

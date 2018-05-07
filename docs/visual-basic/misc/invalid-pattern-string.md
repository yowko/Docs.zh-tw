---
title: 無效的模式字串
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: 4905f74683989d8e1a2b041a8af4af4d7432ffab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="invalid-pattern-string"></a>無效的模式字串
在搜尋的 `Like` 作業中指定的模式字串無效。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請檢閱清單運算式的有效字元。  
  
2.  在模式範圍中，確定起始範圍字元小於結束範圍字元，如同在 `[a-z]`。  
  
3.  在模式範圍中，確定沒有相鄰的多個連字號，如同在 `[a--z]`。  
  
4.  以右括弧結束模式範圍。  
  
## <a name="see-also"></a>另請參閱  
 [Like 運算子](../../visual-basic/language-reference/operators/like-operator.md)

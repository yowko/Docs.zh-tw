---
title: 無效的模式字串
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: 5ef12ac27e96205f9ef1c964293847f56b11cb78
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090686"
---
# <a name="invalid-pattern-string"></a>無效的模式字串

在搜尋的 `Like` 作業中指定的模式字串無效。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請檢閱清單運算式的有效字元。  
  
2. 在模式範圍中，確定起始範圍字元小於結束範圍字元，如同在 `[a-z]`。  
  
3. 在模式範圍中，確定沒有相鄰的多個連字號，如同在 `[a--z]`。  
  
4. 以右括弧結束模式範圍。  
  
## <a name="see-also"></a>另請參閱

- [Like 運算子](../language-reference/operators/like-operator.md)

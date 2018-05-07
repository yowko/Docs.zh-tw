---
title: '&#39;模組&#39;陳述式只可以發生在檔案或命名空間層級'
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: 53199c2d7081445dc5490d5c54c98f93ee7522eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="39module39-statements-can-occur-only-at-file-or-namespace-level"></a>&#39;模組&#39;陳述式只可以發生在檔案或命名空間層級
`Module` 陳述式必須出現在原始程式檔頂端之後立即`Option`和`Imports`陳述式、 全域屬性及命名空間宣告，但所有其他宣告前面。  
  
 **錯誤 ID:** BC30617  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   移動`Module`陳述式來命名空間宣告或原始檔的頂端。  
  
## <a name="see-also"></a>另請參閱  
 [Module 陳述式](../../../visual-basic/language-reference/statements/module-statement.md)

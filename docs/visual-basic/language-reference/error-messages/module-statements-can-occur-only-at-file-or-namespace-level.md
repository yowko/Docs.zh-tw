---
title: '&#39;模組 &#39;陳述式只可以發生在檔案或命名空間層級'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 61fe12fbd7d20e6cd2b6bc464e7fc3293150213b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="39module39-statements-can-occur-only-at-file-or-namespace-level"></a>&#39;模組 &#39;陳述式只可以發生在檔案或命名空間層級
`Module`陳述式必須出現在原始程式檔頂端之後立即`Option`和`Imports`陳述式、 全域屬性及命名空間宣告，但所有其他宣告前面。  
  
 **錯誤 ID:** BC30617  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   移動`Module`陳述式來命名空間宣告或原始檔的頂端。  
  
## <a name="see-also"></a>另請參閱  
 [Module 陳述式](../../../visual-basic/language-reference/statements/module-statement.md)

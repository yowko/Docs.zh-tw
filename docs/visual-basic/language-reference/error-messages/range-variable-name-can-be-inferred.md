---
title: 只能從不含引數的簡單或限定名稱來推斷範圍變數名稱
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5c986fcf188482c526c53ddf3019cec5163d0b62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>只能從不含引數的簡單或限定名稱來推斷範圍變數名稱
LINQ 查詢中包含採用一或多個引數的程式設計項目。 編譯器會無法推斷範圍變數，從該程式設計項目。  
  
 **錯誤 ID:** BC36599  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  提供明確的變數名稱的程式設計項目，如下列程式碼所示：  
  
```  
Dim query = From var1 In collection1   
            Select VariableAlias= SampleFunction(var1), var1  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)

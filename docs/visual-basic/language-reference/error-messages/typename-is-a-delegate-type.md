---
title: "&#39;&lt;typename&gt;&#39; 是委派型別"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords: BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9428f0ac321b90e36d4d987381ed69b6c968894c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="39lttypenamegt39-is-a-delegate-type"></a>&#39;&lt;typename&gt;&#39; 是委派型別
'\<類型名稱 >' 是委派型別。 委派建構允許只有單一 AddressOf 運算式作為引數清單。 通常可以使用 AddressOf 運算式，而不是委派建構。  
  
 A`New`子句建立委派類別的執行個體提供給委派建構函式無效的引數清單。  
  
 您可以提供只有一個`AddressOf`運算式建立新的委派執行個體時。  
  
 如果您沒有傳遞任何引數的委派建構函式，如果您將多個引數，或如果傳遞單一引數，不是有效，此錯誤可能會造成`AddressOf`運算式。  
  
 **錯誤 ID:** BC32008  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   使用單一`AddressOf`委派類別中的引數清單中的運算式`New`子句。  
  
## <a name="see-also"></a>另請參閱  
 [New 運算子](../../../visual-basic/language-reference/operators/new-operator.md)  
 [AddressOf 運算子](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [委派](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [如何：叫用委派方法](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)

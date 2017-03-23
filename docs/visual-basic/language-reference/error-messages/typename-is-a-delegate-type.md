---
title: "&quot;&lt;typename&gt;&quot; 是委派型別 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32008
- vbc32008
dev_langs:
- VB
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
caps.latest.revision: 11
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3d6cc283f7e9815eb9b723a450731998f14b3424
ms.lasthandoff: 03/13/2017

---
# <a name="39lttypenamegt39-is-a-delegate-type"></a>'&lt;typename&gt;' 是委派型別
'\<typename >' 是委派型別。 委派建構允許只有單一 AddressOf 運算式做為引數清單。 通常可以使用 AddressOf 運算式，而不是委派建構。  
  
 A`New`子句建立委派類別的執行個體無效的引數清單提供給委派建構函式。  
  
 您可以提供只會有一個`AddressOf`運算式時建立新的委派執行個體。  
  
 如果您沒有傳遞任何引數的委派建構函式，如果您傳遞多個引數，或如果您傳遞單一引數，不是有效，此錯誤可能會造成`AddressOf`運算式。  
  
 **錯誤識別碼︰** BC32008  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   使用單一`AddressOf`委派類別中的引數清單中的運算式`New`子句。  
  
## <a name="see-also"></a>另請參閱  
 [New 運算子](../../../visual-basic/language-reference/operators/new-operator.md)   
 [AddressOf 運算子](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [委派](../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [如何：叫用委派方法](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)

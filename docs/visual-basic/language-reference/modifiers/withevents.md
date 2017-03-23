---
title: "WithEvents (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.WithEvents
- WithEvents
dev_langs:
- VB
helpviewer_keywords:
- WithEvents keyword
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
caps.latest.revision: 17
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
ms.openlocfilehash: 708cf6fec78faf2c7a5959a3a2694d237d728882
ms.lasthandoff: 03/13/2017

---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
指定一或多個宣告的成員變數參考可以引發事件的類別執行個體。  
  
## <a name="remarks"></a>備註  
 當變數定義使用`WithEvents`，您可以以宣告方式指定，則方法會處理使用變數的事件`Handles`關鍵字。  
  
 您可以使用`WithEvents`只能在類別或模組層級。 這表示宣告內容`WithEvents`變數必須是類別或模組，且不能原始程式檔、 命名空間、 結構或程序。  
  
 您不能使用`WithEvents`結構成員上。  
  
 您可以宣告只有個別變數 — 不陣列 — 與`WithEvents`。  
  
## <a name="rules"></a>規則  
  
-   **項目型別。** 您必須宣告`WithEvents`變數是物件變數，如此可以接受以類別的執行個體。 不過，您無法宣告這些`Object`。 您必須宣告為可引發事件的特定類別。  
  
 `WithEvents`修飾詞可用於此內容︰ [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>另請參閱  
 [控制代碼](../../../visual-basic/language-reference/statements/handles-clause.md)   
 [關鍵字](../../../visual-basic/language-reference/keywords/index.md)   
 [事件](../../../visual-basic/programming-guide/language-features/events/index.md)

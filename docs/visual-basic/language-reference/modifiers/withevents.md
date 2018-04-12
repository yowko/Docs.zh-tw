---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 68a58fd130c04f2ed0cb1f2e5b9250f6c85f120d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
指定一或多個宣告的成員變數會參照可引發事件類別的執行個體。  
  
## <a name="remarks"></a>備註  
 當變數定義使用`WithEvents`，您可以以宣告方式指定，則方法會處理使用的變數的事件`Handles`關鍵字。  
  
 您可以使用`WithEvents`只能在類別或模組層級。 這表示宣告內容`WithEvents`變數必須是類別或模組，而且不能是原始程式檔、 命名空間、 結構、 或程序。  
  
 您無法使用`WithEvents`結構成員上。  
  
 您可以宣告只有個別變數 — 不陣列 — 與`WithEvents`。  
  
## <a name="rules"></a>規則  
  
-   **項目型別。** 您必須宣告`WithEvents`為物件變數使其可接受的變數類別的執行個體。 不過，您無法宣告它們當做`Object`。 您必須宣告為可引發事件的特定類別。  
  
 `WithEvents`修飾詞可用於此內容： [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>另請參閱  
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [關鍵字](../../../visual-basic/language-reference/keywords/index.md)  
 [事件](../../../visual-basic/programming-guide/language-features/events/index.md)

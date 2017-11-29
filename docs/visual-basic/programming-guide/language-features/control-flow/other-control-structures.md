---
title: "其他控制結構 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 09e59d25b3b2fc89026295e8500c30dad7b75086
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="other-control-structures-visual-basic"></a>其他控制結構 (Visual Basic)
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]提供可協助您控制結構的資源處置或減少您必須重複的物件參考的次數。  
  
## <a name="usingend-using-construction"></a>使用...使用建構的結束  
 `Using...End Using`建構會建立陳述式區塊，請在其中使用的資源，例如 SQL 連接。 您可以選擇性地取得的資源`Using`陳述式。 當您結束`Using`區塊，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]使其可供其他程式碼以使用自動處置資源。 資源必須是本機和處置。 如需詳細資訊，請參閱 [Using 陳述式](../../../../visual-basic/language-reference/statements/using-statement.md)。  
  
## <a name="withend-with-construction"></a>與...建構的結尾  
 `With...End With`建構可讓您一次指定的物件參考，然後再執行一系列陳述式來存取其成員。 這可以簡化您的程式碼，並改善效能，因為[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]不需要重新建立每個陳述式會存取它的參考。 如需詳細資訊，請參閱[與...With 陳述式](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)。  
  
## <a name="see-also"></a>另請參閱  
 [控制流程](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [決策結構](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [迴圈結構](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [巢狀控制結構](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Using 陳述式](../../../../visual-basic/language-reference/statements/using-statement.md)  
 [With...End With 陳述式](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)

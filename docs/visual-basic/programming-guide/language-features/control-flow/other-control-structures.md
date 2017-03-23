---
title: "其他控制結構 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
caps.latest.revision: 19
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
ms.openlocfilehash: 639571b493037f26951bd8fbf140d7bce3244889
ms.lasthandoff: 03/13/2017

---
# <a name="other-control-structures-visual-basic"></a>其他控制結構 (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供可協助您控制結構處置資源，或減少您必須重複執行的物件參考的次數。  
  
## <a name="usingend-using-construction"></a>使用...結束使用結構  
 `Using...End Using`建構建立陳述式區塊，請在其中使用的 SQL 連線之類的資源。 您可以選擇性地取得與資源`Using`陳述式。 當您結束`Using`區塊，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]使其可供其他程式碼以使用自動處置資源。 資源必須是本機和可處置。 如需詳細資訊，請參閱[Using 陳述式](../../../../visual-basic/language-reference/statements/using-statement.md)。  
  
## <a name="withend-with-construction"></a>與...結尾結構  
 `With...End With`建構可讓您一次指定的物件參考，然後再執行一系列的陳述式來存取其成員。 這可以簡化您的程式碼，並改善效能，因為[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]不需要重新建立每個陳述式中存取它的參考。 如需詳細資訊，請參閱[與...With 陳述式](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)。  
  
## <a name="see-also"></a>另請參閱  
 [控制流程](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [決策結構](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [迴圈結構](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [巢狀的控制結構](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Using 陳述式](../../../../visual-basic/language-reference/statements/using-statement.md)   
 [With...End With 陳述式](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)

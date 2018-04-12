---
title: 溢位 (Visual Basic 執行階段錯誤)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d1908ad576a499e79102aff23e3e2f11d7d99d52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="overflow-visual-basic-run-time-error"></a>溢位 (Visual Basic 執行階段錯誤)
嘗試設定超出限制的指派的目標時，就會造成溢位。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請確定指派、 計算和資料類型轉換不會太大，而無法表示變數的值，該類型所允許的範圍內，並將值指派給類型的變數的結果可以保存較大範圍的值如有必要。  
  
2.  請確定屬性的指派，符合所建立的屬性的範圍。  
  
3.  請確定強制轉換為整數的計算中使用的數字，並沒有比整數較大的結果。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Int32.MaxValue?displayProperty=nameWithType>  
 <xref:System.Double.MaxValue?displayProperty=nameWithType>  
 [資料類型](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [錯誤類型](../../../visual-basic/programming-guide/language-features/error-types.md)

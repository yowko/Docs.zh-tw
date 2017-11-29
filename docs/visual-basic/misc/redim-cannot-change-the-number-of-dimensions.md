---
title: "&#39;ReDim &#39;無法變更維度的數目"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8cf3713c72bd07803935065780e894c130911a6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="39redim39-cannot-change-the-number-of-dimensions"></a>&#39;ReDim &#39;無法變更維度的數目
作業嘗試使用 `ReDim` 陳述式變更陣列的陣序 (維度數目)。 `ReDim` 可以變更已正式宣告之陣列的一或多個維度大小，但無法變更陣列的陣序。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請確定您是要變更陣列的陣序，而不是其維度的大小，並且請盡可能地使用 `Dim` 來宣告具有所需陣序的新陣列。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 中的陣列](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [在 Visual Basic 中的陣列維度](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [ReDim 陳述式](../../visual-basic/language-reference/statements/redim-statement.md)  
 [Dim 陳述式](../../visual-basic/language-reference/statements/dim-statement.md)

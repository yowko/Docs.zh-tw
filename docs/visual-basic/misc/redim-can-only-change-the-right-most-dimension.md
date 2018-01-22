---
title: "&#39;ReDim &#39;只能變更最右側的維度"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 752e0e54c48b3b348a477787e5e911f1b1777667
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="39redim39-can-only-change-the-right-most-dimension"></a>&#39;ReDim &#39;只能變更最右側的維度
`ReDim` 陳述式嘗試使用 `Preserve` 關鍵字來變更不是最後一個維度的陣列的維度。 使用 `Preserve`時，您只能調整陣列的最後一個維度。 對於所有其他維度，您必須指定與現有陣列相同的大小。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請移除 `Preserve` 關鍵字。  
  
## <a name="see-also"></a>請參閱  
 [Visual Basic 中的陣列](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [在 Visual Basic 中的陣列維度](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [ReDim 陳述式](../../visual-basic/language-reference/statements/redim-statement.md)  
 [Dim 陳述式](../../visual-basic/language-reference/statements/dim-statement.md)  
 [保留-刪除](http://msdn.microsoft.com/library/91badeab-b4e0-48b6-92c9-9f0c8f995d81)

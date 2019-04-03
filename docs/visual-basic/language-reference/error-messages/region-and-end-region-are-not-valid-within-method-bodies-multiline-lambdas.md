---
title: "'#Region' 和 ' #End Region' 陳述式不是在方法主體 / 多行 lambda 中無效"
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: deef3de645040d7c3d95b1a6c8a25fcf10de881b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842703"
---
# <a name="region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="537e3-102">'#Region' 及 '#End Region' 陳述式在方法主體/多行 Lambda 中無效</span><span class="sxs-lookup"><span data-stu-id="537e3-102">'#Region' and '#End Region' statements are not valid within method bodies/multiline lambdas</span></span>
<span data-ttu-id="537e3-103">`#Region`區塊必須宣告類別、 模組或命名空間層級。</span><span class="sxs-lookup"><span data-stu-id="537e3-103">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="537e3-104">可摺疊的區域可以包含一或多個程序，但不是能開始或結束程序內。</span><span class="sxs-lookup"><span data-stu-id="537e3-104">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>  
  
 <span data-ttu-id="537e3-105">**錯誤 ID:** BC32025</span><span class="sxs-lookup"><span data-stu-id="537e3-105">**Error ID:** BC32025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="537e3-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="537e3-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="537e3-107">確保與前述程序已正確地終止`End Function`或`End Sub`陳述式。</span><span class="sxs-lookup"><span data-stu-id="537e3-107">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="537e3-108">請確認`#Region`和`#End Region`指示詞是在相同的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="537e3-108">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="537e3-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="537e3-109">See also</span></span>

- [<span data-ttu-id="537e3-110">#Region 指示詞</span><span class="sxs-lookup"><span data-stu-id="537e3-110">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)

---
title: '&#39; #Region &#39;和 &#39; #End 區域 &#39;陳述式不是在方法主體多行 lambda 中無效'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 614d0c7324bfbf07bc5736c799e8b54937ead081
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="39region39-and-39end-region39-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="18506-102">&#39; #Region &#39;和 &#39; #End 區域 &#39;陳述式不是在方法主體/多行 lambda 中無效</span><span class="sxs-lookup"><span data-stu-id="18506-102">&#39;#Region&#39; and &#39;#End Region&#39; statements are not valid within method bodies/multiline lambdas</span></span>
<span data-ttu-id="18506-103">`#Region`區塊必須宣告類別、 模組或命名空間層級。</span><span class="sxs-lookup"><span data-stu-id="18506-103">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="18506-104">可摺疊的區域可以包含一或多個程序，但它無法開始或結束程序內。</span><span class="sxs-lookup"><span data-stu-id="18506-104">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>  
  
 <span data-ttu-id="18506-105">**錯誤 ID:** BC32025</span><span class="sxs-lookup"><span data-stu-id="18506-105">**Error ID:** BC32025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="18506-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="18506-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="18506-107">請確定前面的程序已正確地終止與`End Function`或`End Sub`陳述式。</span><span class="sxs-lookup"><span data-stu-id="18506-107">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="18506-108">請確認`#Region`和`#End Region`指示詞是在相同的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="18506-108">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18506-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18506-109">See Also</span></span>  
 [<span data-ttu-id="18506-110">#Region 指示詞</span><span class="sxs-lookup"><span data-stu-id="18506-110">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)

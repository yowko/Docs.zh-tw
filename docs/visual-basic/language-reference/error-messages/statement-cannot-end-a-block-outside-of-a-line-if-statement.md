---
title: "陳述式不能在之外結束區塊的列 &#39; 如果 &#39;陳述式"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords: BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 73fe3eb44e904366db7d505bbe8c5fef461eb78b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a><span data-ttu-id="183ca-102">陳述式不能在之外結束區塊的列 &#39; 如果 &#39;陳述式</span><span class="sxs-lookup"><span data-stu-id="183ca-102">Statement cannot end a block outside of a line &#39;If&#39; statement</span></span>
<span data-ttu-id="183ca-103">單行`If`陳述式包含以冒號 （:），其中一項分隔的數個陳述式`End`控制區塊之外單行陳述式`If`。</span><span class="sxs-lookup"><span data-stu-id="183ca-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="183ca-104">單行`If`陳述式就不會使用`End If`陳述式。</span><span class="sxs-lookup"><span data-stu-id="183ca-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="183ca-105">**錯誤 ID:** BC32005</span><span class="sxs-lookup"><span data-stu-id="183ca-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="183ca-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="183ca-106">To correct this error</span></span>  
  
-   <span data-ttu-id="183ca-107">移動的單一線條`If`陳述式區塊外部的控制項，其中包含`End If`陳述式。</span><span class="sxs-lookup"><span data-stu-id="183ca-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="183ca-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="183ca-108">See Also</span></span>  
 [<span data-ttu-id="183ca-109">If...Then...Else 陳述式</span><span class="sxs-lookup"><span data-stu-id="183ca-109">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)

---
title: "變數 &#39;&lt;variablename&gt;&#39; 隱藏了封閉區塊中的變數"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords: BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2af570cd002b4be4e15a7c03b0ffc2ff84ba3982
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="variable-39ltvariablenamegt39-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="66d84-102">變數 &#39;&lt;variablename&gt;&#39; 隱藏了封閉區塊中的變數</span><span class="sxs-lookup"><span data-stu-id="66d84-102">Variable &#39;&lt;variablename&gt;&#39; hides a variable in an enclosing block</span></span>
<span data-ttu-id="66d84-103">區塊中的變數具有相同名稱做為另一個本機變數。</span><span class="sxs-lookup"><span data-stu-id="66d84-103">A variable enclosed in a block has the same name as another local variable.</span></span>  
  
 <span data-ttu-id="66d84-104">**錯誤 ID:** BC30616</span><span class="sxs-lookup"><span data-stu-id="66d84-104">**Error ID:** BC30616</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="66d84-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="66d84-105">To correct this error</span></span>  
  
-   <span data-ttu-id="66d84-106">重新命名封閉區塊中的變數，使它不是其他任何區域變數一樣。</span><span class="sxs-lookup"><span data-stu-id="66d84-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="66d84-107">例如：</span><span class="sxs-lookup"><span data-stu-id="66d84-107">For example:</span></span>  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   <span data-ttu-id="66d84-108">這項錯誤的常見原因是使用`Catch e As Exception`內的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="66d84-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="66d84-109">如果這種情況，命名`Catch`區塊變數`ex`而不是`e`。</span><span class="sxs-lookup"><span data-stu-id="66d84-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>  
  
-   <span data-ttu-id="66d84-110">此錯誤的另一個常見來源是嘗試存取內宣告的區域變數`Try`中個別區塊`Catch`區塊。</span><span class="sxs-lookup"><span data-stu-id="66d84-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="66d84-111">若要修正此問題，外部變數宣告`Try...Catch...Finally`結構。</span><span class="sxs-lookup"><span data-stu-id="66d84-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66d84-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66d84-112">See Also</span></span>  
 [<span data-ttu-id="66d84-113">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="66d84-113">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="66d84-114">變數宣告</span><span class="sxs-lookup"><span data-stu-id="66d84-114">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)

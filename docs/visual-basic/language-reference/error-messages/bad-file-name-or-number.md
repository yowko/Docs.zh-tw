---
title: "不正確的檔名或數目"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3d7c8bae3df0e75a1c4f9afacdff681a553503d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="70467-102">不正確的檔名或數目</span><span class="sxs-lookup"><span data-stu-id="70467-102">Bad file name or number</span></span>
<span data-ttu-id="70467-103">嘗試存取指定的檔案時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="70467-103">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="70467-104">此錯誤的可能原因包括：</span><span class="sxs-lookup"><span data-stu-id="70467-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="70467-105">陳述式中未指定檔名或數目與檔案參考`FileOpen`或陳述式中指定`FileOpen`陳述式，但卻是之後關閉。</span><span class="sxs-lookup"><span data-stu-id="70467-105">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
-   <span data-ttu-id="70467-106">陳述式所參考的檔案與超出範圍的檔案數字的數字。</span><span class="sxs-lookup"><span data-stu-id="70467-106">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
-   <span data-ttu-id="70467-107">陳述式參考的檔案名稱或不是有效的數字。</span><span class="sxs-lookup"><span data-stu-id="70467-107">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="70467-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="70467-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="70467-109">請確認檔案名稱指定在`FileOpen`陳述式。</span><span class="sxs-lookup"><span data-stu-id="70467-109">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="70467-110">請注意，如果您叫用`FileClose`陳述式沒有引數，您可能會不小心關閉所有開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="70467-110">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2.  <span data-ttu-id="70467-111">如果您的程式碼會利用演算法產生檔案數目，請確定使用數字。</span><span class="sxs-lookup"><span data-stu-id="70467-111">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3.  <span data-ttu-id="70467-112">請檢查檔案名稱，以確保它們符合作業系統慣例。</span><span class="sxs-lookup"><span data-stu-id="70467-112">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70467-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70467-113">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>  
 [<span data-ttu-id="70467-114">Visual Basic 命名慣例</span><span class="sxs-lookup"><span data-stu-id="70467-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)

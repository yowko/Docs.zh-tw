---
title: 不正確的檔名或數目
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 2e5d4a3ddd66df85dc4758e22b36ac1ed495659a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935222"
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="67cf2-102">不正確的檔名或數目</span><span class="sxs-lookup"><span data-stu-id="67cf2-102">Bad file name or number</span></span>
<span data-ttu-id="67cf2-103">嘗試存取指定的檔案時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="67cf2-103">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="67cf2-104">此錯誤的可能原因包括：</span><span class="sxs-lookup"><span data-stu-id="67cf2-104">Among the possible causes for this error are:</span></span>  
  
- <span data-ttu-id="67cf2-105">陳述式所參考的檔案中未指定檔案名稱或數字`FileOpen`中指定陳述式或`FileOpen`陳述式，但卻是之後關閉。</span><span class="sxs-lookup"><span data-stu-id="67cf2-105">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
- <span data-ttu-id="67cf2-106">陳述式所參考的檔案，以超出範圍的檔案數字的數字。</span><span class="sxs-lookup"><span data-stu-id="67cf2-106">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
- <span data-ttu-id="67cf2-107">陳述式參考的檔案名稱或不是有效的數字。</span><span class="sxs-lookup"><span data-stu-id="67cf2-107">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="67cf2-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="67cf2-108">To correct this error</span></span>  
  
1. <span data-ttu-id="67cf2-109">請確定檔案名稱已在指定`FileOpen`陳述式。</span><span class="sxs-lookup"><span data-stu-id="67cf2-109">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="67cf2-110">請注意，如果您叫用`FileClose`陳述式不含引數，您可能不小心關閉所有開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="67cf2-110">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2. <span data-ttu-id="67cf2-111">如果您的程式碼以演算法產生的檔案數字，確定數字都有效。</span><span class="sxs-lookup"><span data-stu-id="67cf2-111">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3. <span data-ttu-id="67cf2-112">請檢查檔案名稱，以確保它們符合作業系統的慣例。</span><span class="sxs-lookup"><span data-stu-id="67cf2-112">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67cf2-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67cf2-113">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [<span data-ttu-id="67cf2-114">Visual Basic 命名慣例</span><span class="sxs-lookup"><span data-stu-id="67cf2-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)

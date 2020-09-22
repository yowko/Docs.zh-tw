---
title: 不正確的檔名或數目
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: d57a9e78e6ae179d3050e5a92399ca731fa16ba7
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874905"
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="1fab7-102">不正確的檔名或數目</span><span class="sxs-lookup"><span data-stu-id="1fab7-102">Bad file name or number</span></span>

<span data-ttu-id="1fab7-103">嘗試存取指定的檔案時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="1fab7-103">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="1fab7-104">此錯誤的可能原因包括：</span><span class="sxs-lookup"><span data-stu-id="1fab7-104">Among the possible causes for this error are:</span></span>  
  
- <span data-ttu-id="1fab7-105">語句參考的檔案中，沒有在語句中指定的檔案名或數位， `FileOpen` 或是在語句中指定 `FileOpen` 但之後關閉的檔案。</span><span class="sxs-lookup"><span data-stu-id="1fab7-105">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
- <span data-ttu-id="1fab7-106">語句所參考的檔案，其數位超出檔案數目範圍。</span><span class="sxs-lookup"><span data-stu-id="1fab7-106">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
- <span data-ttu-id="1fab7-107">語句參考的檔案名或號碼無效。</span><span class="sxs-lookup"><span data-stu-id="1fab7-107">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1fab7-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="1fab7-108">To correct this error</span></span>  
  
1. <span data-ttu-id="1fab7-109">請確定已在語句中指定檔案名 `FileOpen` 。</span><span class="sxs-lookup"><span data-stu-id="1fab7-109">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="1fab7-110">請注意，如果您叫 `FileClose` 用沒有引數的語句，您可能會不小心關閉所有開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="1fab7-110">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2. <span data-ttu-id="1fab7-111">如果您的程式碼會產生檔案號碼演算法，請確定數位有效。</span><span class="sxs-lookup"><span data-stu-id="1fab7-111">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3. <span data-ttu-id="1fab7-112">請檢查檔案名，以確定它們符合作業系統慣例。</span><span class="sxs-lookup"><span data-stu-id="1fab7-112">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fab7-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1fab7-113">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [<span data-ttu-id="1fab7-114">Visual Basic 命名慣例</span><span class="sxs-lookup"><span data-stu-id="1fab7-114">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)

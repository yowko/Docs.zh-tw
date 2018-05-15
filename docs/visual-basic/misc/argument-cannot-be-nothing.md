---
title: 引數不能為 Nothing
ms.date: 07/20/2015
f1_keywords:
- vbrGeneral_ArgumentNullException
ms.assetid: 2abd995b-36a5-45f0-b3c1-6e0c3b31a875
ms.openlocfilehash: 7b08dd41f638138df4c2f92fbe9f05f1312c2d03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="argument-cannot-be-nothing"></a><span data-ttu-id="27242-102">引數不能為 Nothing</span><span class="sxs-lookup"><span data-stu-id="27242-102">Argument cannot be Nothing</span></span>
<span data-ttu-id="27242-103">Null 值已提供給必須有值的引數。</span><span class="sxs-lookup"><span data-stu-id="27242-103">A null value has been supplied for an argument that must have a value.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="27242-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="27242-104">To correct this error</span></span>  
  
-   <span data-ttu-id="27242-105">您可能嘗試使用物件，卻未提供該物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="27242-105">You might have tried to use an object without providing an instance of the object.</span></span> <span data-ttu-id="27242-106">這種情況請使用 `New` 關鍵字建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="27242-106">In such a case, use the `New` keyword to create the instance.</span></span>  
  
-   <span data-ttu-id="27242-107">檢查值是否計算正確。</span><span class="sxs-lookup"><span data-stu-id="27242-107">Check that the value is calculated correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27242-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27242-108">See Also</span></span>  
 <xref:System.NullReferenceException>

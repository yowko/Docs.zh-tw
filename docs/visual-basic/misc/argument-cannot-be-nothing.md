---
title: 引數不能為 Nothing
ms.date: 07/20/2015
f1_keywords:
- vbrGeneral_ArgumentNullException
ms.assetid: 2abd995b-36a5-45f0-b3c1-6e0c3b31a875
ms.openlocfilehash: 157329c74e9c300f8d4d60d96980f9cb77d0e550
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656124"
---
# <a name="argument-cannot-be-nothing"></a><span data-ttu-id="546ef-102">引數不能為 Nothing</span><span class="sxs-lookup"><span data-stu-id="546ef-102">Argument cannot be Nothing</span></span>
<span data-ttu-id="546ef-103">Null 值已提供給必須有值的引數。</span><span class="sxs-lookup"><span data-stu-id="546ef-103">A null value has been supplied for an argument that must have a value.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="546ef-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="546ef-104">To correct this error</span></span>  
  
-   <span data-ttu-id="546ef-105">您可能嘗試使用物件，卻未提供該物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="546ef-105">You might have tried to use an object without providing an instance of the object.</span></span> <span data-ttu-id="546ef-106">這種情況請使用 `New` 關鍵字建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="546ef-106">In such a case, use the `New` keyword to create the instance.</span></span>  
  
-   <span data-ttu-id="546ef-107">檢查值是否計算正確。</span><span class="sxs-lookup"><span data-stu-id="546ef-107">Check that the value is calculated correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="546ef-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="546ef-108">See also</span></span>
- <xref:System.NullReferenceException>

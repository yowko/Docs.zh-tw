---
title: PreCloseAssembly 方法
ms.date: 03/30/2017
api_name:
- IALink.PreCloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- PreCloseAssembly
helpviewer_keywords:
- PreCloseAssembly method
ms.assetid: 6d23ac54-15ea-4027-a172-9ebef43e8f56
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d4cf862ae3676b85a7fc3f09a4f5794e01284737
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787230"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="9f749-102">PreCloseAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="9f749-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="9f749-103">關閉元件檔。</span><span class="sxs-lookup"><span data-stu-id="9f749-103">Closes the assembly file.</span></span> <span data-ttu-id="9f749-104">請在關閉所有其他檔案之後，但在關閉元件檔之前，呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="9f749-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="9f749-105">請勿針對未系結的模組呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="9f749-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f749-106">語法</span><span class="sxs-lookup"><span data-stu-id="9f749-106">Syntax</span></span>  
  
```cpp  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f749-107">參數</span><span class="sxs-lookup"><span data-stu-id="9f749-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="9f749-108">元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="9f749-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9f749-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="9f749-109">Return Value</span></span>  
 <span data-ttu-id="9f749-110">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="9f749-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f749-111">需求</span><span class="sxs-lookup"><span data-stu-id="9f749-111">Requirements</span></span>  
 <span data-ttu-id="9f749-112">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="9f749-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f749-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f749-113">See also</span></span>

- [<span data-ttu-id="9f749-114">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="9f749-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="9f749-115">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="9f749-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="9f749-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="9f749-116">ALink API</span></span>](index.md)

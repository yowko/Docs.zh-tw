---
title: StrongNameHashSize 函式
ms.date: 03/30/2017
api_name:
- StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameHashSize
helpviewer_keywords:
- StrongNameHashSize function [.NET Framework strong naming]
ms.assetid: 738c98d7-a60c-45fe-a296-220af05e6991
topic_type:
- apiref
ms.openlocfilehash: c656f73748faf8be7124be65f3ed455f2d5fd07a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73105183"
---
# <a name="strongnamehashsize-function"></a><span data-ttu-id="e9315-102">StrongNameHashSize 函式</span><span class="sxs-lookup"><span data-stu-id="e9315-102">StrongNameHashSize Function</span></span>
<span data-ttu-id="e9315-103">使用指定的雜湊演算法取得雜湊所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="e9315-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="e9315-104">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="e9315-104">This function has been deprecated.</span></span> <span data-ttu-id="e9315-105">請改用[ICLRStrongName：： StrongNameHashSize](../hosting/iclrstrongname-strongnamehashsize-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="e9315-105">Use the [ICLRStrongName::StrongNameHashSize](../hosting/iclrstrongname-strongnamehashsize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9315-106">語法</span><span class="sxs-lookup"><span data-stu-id="e9315-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9315-107">參數</span><span class="sxs-lookup"><span data-stu-id="e9315-107">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="e9315-108">在用來計算緩衝區大小的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="e9315-108">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="e9315-109">脫銷傳回的緩衝區大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="e9315-109">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9315-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="e9315-110">Return Value</span></span>  
 <span data-ttu-id="e9315-111">成功完成時 `true`;否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="e9315-111">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9315-112">備註</span><span class="sxs-lookup"><span data-stu-id="e9315-112">Remarks</span></span>  
 <span data-ttu-id="e9315-113">如果 `StrongNameHashSize` 函式未順利完成，請呼叫[StrongNameErrorInfo](strongnameerrorinfo-function.md)函式，以取出最後產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="e9315-113">If the `StrongNameHashSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9315-114">需求</span><span class="sxs-lookup"><span data-stu-id="e9315-114">Requirements</span></span>  
 <span data-ttu-id="e9315-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e9315-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9315-116">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="e9315-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="e9315-117">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e9315-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e9315-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9315-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9315-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="e9315-119">See also</span></span>

- [<span data-ttu-id="e9315-120">StrongNameHashSize 方法</span><span class="sxs-lookup"><span data-stu-id="e9315-120">StrongNameHashSize Method</span></span>](../hosting/iclrstrongname-strongnamehashsize-method.md)
- [<span data-ttu-id="e9315-121">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="e9315-121">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)

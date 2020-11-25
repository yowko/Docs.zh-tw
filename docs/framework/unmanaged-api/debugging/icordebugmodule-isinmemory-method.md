---
title: ICorDebugModule::IsInMemory 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsInMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsInMemory
helpviewer_keywords:
- IsInMemory method [.NET Framework debugging]
- ICorDebugModule::IsInMemory method [.NET Framework debugging]
ms.assetid: 89940711-98e7-4aa6-bffc-5e39e91e1b7d
topic_type:
- apiref
ms.openlocfilehash: 637cac67e73d38aca0fdc5eaeae5405c4a859aa3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709813"
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="ca8d3-102">ICorDebugModule::IsInMemory 方法</span><span class="sxs-lookup"><span data-stu-id="ca8d3-102">ICorDebugModule::IsInMemory Method</span></span>

<span data-ttu-id="ca8d3-103">取得值，這個值會指出此模組是否只存在於記憶體中。</span><span class="sxs-lookup"><span data-stu-id="ca8d3-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca8d3-104">語法</span><span class="sxs-lookup"><span data-stu-id="ca8d3-104">Syntax</span></span>  
  
```cpp  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca8d3-105">參數</span><span class="sxs-lookup"><span data-stu-id="ca8d3-105">Parameters</span></span>  

 `pInMemory`  
 <span data-ttu-id="ca8d3-106">[out] `true` 如果此模組只存在於記憶體中，則為。否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="ca8d3-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca8d3-107">備註</span><span class="sxs-lookup"><span data-stu-id="ca8d3-107">Remarks</span></span>  

 <span data-ttu-id="ca8d3-108">Common language runtime (CLR) 支援從原始位元組串流載入模組。</span><span class="sxs-lookup"><span data-stu-id="ca8d3-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="ca8d3-109">這類別模組稱為 *記憶體內部模組* ，而且不存在於磁片上。</span><span class="sxs-lookup"><span data-stu-id="ca8d3-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca8d3-110">需求</span><span class="sxs-lookup"><span data-stu-id="ca8d3-110">Requirements</span></span>  

 <span data-ttu-id="ca8d3-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ca8d3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca8d3-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca8d3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca8d3-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca8d3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca8d3-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca8d3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca8d3-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca8d3-115">See also</span></span>

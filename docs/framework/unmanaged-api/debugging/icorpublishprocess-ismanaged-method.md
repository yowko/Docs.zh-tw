---
title: ICorPublishProcess::IsManaged 方法
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type:
- apiref
ms.openlocfilehash: ad3a357a98cb5ed28a34e4076b5e145903ceaf91
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103491"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="52aa8-102">ICorPublishProcess::IsManaged 方法</span><span class="sxs-lookup"><span data-stu-id="52aa8-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="52aa8-103">取得值，指出此[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)所參考的進程是否已知具有 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="52aa8-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52aa8-104">語法</span><span class="sxs-lookup"><span data-stu-id="52aa8-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52aa8-105">參數</span><span class="sxs-lookup"><span data-stu-id="52aa8-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="52aa8-106">脫銷布林值的指標，指出進程是否有 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="52aa8-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="52aa8-107">如果進程具有 managed 程式碼，則此值為 `true`;否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="52aa8-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52aa8-108">備註</span><span class="sxs-lookup"><span data-stu-id="52aa8-108">Remarks</span></span>  
 <span data-ttu-id="52aa8-109">由於目前的 `ICorPublishProcess` 版本只允許存取具有 managed 程式碼的進程，`IsManaged` 一律會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="52aa8-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52aa8-110">需求</span><span class="sxs-lookup"><span data-stu-id="52aa8-110">Requirements</span></span>  
 <span data-ttu-id="52aa8-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="52aa8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52aa8-112">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="52aa8-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="52aa8-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52aa8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52aa8-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52aa8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52aa8-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="52aa8-115">See also</span></span>

- [<span data-ttu-id="52aa8-116">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="52aa8-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)

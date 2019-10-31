---
title: ICorPublishAppDomain::GetID 方法
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetID
helpviewer_keywords:
- GetID method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetID method [.NET Framework debugging]
ms.assetid: 229437e3-1465-4bd8-8846-9804b2488133
topic_type:
- apiref
ms.openlocfilehash: 33a72d9aea09f808d42d1a17a7ec5640d20d7c79
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140382"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="e6ed0-102">ICorPublishAppDomain::GetID 方法</span><span class="sxs-lookup"><span data-stu-id="e6ed0-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="e6ed0-103">取得此[ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="e6ed0-103">Gets the unique identifier for this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6ed0-104">語法</span><span class="sxs-lookup"><span data-stu-id="e6ed0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6ed0-105">參數</span><span class="sxs-lookup"><span data-stu-id="e6ed0-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="e6ed0-106">脫銷應用程式域的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="e6ed0-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6ed0-107">備註</span><span class="sxs-lookup"><span data-stu-id="e6ed0-107">Remarks</span></span>  
 <span data-ttu-id="e6ed0-108">只有在包含進程的範圍內，識別碼是唯一的。</span><span class="sxs-lookup"><span data-stu-id="e6ed0-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6ed0-109">需求</span><span class="sxs-lookup"><span data-stu-id="e6ed0-109">Requirements</span></span>  
 <span data-ttu-id="e6ed0-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e6ed0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6ed0-111">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="e6ed0-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="e6ed0-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6ed0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6ed0-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6ed0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6ed0-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="e6ed0-114">See also</span></span>

- [<span data-ttu-id="e6ed0-115">ICorPublishAppDomain 介面</span><span class="sxs-lookup"><span data-stu-id="e6ed0-115">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)

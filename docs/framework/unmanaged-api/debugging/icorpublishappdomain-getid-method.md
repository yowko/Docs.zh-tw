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
ms.openlocfilehash: 8d6e130981693268ae5c2cd615036b84ca8ed2d8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790704"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="8df6a-102">ICorPublishAppDomain::GetID 方法</span><span class="sxs-lookup"><span data-stu-id="8df6a-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="8df6a-103">取得此[ICorPublishAppDomain](icorpublishappdomain-interface.md)的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="8df6a-103">Gets the unique identifier for this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8df6a-104">語法</span><span class="sxs-lookup"><span data-stu-id="8df6a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8df6a-105">參數</span><span class="sxs-lookup"><span data-stu-id="8df6a-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="8df6a-106">脫銷應用程式域的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="8df6a-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8df6a-107">備註</span><span class="sxs-lookup"><span data-stu-id="8df6a-107">Remarks</span></span>  
 <span data-ttu-id="8df6a-108">只有在包含進程的範圍內，識別碼是唯一的。</span><span class="sxs-lookup"><span data-stu-id="8df6a-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8df6a-109">需求</span><span class="sxs-lookup"><span data-stu-id="8df6a-109">Requirements</span></span>  
 <span data-ttu-id="8df6a-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8df6a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8df6a-111">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="8df6a-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="8df6a-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8df6a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8df6a-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8df6a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8df6a-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="8df6a-114">See also</span></span>

- [<span data-ttu-id="8df6a-115">ICorPublishAppDomain 介面</span><span class="sxs-lookup"><span data-stu-id="8df6a-115">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)

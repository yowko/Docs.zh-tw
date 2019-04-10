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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44a2038af5d6ef46ad7cc661603e99b2f3dd67a9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215920"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="ab5a2-102">ICorPublishAppDomain::GetID 方法</span><span class="sxs-lookup"><span data-stu-id="ab5a2-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="ab5a2-103">取得這個唯一識別碼[ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="ab5a2-103">Gets the unique identifier for this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab5a2-104">語法</span><span class="sxs-lookup"><span data-stu-id="ab5a2-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab5a2-105">參數</span><span class="sxs-lookup"><span data-stu-id="ab5a2-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="ab5a2-106">[out]為應用程式定義域的識別項的指標。</span><span class="sxs-lookup"><span data-stu-id="ab5a2-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab5a2-107">備註</span><span class="sxs-lookup"><span data-stu-id="ab5a2-107">Remarks</span></span>  
 <span data-ttu-id="ab5a2-108">此識別碼只能在包含的程序的範圍內是唯一的。</span><span class="sxs-lookup"><span data-stu-id="ab5a2-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab5a2-109">需求</span><span class="sxs-lookup"><span data-stu-id="ab5a2-109">Requirements</span></span>  
 <span data-ttu-id="ab5a2-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ab5a2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab5a2-111">**標頭：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="ab5a2-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ab5a2-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab5a2-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ab5a2-113">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="ab5a2-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ab5a2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab5a2-114">See also</span></span>

- [<span data-ttu-id="ab5a2-115">ICorPublishAppDomain 介面</span><span class="sxs-lookup"><span data-stu-id="ab5a2-115">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)

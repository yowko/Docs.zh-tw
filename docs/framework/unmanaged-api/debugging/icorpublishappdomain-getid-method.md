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
ms.openlocfilehash: 36c5c674f3cdf867107b9ee85a5befadc9246d78
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396310"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="d7b2d-102">ICorPublishAppDomain::GetID 方法</span><span class="sxs-lookup"><span data-stu-id="d7b2d-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="d7b2d-103">取得此[ICorPublishAppDomain](icorpublishappdomain-interface.md)的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="d7b2d-103">Gets the unique identifier for this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7b2d-104">語法</span><span class="sxs-lookup"><span data-stu-id="d7b2d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7b2d-105">參數</span><span class="sxs-lookup"><span data-stu-id="d7b2d-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="d7b2d-106">脫銷應用程式域的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="d7b2d-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7b2d-107">備註</span><span class="sxs-lookup"><span data-stu-id="d7b2d-107">Remarks</span></span>  
 <span data-ttu-id="d7b2d-108">只有在包含進程的範圍內，識別碼是唯一的。</span><span class="sxs-lookup"><span data-stu-id="d7b2d-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7b2d-109">需求</span><span class="sxs-lookup"><span data-stu-id="d7b2d-109">Requirements</span></span>  
 <span data-ttu-id="d7b2d-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d7b2d-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7b2d-111">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="d7b2d-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="d7b2d-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7b2d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7b2d-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7b2d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7b2d-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="d7b2d-114">See also</span></span>

- [<span data-ttu-id="d7b2d-115">ICorPublishAppDomain 介面</span><span class="sxs-lookup"><span data-stu-id="d7b2d-115">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)

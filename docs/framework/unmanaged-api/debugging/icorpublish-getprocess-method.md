---
title: ICorPublish::GetProcess 方法
ms.date: 03/30/2017
api_name:
- ICorPublish.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::GetProcess
helpviewer_keywords:
- ICorPublish::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorPublish interface [.NET Framework debugging]
ms.assetid: c5143805-2eb7-45b8-85ed-c8fb34df1084
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b2dcdaed34044122dd2a61c9e0b5bb02f8cc0d9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774267"
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="ab094-102">ICorPublish::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="ab094-102">ICorPublish::GetProcess Method</span></span>
<span data-ttu-id="ab094-103">取得[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)執行個體，表示具有指定識別碼的程序。</span><span class="sxs-lookup"><span data-stu-id="ab094-103">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab094-104">語法</span><span class="sxs-lookup"><span data-stu-id="ab094-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess(  
    [in] unsigned              pid,   
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab094-105">參數</span><span class="sxs-lookup"><span data-stu-id="ab094-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="ab094-106">[in]處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="ab094-106">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="ab094-107">[out]位址指標`ICorPublishProcess`代表程序的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ab094-107">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab094-108">備註</span><span class="sxs-lookup"><span data-stu-id="ab094-108">Remarks</span></span>  
 <span data-ttu-id="ab094-109">`GetProcess` 如果處理程序不存在，或未受管理的程序可由目前的使用者進行偵錯，就會失敗。</span><span class="sxs-lookup"><span data-stu-id="ab094-109">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab094-110">需求</span><span class="sxs-lookup"><span data-stu-id="ab094-110">Requirements</span></span>  
 <span data-ttu-id="ab094-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ab094-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab094-112">**標頭：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="ab094-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ab094-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab094-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab094-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab094-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab094-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab094-115">See also</span></span>

- [<span data-ttu-id="ab094-116">ICorPublish 介面</span><span class="sxs-lookup"><span data-stu-id="ab094-116">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)

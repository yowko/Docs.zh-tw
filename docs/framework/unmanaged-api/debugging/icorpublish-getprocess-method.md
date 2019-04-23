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
ms.openlocfilehash: 021068caa8f1ad2c64e5ca3d18ea25dc827563a4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59084996"
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="11fbe-102">ICorPublish::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="11fbe-102">ICorPublish::GetProcess Method</span></span>
<span data-ttu-id="11fbe-103">取得[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)執行個體，表示具有指定識別碼的程序。</span><span class="sxs-lookup"><span data-stu-id="11fbe-103">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11fbe-104">語法</span><span class="sxs-lookup"><span data-stu-id="11fbe-104">Syntax</span></span>  
  
```  
HRESULT GetProcess(  
    [in] unsigned              pid,   
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11fbe-105">參數</span><span class="sxs-lookup"><span data-stu-id="11fbe-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="11fbe-106">[in]處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="11fbe-106">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="11fbe-107">[out]位址指標`ICorPublishProcess`代表程序的執行個體。</span><span class="sxs-lookup"><span data-stu-id="11fbe-107">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11fbe-108">備註</span><span class="sxs-lookup"><span data-stu-id="11fbe-108">Remarks</span></span>  
 <span data-ttu-id="11fbe-109">`GetProcess` 如果處理程序不存在，或未受管理的程序可由目前的使用者進行偵錯，就會失敗。</span><span class="sxs-lookup"><span data-stu-id="11fbe-109">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11fbe-110">需求</span><span class="sxs-lookup"><span data-stu-id="11fbe-110">Requirements</span></span>  
 <span data-ttu-id="11fbe-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="11fbe-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11fbe-112">**標頭：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="11fbe-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="11fbe-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11fbe-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11fbe-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11fbe-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11fbe-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11fbe-115">See also</span></span>

- [<span data-ttu-id="11fbe-116">ICorPublish 介面</span><span class="sxs-lookup"><span data-stu-id="11fbe-116">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)

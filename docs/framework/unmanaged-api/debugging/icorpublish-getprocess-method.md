---
title: "ICorPublish::GetProcess 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e613b9101e842a584eef4bcbac1bf3de1dba5cd3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="68300-102">ICorPublish::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="68300-102">ICorPublish::GetProcess Method</span></span>
<span data-ttu-id="68300-103">取得[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)代表具有指定識別碼的程序的執行個體。</span><span class="sxs-lookup"><span data-stu-id="68300-103">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68300-104">語法</span><span class="sxs-lookup"><span data-stu-id="68300-104">Syntax</span></span>  
  
```  
HRESULT GetProcess(  
    [in] unsigned              pid,   
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68300-105">參數</span><span class="sxs-lookup"><span data-stu-id="68300-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="68300-106">[in]程序的識別項。</span><span class="sxs-lookup"><span data-stu-id="68300-106">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="68300-107">[out]位址指標`ICorPublishProcess`代表程序的執行個體。</span><span class="sxs-lookup"><span data-stu-id="68300-107">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68300-108">備註</span><span class="sxs-lookup"><span data-stu-id="68300-108">Remarks</span></span>  
 <span data-ttu-id="68300-109">`GetProcess`如果處理程序不存在，或不是由目前的使用者才能進行偵錯 managed 處理序會失敗。</span><span class="sxs-lookup"><span data-stu-id="68300-109">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68300-110">需求</span><span class="sxs-lookup"><span data-stu-id="68300-110">Requirements</span></span>  
 <span data-ttu-id="68300-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="68300-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68300-112">**標頭：** CorPub.idl、 CorPub.h</span><span class="sxs-lookup"><span data-stu-id="68300-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="68300-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68300-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68300-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68300-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68300-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="68300-115">See Also</span></span>  
 [<span data-ttu-id="68300-116">ICorPublish 介面</span><span class="sxs-lookup"><span data-stu-id="68300-116">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)

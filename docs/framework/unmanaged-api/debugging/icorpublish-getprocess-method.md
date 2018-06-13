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
ms.openlocfilehash: 414bc1bbd3578d0707e35fa70fe196b504af9942
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418492"
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="29e3a-102">ICorPublish::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="29e3a-102">ICorPublish::GetProcess Method</span></span>
<span data-ttu-id="29e3a-103">取得[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)代表具有指定識別碼的程序的執行個體。</span><span class="sxs-lookup"><span data-stu-id="29e3a-103">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29e3a-104">語法</span><span class="sxs-lookup"><span data-stu-id="29e3a-104">Syntax</span></span>  
  
```  
HRESULT GetProcess(  
    [in] unsigned              pid,   
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29e3a-105">參數</span><span class="sxs-lookup"><span data-stu-id="29e3a-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="29e3a-106">[in]程序的識別項。</span><span class="sxs-lookup"><span data-stu-id="29e3a-106">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="29e3a-107">[out]位址指標`ICorPublishProcess`代表程序的執行個體。</span><span class="sxs-lookup"><span data-stu-id="29e3a-107">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29e3a-108">備註</span><span class="sxs-lookup"><span data-stu-id="29e3a-108">Remarks</span></span>  
 <span data-ttu-id="29e3a-109">`GetProcess` 如果處理程序不存在，或不是由目前的使用者才能進行偵錯 managed 處理序會失敗。</span><span class="sxs-lookup"><span data-stu-id="29e3a-109">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29e3a-110">需求</span><span class="sxs-lookup"><span data-stu-id="29e3a-110">Requirements</span></span>  
 <span data-ttu-id="29e3a-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="29e3a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29e3a-112">**標頭：** CorPub.idl、 CorPub.h</span><span class="sxs-lookup"><span data-stu-id="29e3a-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="29e3a-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29e3a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29e3a-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29e3a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29e3a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29e3a-115">See Also</span></span>  
 [<span data-ttu-id="29e3a-116">ICorPublish 介面</span><span class="sxs-lookup"><span data-stu-id="29e3a-116">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)

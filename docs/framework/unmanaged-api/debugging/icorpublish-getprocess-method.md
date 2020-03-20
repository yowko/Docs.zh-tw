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
ms.openlocfilehash: 46f047dbec7ff008873540806b76ffe7085086b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178427"
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="2a123-102">ICorPublish::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="2a123-102">ICorPublish::GetProcess Method</span></span>
<span data-ttu-id="2a123-103">獲取使用指定識別碼表示進程的[ICorPublishProcess](icorpublishprocess-interface.md)實例。</span><span class="sxs-lookup"><span data-stu-id="2a123-103">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a123-104">語法</span><span class="sxs-lookup"><span data-stu-id="2a123-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess(  
    [in] unsigned              pid,
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a123-105">參數</span><span class="sxs-lookup"><span data-stu-id="2a123-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="2a123-106">[在]進程的識別碼。</span><span class="sxs-lookup"><span data-stu-id="2a123-106">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="2a123-107">[出]指向表示進程的`ICorPublishProcess`實例位址的指標。</span><span class="sxs-lookup"><span data-stu-id="2a123-107">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a123-108">備註</span><span class="sxs-lookup"><span data-stu-id="2a123-108">Remarks</span></span>  
 <span data-ttu-id="2a123-109">`GetProcess`如果進程不存在，或者不是當前使用者可以調試的託管進程，則失敗。</span><span class="sxs-lookup"><span data-stu-id="2a123-109">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a123-110">需求</span><span class="sxs-lookup"><span data-stu-id="2a123-110">Requirements</span></span>  
 <span data-ttu-id="2a123-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2a123-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a123-112">**標題：** 科爾普布.idl， 科爾普布.h</span><span class="sxs-lookup"><span data-stu-id="2a123-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="2a123-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a123-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a123-114">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a123-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a123-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a123-115">See also</span></span>

- [<span data-ttu-id="2a123-116">ICorPublish 介面</span><span class="sxs-lookup"><span data-stu-id="2a123-116">ICorPublish Interface</span></span>](icorpublish-interface.md)

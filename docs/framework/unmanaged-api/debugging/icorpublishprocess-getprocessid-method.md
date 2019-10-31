---
title: ICorPublishProcess::GetProcessID 方法
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.GetProcessID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::GetProcessID
helpviewer_keywords:
- ICorPublishProcess::GetProcessID method [.NET Framework debugging]
- GetProcessID method [.NET Framework debugging]
ms.assetid: f31185e0-f01d-463a-b392-42163e39bfe9
topic_type:
- apiref
ms.openlocfilehash: 728e8bdbce7f93176324d8f80261030f8cbae283
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140415"
---
# <a name="icorpublishprocessgetprocessid-method"></a><span data-ttu-id="6301d-102">ICorPublishProcess::GetProcessID 方法</span><span class="sxs-lookup"><span data-stu-id="6301d-102">ICorPublishProcess::GetProcessID Method</span></span>
<span data-ttu-id="6301d-103">取得此進程的作業系統識別碼。</span><span class="sxs-lookup"><span data-stu-id="6301d-103">Gets the operating system identifier for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6301d-104">語法</span><span class="sxs-lookup"><span data-stu-id="6301d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcessID (  
    [out] unsigned   *pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6301d-105">參數</span><span class="sxs-lookup"><span data-stu-id="6301d-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="6301d-106">脫銷這個[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)物件所表示之進程的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="6301d-106">[out] A pointer to the identifier of the process represented by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6301d-107">需求</span><span class="sxs-lookup"><span data-stu-id="6301d-107">Requirements</span></span>  
 <span data-ttu-id="6301d-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6301d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6301d-109">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="6301d-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="6301d-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6301d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6301d-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6301d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6301d-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="6301d-112">See also</span></span>

- [<span data-ttu-id="6301d-113">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="6301d-113">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)

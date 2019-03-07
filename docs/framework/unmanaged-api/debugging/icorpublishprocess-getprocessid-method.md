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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61c67e074fc32098fa0d8326ea2f0ecfb1efa952
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471763"
---
# <a name="icorpublishprocessgetprocessid-method"></a><span data-ttu-id="f3fcf-102">ICorPublishProcess::GetProcessID 方法</span><span class="sxs-lookup"><span data-stu-id="f3fcf-102">ICorPublishProcess::GetProcessID Method</span></span>
<span data-ttu-id="f3fcf-103">取得這個處理序作業系統識別項。</span><span class="sxs-lookup"><span data-stu-id="f3fcf-103">Gets the operating system identifier for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3fcf-104">語法</span><span class="sxs-lookup"><span data-stu-id="f3fcf-104">Syntax</span></span>  
  
```  
HRESULT GetProcessID (  
    [out] unsigned   *pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3fcf-105">參數</span><span class="sxs-lookup"><span data-stu-id="f3fcf-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="f3fcf-106">[out]所表示的程序的識別項的指標[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="f3fcf-106">[out] A pointer to the identifier of the process represented by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3fcf-107">需求</span><span class="sxs-lookup"><span data-stu-id="f3fcf-107">Requirements</span></span>  
 <span data-ttu-id="f3fcf-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f3fcf-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3fcf-109">**標頭：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="f3fcf-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="f3fcf-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3fcf-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3fcf-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3fcf-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3fcf-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3fcf-112">See also</span></span>
- [<span data-ttu-id="f3fcf-113">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="f3fcf-113">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)

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
ms.openlocfilehash: 91e1697366bd3ee95fd040ee261d68417a8125e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423604"
---
# <a name="icorpublishprocessgetprocessid-method"></a><span data-ttu-id="c2850-102">ICorPublishProcess::GetProcessID 方法</span><span class="sxs-lookup"><span data-stu-id="c2850-102">ICorPublishProcess::GetProcessID Method</span></span>
<span data-ttu-id="c2850-103">取得這個處理序作業系統識別項。</span><span class="sxs-lookup"><span data-stu-id="c2850-103">Gets the operating system identifier for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2850-104">語法</span><span class="sxs-lookup"><span data-stu-id="c2850-104">Syntax</span></span>  
  
```  
HRESULT GetProcessID (  
    [out] unsigned   *pid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c2850-105">參數</span><span class="sxs-lookup"><span data-stu-id="c2850-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="c2850-106">[out]程序所代表的識別項的指標[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="c2850-106">[out] A pointer to the identifier of the process represented by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2850-107">需求</span><span class="sxs-lookup"><span data-stu-id="c2850-107">Requirements</span></span>  
 <span data-ttu-id="c2850-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c2850-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2850-109">**標頭：** CorPub.idl、 CorPub.h</span><span class="sxs-lookup"><span data-stu-id="c2850-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="c2850-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2850-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2850-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2850-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2850-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2850-112">See Also</span></span>  
 [<span data-ttu-id="c2850-113">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="c2850-113">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)

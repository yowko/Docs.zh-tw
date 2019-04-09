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
ms.openlocfilehash: 6f3948e45b991e667ea90c7846ee0d6fd630c0db
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165798"
---
# <a name="icorpublishprocessgetprocessid-method"></a><span data-ttu-id="a54fe-102">ICorPublishProcess::GetProcessID 方法</span><span class="sxs-lookup"><span data-stu-id="a54fe-102">ICorPublishProcess::GetProcessID Method</span></span>
<span data-ttu-id="a54fe-103">取得這個處理序作業系統識別項。</span><span class="sxs-lookup"><span data-stu-id="a54fe-103">Gets the operating system identifier for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a54fe-104">語法</span><span class="sxs-lookup"><span data-stu-id="a54fe-104">Syntax</span></span>  
  
```  
HRESULT GetProcessID (  
    [out] unsigned   *pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a54fe-105">參數</span><span class="sxs-lookup"><span data-stu-id="a54fe-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="a54fe-106">[out]所表示的程序的識別項的指標[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="a54fe-106">[out] A pointer to the identifier of the process represented by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a54fe-107">需求</span><span class="sxs-lookup"><span data-stu-id="a54fe-107">Requirements</span></span>  
 <span data-ttu-id="a54fe-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a54fe-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a54fe-109">**標頭：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="a54fe-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a54fe-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a54fe-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="a54fe-111">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="a54fe-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a54fe-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a54fe-112">See also</span></span>

- [<span data-ttu-id="a54fe-113">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="a54fe-113">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)

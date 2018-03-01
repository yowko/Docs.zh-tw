---
title: "ICorPublishProcess::GetDisplayName 方法"
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
- ICorPublishProcess.GetDisplayName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::GetDisplayName
helpviewer_keywords:
- ICorPublishProcess::GetDisplayName method [.NET Framework debugging]
- GetDisplayName method, ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 7c0af9e9-a73f-41aa-a685-b21c439e059d
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 98c751b29f1bffd8baa8b87548d588c6db98eed2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="edef0-102">ICorPublishProcess::GetDisplayName 方法</span><span class="sxs-lookup"><span data-stu-id="edef0-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="edef0-103">取得處理序所參考的可執行檔的完整路徑[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="edef0-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edef0-104">語法</span><span class="sxs-lookup"><span data-stu-id="edef0-104">Syntax</span></span>  
  
```  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,   
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR                        *szName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="edef0-105">參數</span><span class="sxs-lookup"><span data-stu-id="edef0-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="edef0-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="edef0-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="edef0-107">[out]傳回的寬字元數目`szName`陣列。</span><span class="sxs-lookup"><span data-stu-id="edef0-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="edef0-108">[out]陣列來儲存名稱，包括可執行檔的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="edef0-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="edef0-109">名稱是以 null 結束。</span><span class="sxs-lookup"><span data-stu-id="edef0-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edef0-110">需求</span><span class="sxs-lookup"><span data-stu-id="edef0-110">Requirements</span></span>  
 <span data-ttu-id="edef0-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="edef0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edef0-112">**標頭：** CorPub.idl、 CorPub.h</span><span class="sxs-lookup"><span data-stu-id="edef0-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="edef0-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="edef0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="edef0-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edef0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edef0-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="edef0-115">See Also</span></span>  
 [<span data-ttu-id="edef0-116">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="edef0-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)

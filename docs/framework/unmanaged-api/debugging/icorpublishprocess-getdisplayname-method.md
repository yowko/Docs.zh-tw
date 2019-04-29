---
title: ICorPublishProcess::GetDisplayName 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6e7aa845f104ef734f039d46e1eeaba5fd01c73
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704085"
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="a435d-102">ICorPublishProcess::GetDisplayName 方法</span><span class="sxs-lookup"><span data-stu-id="a435d-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="a435d-103">取得處理序所參考的可執行檔的完整路徑[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="a435d-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a435d-104">語法</span><span class="sxs-lookup"><span data-stu-id="a435d-104">Syntax</span></span>  
  
```  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,   
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR                        *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a435d-105">參數</span><span class="sxs-lookup"><span data-stu-id="a435d-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="a435d-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="a435d-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="a435d-107">[out]中傳回的寬字元數目`szName`陣列。</span><span class="sxs-lookup"><span data-stu-id="a435d-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="a435d-108">[out]要儲存的名稱，包括可執行檔的完整路徑的陣列。</span><span class="sxs-lookup"><span data-stu-id="a435d-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="a435d-109">名稱是以 null 結束。</span><span class="sxs-lookup"><span data-stu-id="a435d-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a435d-110">需求</span><span class="sxs-lookup"><span data-stu-id="a435d-110">Requirements</span></span>  
 <span data-ttu-id="a435d-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a435d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a435d-112">**標頭：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="a435d-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a435d-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a435d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a435d-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a435d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a435d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a435d-115">See also</span></span>

- [<span data-ttu-id="a435d-116">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="a435d-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)

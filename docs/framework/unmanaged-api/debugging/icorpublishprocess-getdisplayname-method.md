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
ms.openlocfilehash: df2750f082ddc40bbeee121116c3e877d037da84
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140426"
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="ceb8e-102">ICorPublishProcess::GetDisplayName 方法</span><span class="sxs-lookup"><span data-stu-id="ceb8e-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="ceb8e-103">取得此[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)所參考之進程的可執行檔完整路徑。</span><span class="sxs-lookup"><span data-stu-id="ceb8e-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceb8e-104">語法</span><span class="sxs-lookup"><span data-stu-id="ceb8e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,   
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR                        *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ceb8e-105">參數</span><span class="sxs-lookup"><span data-stu-id="ceb8e-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="ceb8e-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="ceb8e-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ceb8e-107">脫銷`szName` 陣列中傳回的寬字元數。</span><span class="sxs-lookup"><span data-stu-id="ceb8e-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="ceb8e-108">脫銷用來儲存可執行檔之名稱的陣列，包括完整路徑。</span><span class="sxs-lookup"><span data-stu-id="ceb8e-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="ceb8e-109">名稱是以 null 結束。</span><span class="sxs-lookup"><span data-stu-id="ceb8e-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ceb8e-110">需求</span><span class="sxs-lookup"><span data-stu-id="ceb8e-110">Requirements</span></span>  
 <span data-ttu-id="ceb8e-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ceb8e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ceb8e-112">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="ceb8e-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ceb8e-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ceb8e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ceb8e-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ceb8e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceb8e-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="ceb8e-115">See also</span></span>

- [<span data-ttu-id="ceb8e-116">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="ceb8e-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)

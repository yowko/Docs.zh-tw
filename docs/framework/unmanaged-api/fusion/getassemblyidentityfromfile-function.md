---
title: GetAssemblyIdentityFromFile 函式
ms.date: 03/30/2017
api_name:
- GetAssemblyIdentityFromFile
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyIdentityFromFile
helpviewer_keywords:
- GetAssemblyIdentityFromFile function [.NET Framework fusion]
ms.assetid: 2c32da53-76c7-4048-84d0-d05207333004
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f5dd25ec2a6a1b0b5d6266c3d8e728bd128a9ed
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59106310"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="abb4d-102">GetAssemblyIdentityFromFile 函式</span><span class="sxs-lookup"><span data-stu-id="abb4d-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="abb4d-103">取得指標`IUnknown`使用指定的物件`IID`中指定的檔案路徑中的組件。</span><span class="sxs-lookup"><span data-stu-id="abb4d-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abb4d-104">語法</span><span class="sxs-lookup"><span data-stu-id="abb4d-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="abb4d-105">參數</span><span class="sxs-lookup"><span data-stu-id="abb4d-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="abb4d-106">[in]要求的組件的有效路徑。</span><span class="sxs-lookup"><span data-stu-id="abb4d-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="abb4d-107">[in]`IID`来傳回的介面。</span><span class="sxs-lookup"><span data-stu-id="abb4d-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="abb4d-108">[out]傳回的介面指標。</span><span class="sxs-lookup"><span data-stu-id="abb4d-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abb4d-109">需求</span><span class="sxs-lookup"><span data-stu-id="abb4d-109">Requirements</span></span>  
 <span data-ttu-id="abb4d-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="abb4d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abb4d-111">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="abb4d-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="abb4d-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abb4d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abb4d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abb4d-113">See also</span></span>

- [<span data-ttu-id="abb4d-114">IUnknown</span><span class="sxs-lookup"><span data-stu-id="abb4d-114">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="abb4d-115">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="abb4d-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

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
ms.openlocfilehash: 20ea800b86a169eff984b6068db3e9887235a034
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496972"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="f6f19-102">GetAssemblyIdentityFromFile 函式</span><span class="sxs-lookup"><span data-stu-id="f6f19-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="f6f19-103">取得指標`IUnknown`使用指定的物件`IID`中指定的檔案路徑中的組件。</span><span class="sxs-lookup"><span data-stu-id="f6f19-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6f19-104">語法</span><span class="sxs-lookup"><span data-stu-id="f6f19-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6f19-105">參數</span><span class="sxs-lookup"><span data-stu-id="f6f19-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="f6f19-106">[in]要求的組件的有效路徑。</span><span class="sxs-lookup"><span data-stu-id="f6f19-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="f6f19-107">[in]`IID`来傳回的介面。</span><span class="sxs-lookup"><span data-stu-id="f6f19-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="f6f19-108">[out]傳回的介面指標。</span><span class="sxs-lookup"><span data-stu-id="f6f19-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6f19-109">需求</span><span class="sxs-lookup"><span data-stu-id="f6f19-109">Requirements</span></span>  
 <span data-ttu-id="f6f19-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f6f19-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6f19-111">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="f6f19-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f6f19-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6f19-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6f19-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6f19-113">See also</span></span>
- [<span data-ttu-id="f6f19-114">IUnknown</span><span class="sxs-lookup"><span data-stu-id="f6f19-114">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="f6f19-115">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="f6f19-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

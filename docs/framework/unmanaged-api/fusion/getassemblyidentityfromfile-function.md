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
ms.openlocfilehash: 581c675cfb69503e6366471a469ffed1a2d13b1a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745238"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="0cac9-102">GetAssemblyIdentityFromFile 函式</span><span class="sxs-lookup"><span data-stu-id="0cac9-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="0cac9-103">取得指標`IUnknown`使用指定的物件`IID`中指定的檔案路徑中的組件。</span><span class="sxs-lookup"><span data-stu-id="0cac9-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cac9-104">語法</span><span class="sxs-lookup"><span data-stu-id="0cac9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="0cac9-105">參數</span><span class="sxs-lookup"><span data-stu-id="0cac9-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="0cac9-106">[in]要求的組件的有效路徑。</span><span class="sxs-lookup"><span data-stu-id="0cac9-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="0cac9-107">[in]`IID`来傳回的介面。</span><span class="sxs-lookup"><span data-stu-id="0cac9-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="0cac9-108">[out]傳回的介面指標。</span><span class="sxs-lookup"><span data-stu-id="0cac9-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cac9-109">需求</span><span class="sxs-lookup"><span data-stu-id="0cac9-109">Requirements</span></span>  
 <span data-ttu-id="0cac9-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0cac9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cac9-111">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="0cac9-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="0cac9-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cac9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cac9-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cac9-113">See also</span></span>

- [<span data-ttu-id="0cac9-114">IUnknown</span><span class="sxs-lookup"><span data-stu-id="0cac9-114">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="0cac9-115">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="0cac9-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

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
ms.openlocfilehash: 5ea151417a1cb53104ec29fff1e76e21f82ec9bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431639"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="49da3-102">GetAssemblyIdentityFromFile 函式</span><span class="sxs-lookup"><span data-stu-id="49da3-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="49da3-103">取得指標`IUnknown`物件具有指定`IID`中位於指定的檔案路徑的組件。</span><span class="sxs-lookup"><span data-stu-id="49da3-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49da3-104">語法</span><span class="sxs-lookup"><span data-stu-id="49da3-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="49da3-105">參數</span><span class="sxs-lookup"><span data-stu-id="49da3-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="49da3-106">[in]要求的組件的有效路徑。</span><span class="sxs-lookup"><span data-stu-id="49da3-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="49da3-107">[in]`IID`来傳回的介面。</span><span class="sxs-lookup"><span data-stu-id="49da3-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="49da3-108">[out]傳回的介面指標。</span><span class="sxs-lookup"><span data-stu-id="49da3-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49da3-109">需求</span><span class="sxs-lookup"><span data-stu-id="49da3-109">Requirements</span></span>  
 <span data-ttu-id="49da3-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="49da3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49da3-111">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="49da3-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="49da3-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49da3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49da3-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49da3-113">See Also</span></span>  
 <span data-ttu-id="49da3-114"><<!--zzxref:IUnknown --> `IUnknown`></span><span class="sxs-lookup"><span data-stu-id="49da3-114"><<!--zzxref:IUnknown --> `IUnknown`></span></span>  
 [<span data-ttu-id="49da3-115">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="49da3-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

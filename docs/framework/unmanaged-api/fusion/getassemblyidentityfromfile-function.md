---
title: "GetAssemblyIdentityFromFile 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetAssemblyIdentityFromFile
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: COM
f1_keywords: GetAssemblyIdentityFromFile
helpviewer_keywords: GetAssemblyIdentityFromFile function [.NET Framework fusion]
ms.assetid: 2c32da53-76c7-4048-84d0-d05207333004
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9f3374553df02193a6b726f37a53a929533e86cd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="acd1f-102">GetAssemblyIdentityFromFile 函式</span><span class="sxs-lookup"><span data-stu-id="acd1f-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="acd1f-103">取得指標`IUnknown`物件具有指定`IID`中位於指定的檔案路徑的組件。</span><span class="sxs-lookup"><span data-stu-id="acd1f-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acd1f-104">語法</span><span class="sxs-lookup"><span data-stu-id="acd1f-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="acd1f-105">參數</span><span class="sxs-lookup"><span data-stu-id="acd1f-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="acd1f-106">[in]要求的組件的有效路徑。</span><span class="sxs-lookup"><span data-stu-id="acd1f-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="acd1f-107">[in]`IID`来傳回的介面。</span><span class="sxs-lookup"><span data-stu-id="acd1f-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="acd1f-108">[out]傳回的介面指標。</span><span class="sxs-lookup"><span data-stu-id="acd1f-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acd1f-109">需求</span><span class="sxs-lookup"><span data-stu-id="acd1f-109">Requirements</span></span>  
 <span data-ttu-id="acd1f-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="acd1f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acd1f-111">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="acd1f-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="acd1f-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acd1f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acd1f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acd1f-113">See Also</span></span>  
 <span data-ttu-id="acd1f-114"><<!--zzxref:IUnknown --> `IUnknown`></span><span class="sxs-lookup"><span data-stu-id="acd1f-114"><<!--zzxref:IUnknown --> `IUnknown`></span></span>  
 [<span data-ttu-id="acd1f-115">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="acd1f-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

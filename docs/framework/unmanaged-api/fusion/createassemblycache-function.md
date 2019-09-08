---
title: CreateAssemblyCache 函式
ms.date: 03/30/2017
api_name:
- CreateAssemblyCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyCache
helpviewer_keywords:
- CreateAssemblyCache function [.NET Framework fusion]
ms.assetid: 348c7c8c-8578-46ae-97cf-480d6015c3c6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c855d6f85c3cbfa6d81a1fbce3ef5b83abb3f583
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795403"
---
# <a name="createassemblycache-function"></a><span data-ttu-id="d63ae-102">CreateAssemblyCache 函式</span><span class="sxs-lookup"><span data-stu-id="d63ae-102">CreateAssemblyCache Function</span></span>
<span data-ttu-id="d63ae-103">取得代表全域組件快取之新[IAssemblyCache](iassemblycache-interface.md)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="d63ae-103">Gets a pointer to a new [IAssemblyCache](iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d63ae-104">語法</span><span class="sxs-lookup"><span data-stu-id="d63ae-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="d63ae-105">參數</span><span class="sxs-lookup"><span data-stu-id="d63ae-105">Parameters</span></span>  
 `ppAsmCache`  
 <span data-ttu-id="d63ae-106">脫銷傳回`IAssemblyCache`的指標。</span><span class="sxs-lookup"><span data-stu-id="d63ae-106">[out] The returned `IAssemblyCache` pointer.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="d63ae-107">在保留以供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="d63ae-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="d63ae-108">`dwReserved`必須是0（零）。</span><span class="sxs-lookup"><span data-stu-id="d63ae-108">`dwReserved` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d63ae-109">需求</span><span class="sxs-lookup"><span data-stu-id="d63ae-109">Requirements</span></span>  
 <span data-ttu-id="d63ae-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d63ae-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d63ae-111">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="d63ae-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d63ae-112">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d63ae-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d63ae-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d63ae-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d63ae-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d63ae-114">See also</span></span>

- [<span data-ttu-id="d63ae-115">IAssemblyCache 介面</span><span class="sxs-lookup"><span data-stu-id="d63ae-115">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="d63ae-116">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="d63ae-116">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="d63ae-117">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="d63ae-117">Global Assembly Cache</span></span>](../../app-domains/gac.md)

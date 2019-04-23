---
title: PreBindAssemblyEx 函式
ms.date: 03/30/2017
api_name:
- PreBindAssemblyEx
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- PreBindAssemblyEx
helpviewer_keywords:
- PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8251d21fe535f85cc6abd0a7bc6c96ab320007f0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090234"
---
# <a name="prebindassemblyex-function"></a><span data-ttu-id="4a458-102">PreBindAssemblyEx 函式</span><span class="sxs-lookup"><span data-stu-id="4a458-102">PreBindAssemblyEx Function</span></span>
<span data-ttu-id="4a458-103">取得組件的原則後顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="4a458-103">Gets the post-policy display name for an assembly.</span></span>  
  
 <span data-ttu-id="4a458-104">此函式支援.NET Framework 基礎結構，並不是直接從您的程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="4a458-104">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a458-105">語法</span><span class="sxs-lookup"><span data-stu-id="4a458-105">Syntax</span></span>  
  
```  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a458-106">參數</span><span class="sxs-lookup"><span data-stu-id="4a458-106">Parameters</span></span>  
 `pAppCtx`  
 <span data-ttu-id="4a458-107">[in]識別應用程式內容。</span><span class="sxs-lookup"><span data-stu-id="4a458-107">[in] Identifies the application context.</span></span>  
  
 `pName`  
 <span data-ttu-id="4a458-108">[in]識別組件名稱。</span><span class="sxs-lookup"><span data-stu-id="4a458-108">[in] Identifies the assembly name.</span></span>  
  
 `pAsmParent`  
 <span data-ttu-id="4a458-109">[in]識別父組件。</span><span class="sxs-lookup"><span data-stu-id="4a458-109">[in] Identifies the parent assembly.</span></span> <span data-ttu-id="4a458-110">這個參數已忽略。</span><span class="sxs-lookup"><span data-stu-id="4a458-110">This parameter is ignored.</span></span>  
  
 `pwzRuntimeVersion`  
 <span data-ttu-id="4a458-111">[in]識別執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="4a458-111">[in] Identifies the runtime version.</span></span>  
  
 `ppNamePostPolicy`  
 <span data-ttu-id="4a458-112">[out]包含的原則後顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="4a458-112">[out] Contains the post-policy display name.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="4a458-113">[in]保留供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="4a458-113">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="4a458-114">`pvReserved` 必須是 null 參考。</span><span class="sxs-lookup"><span data-stu-id="4a458-114">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a458-115">備註</span><span class="sxs-lookup"><span data-stu-id="4a458-115">Remarks</span></span>  
 <span data-ttu-id="4a458-116">`ppNamePostPolicy`函式會傳回 HRESULT FUSION_E_REF_DEF_MISMATCH 時，才設定輸出參數。</span><span class="sxs-lookup"><span data-stu-id="4a458-116">The `ppNamePostPolicy` output parameter is set only if the function returns HRESULT FUSION_E_REF_DEF_MISMATCH.</span></span> <span data-ttu-id="4a458-117">否則，它是 null。</span><span class="sxs-lookup"><span data-stu-id="4a458-117">Otherwise, it is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a458-118">需求</span><span class="sxs-lookup"><span data-stu-id="4a458-118">Requirements</span></span>  
 <span data-ttu-id="4a458-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4a458-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a458-120">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="4a458-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4a458-121">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4a458-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4a458-122">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a458-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a458-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a458-123">See also</span></span>

- [<span data-ttu-id="4a458-124">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="4a458-124">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

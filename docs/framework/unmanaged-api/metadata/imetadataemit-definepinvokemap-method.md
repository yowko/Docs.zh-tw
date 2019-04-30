---
title: IMetaDataEmit::DefinePinvokeMap 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePinvokeMap
helpviewer_keywords:
- DefinePinvokeMap method [.NET Framework metadata]
- IMetaDataEmit::DefinePinvokeMap method [.NET Framework metadata]
ms.assetid: 03abf921-5154-4070-88fa-10b7092901fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15fd75ae807ee5cd7f94f6e650639c3be0628429
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043897"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="90532-102">IMetaDataEmit::DefinePinvokeMap 方法</span><span class="sxs-lookup"><span data-stu-id="90532-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="90532-103">設定指定的語彙基元所參考方法的 PInvoke 簽章的功能。</span><span class="sxs-lookup"><span data-stu-id="90532-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90532-104">語法</span><span class="sxs-lookup"><span data-stu-id="90532-104">Syntax</span></span>  
  
```  
HRESULT DefinePinvokeMap (   
    [in]  mdToken            tk,   
    [in]  DWORD              dwMappingFlags,   
    [in]  LPCWSTR            szImportName,   
    [in]  mdModuleRef        mrImportDLL   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90532-105">參數</span><span class="sxs-lookup"><span data-stu-id="90532-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="90532-106">[in]目標方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="90532-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="90532-107">[in]PInvoke 用來進行對應的旗標。</span><span class="sxs-lookup"><span data-stu-id="90532-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="90532-108">[in]方法在 unmanaged DLL 中的匯出目標的名稱。</span><span class="sxs-lookup"><span data-stu-id="90532-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="90532-109">[in]目標的語彙基元的原生 DLL。</span><span class="sxs-lookup"><span data-stu-id="90532-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90532-110">需求</span><span class="sxs-lookup"><span data-stu-id="90532-110">Requirements</span></span>  
 <span data-ttu-id="90532-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="90532-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90532-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="90532-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="90532-113">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="90532-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="90532-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90532-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90532-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90532-115">See also</span></span>

- [<span data-ttu-id="90532-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="90532-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="90532-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="90532-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

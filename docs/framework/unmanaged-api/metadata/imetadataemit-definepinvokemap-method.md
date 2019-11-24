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
ms.openlocfilehash: 9d4ea16a212ac5f0120d63510f07eaee69af739e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431482"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="39071-102">IMetaDataEmit::DefinePinvokeMap 方法</span><span class="sxs-lookup"><span data-stu-id="39071-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="39071-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span><span class="sxs-lookup"><span data-stu-id="39071-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39071-104">語法</span><span class="sxs-lookup"><span data-stu-id="39071-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePinvokeMap (   
    [in]  mdToken            tk,   
    [in]  DWORD              dwMappingFlags,   
    [in]  LPCWSTR            szImportName,   
    [in]  mdModuleRef        mrImportDLL   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39071-105">參數</span><span class="sxs-lookup"><span data-stu-id="39071-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="39071-106">[in] The token for the target method.</span><span class="sxs-lookup"><span data-stu-id="39071-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="39071-107">[in] Flags used by PInvoke to do the mapping.</span><span class="sxs-lookup"><span data-stu-id="39071-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="39071-108">[in] The name of the target export method in an unmanaged DLL.</span><span class="sxs-lookup"><span data-stu-id="39071-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="39071-109">[in] The token for the target native DLL.</span><span class="sxs-lookup"><span data-stu-id="39071-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39071-110">需求</span><span class="sxs-lookup"><span data-stu-id="39071-110">Requirements</span></span>  
 <span data-ttu-id="39071-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="39071-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39071-112">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="39071-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="39071-113">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="39071-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="39071-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39071-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39071-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="39071-115">See also</span></span>

- [<span data-ttu-id="39071-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="39071-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="39071-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="39071-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

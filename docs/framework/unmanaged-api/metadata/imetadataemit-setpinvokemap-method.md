---
title: IMetaDataEmit::SetPinvokeMap 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPinvokeMap
helpviewer_keywords:
- IMetaDataEmit::SetPinvokeMap method [.NET Framework metadata]
- SetPinvokeMap method [.NET Framework metadata]
ms.assetid: c6bfd574-1da3-4ba7-82f2-46ca5efcbaba
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b838a83a160707e546b05ef334eb17d0c6e6cc27
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133558"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="ec57c-102">IMetaDataEmit::SetPinvokeMap 方法</span><span class="sxs-lookup"><span data-stu-id="ec57c-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="ec57c-103">設定或變更方法的 PInvoke 簽章的功能，如先前呼叫所定義[imetadataemit:: Definepinvokemap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md)。</span><span class="sxs-lookup"><span data-stu-id="ec57c-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec57c-104">語法</span><span class="sxs-lookup"><span data-stu-id="ec57c-104">Syntax</span></span>  
  
```  
HRESULT SetPinvokeMap (   
    [in]  mdToken      tk,   
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,   
    [in]  mdModuleRef  mrImportDLL   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec57c-105">參數</span><span class="sxs-lookup"><span data-stu-id="ec57c-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="ec57c-106">[in]`mdToken`資訊所套用至對應。</span><span class="sxs-lookup"><span data-stu-id="ec57c-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="ec57c-107">[in]PInvoke 用來進行對應的旗標。</span><span class="sxs-lookup"><span data-stu-id="ec57c-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="ec57c-108">這是位元遮罩`CorPinvokeMap`值。</span><span class="sxs-lookup"><span data-stu-id="ec57c-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="ec57c-109">[in]原生 DLL 中匯出目標的名稱。</span><span class="sxs-lookup"><span data-stu-id="ec57c-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="ec57c-110">[in]`mdModuleRef`目標的語彙基元 unmanaged DLL。</span><span class="sxs-lookup"><span data-stu-id="ec57c-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec57c-111">需求</span><span class="sxs-lookup"><span data-stu-id="ec57c-111">Requirements</span></span>  
 <span data-ttu-id="ec57c-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ec57c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec57c-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ec57c-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ec57c-114">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ec57c-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ec57c-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec57c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec57c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec57c-116">See also</span></span>

- [<span data-ttu-id="ec57c-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="ec57c-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ec57c-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="ec57c-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

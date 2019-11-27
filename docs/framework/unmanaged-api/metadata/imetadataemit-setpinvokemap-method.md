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
ms.openlocfilehash: 4e2a78e2d049e952aa1be0b3a8fd640eb18d0320
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440577"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="72417-102">IMetaDataEmit::SetPinvokeMap 方法</span><span class="sxs-lookup"><span data-stu-id="72417-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="72417-103">設定或變更方法之 PInvoke 簽章的功能，如先前的 IMetaDataEmit 呼叫所定義[：:D 的 efinepinvokemap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md)。</span><span class="sxs-lookup"><span data-stu-id="72417-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72417-104">語法</span><span class="sxs-lookup"><span data-stu-id="72417-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPinvokeMap (   
    [in]  mdToken      tk,   
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,   
    [in]  mdModuleRef  mrImportDLL   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72417-105">參數</span><span class="sxs-lookup"><span data-stu-id="72417-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="72417-106">在套用對應資訊的 `mdToken`。</span><span class="sxs-lookup"><span data-stu-id="72417-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="72417-107">在PInvoke 用來執行對應的旗標。</span><span class="sxs-lookup"><span data-stu-id="72417-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="72417-108">這是 `CorPinvokeMap` 值的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="72417-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="72417-109">在原生 DLL 中的目標匯出名稱。</span><span class="sxs-lookup"><span data-stu-id="72417-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="72417-110">在目標非受控 DLL 的 `mdModuleRef` token。</span><span class="sxs-lookup"><span data-stu-id="72417-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72417-111">需求</span><span class="sxs-lookup"><span data-stu-id="72417-111">Requirements</span></span>  
 <span data-ttu-id="72417-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="72417-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72417-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="72417-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="72417-114">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="72417-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72417-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72417-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72417-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72417-116">See also</span></span>

- [<span data-ttu-id="72417-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="72417-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="72417-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="72417-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

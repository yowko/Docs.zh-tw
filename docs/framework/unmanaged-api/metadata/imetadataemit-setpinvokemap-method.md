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
ms.openlocfilehash: 84b2c0571a7991829e65b45759bd61fa4009aa71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445873"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="54f13-102">IMetaDataEmit::SetPinvokeMap 方法</span><span class="sxs-lookup"><span data-stu-id="54f13-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="54f13-103">設定或變更在先前呼叫所定義的功能，該方法的 PInvoke 簽章， [imetadataemit:: Definepinvokemap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md)。</span><span class="sxs-lookup"><span data-stu-id="54f13-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54f13-104">語法</span><span class="sxs-lookup"><span data-stu-id="54f13-104">Syntax</span></span>  
  
```  
HRESULT SetPinvokeMap (   
    [in]  mdToken      tk,   
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,   
    [in]  mdModuleRef  mrImportDLL   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="54f13-105">參數</span><span class="sxs-lookup"><span data-stu-id="54f13-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="54f13-106">[in]`mdToken`資訊套用到對應。</span><span class="sxs-lookup"><span data-stu-id="54f13-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="54f13-107">[in]用來執行對應 PInvoke 旗標。</span><span class="sxs-lookup"><span data-stu-id="54f13-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="54f13-108">這是位元遮罩`CorPinvokeMap`值。</span><span class="sxs-lookup"><span data-stu-id="54f13-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="54f13-109">[in]原生 DLL 中匯出目標的名稱。</span><span class="sxs-lookup"><span data-stu-id="54f13-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="54f13-110">[in]`mdModuleRef`權杖的目標 unmanaged DLL。</span><span class="sxs-lookup"><span data-stu-id="54f13-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54f13-111">需求</span><span class="sxs-lookup"><span data-stu-id="54f13-111">Requirements</span></span>  
 <span data-ttu-id="54f13-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="54f13-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54f13-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="54f13-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="54f13-114">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="54f13-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54f13-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54f13-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54f13-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54f13-116">See Also</span></span>  
 [<span data-ttu-id="54f13-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="54f13-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="54f13-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="54f13-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

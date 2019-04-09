---
title: IMetaDataDispenserEx::FindAssembly 方法
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.FindAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::FindAssembly
helpviewer_keywords:
- FindAssembly method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssembly method [.NET Framework metadata]
ms.assetid: 3afe7252-5f28-48d9-a74d-1927566c404c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d204ec29304fe0c4596950cd17c48d0c1d2ac616
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59152616"
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="9ed3b-102">IMetaDataDispenserEx::FindAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="9ed3b-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="9ed3b-103">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="9ed3b-103">This method is not implemented.</span></span> <span data-ttu-id="9ed3b-104">如果呼叫，它會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="9ed3b-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ed3b-105">語法</span><span class="sxs-lookup"><span data-stu-id="9ed3b-105">Syntax</span></span>  
  
```  
HRESULT FindAssembly(  
    [in]  LPCWSTR  szAppBase,  
    [in]  LPCWSTR  szPrivateBin,  
    [in]  LPCWSTR  szGlobalBin,  
    [in]  LPCWSTR  szAssemblyName,  
    [out] LPCWSTR  szName,  
    [in]  ULONG    cchName,  
    [out] ULONG    *pcName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ed3b-106">參數</span><span class="sxs-lookup"><span data-stu-id="9ed3b-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="9ed3b-107">[in]不使用。</span><span class="sxs-lookup"><span data-stu-id="9ed3b-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="9ed3b-108">[in]不使用。</span><span class="sxs-lookup"><span data-stu-id="9ed3b-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="9ed3b-109">[in]不使用。</span><span class="sxs-lookup"><span data-stu-id="9ed3b-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="9ed3b-110">[in]要找的組件。</span><span class="sxs-lookup"><span data-stu-id="9ed3b-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="9ed3b-111">[out]組件的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="9ed3b-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="9ed3b-112">[in]大小，以位元組為單位的`szName`。</span><span class="sxs-lookup"><span data-stu-id="9ed3b-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="9ed3b-113">[out]中實際傳回的字元數`szName`。</span><span class="sxs-lookup"><span data-stu-id="9ed3b-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ed3b-114">需求</span><span class="sxs-lookup"><span data-stu-id="9ed3b-114">Requirements</span></span>  
 <span data-ttu-id="9ed3b-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9ed3b-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ed3b-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9ed3b-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9ed3b-117">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9ed3b-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="9ed3b-118">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="9ed3b-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9ed3b-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ed3b-119">See also</span></span>

- [<span data-ttu-id="9ed3b-120">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="9ed3b-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="9ed3b-121">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="9ed3b-121">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)

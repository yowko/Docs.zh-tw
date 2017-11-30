---
title: "IMetaDataDispenserEx::FindAssembly 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.FindAssembly
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::FindAssembly
helpviewer_keywords:
- FindAssembly method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssembly method [.NET Framework metadata]
ms.assetid: 3afe7252-5f28-48d9-a74d-1927566c404c
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7a70d1e2b3636a405fe28b84c2e76dd7264df4f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="3d8bc-102">IMetaDataDispenserEx::FindAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="3d8bc-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="3d8bc-103">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="3d8bc-103">This method is not implemented.</span></span> <span data-ttu-id="3d8bc-104">如果呼叫，它會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="3d8bc-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d8bc-105">語法</span><span class="sxs-lookup"><span data-stu-id="3d8bc-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="3d8bc-106">參數</span><span class="sxs-lookup"><span data-stu-id="3d8bc-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="3d8bc-107">[in]未使用。</span><span class="sxs-lookup"><span data-stu-id="3d8bc-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="3d8bc-108">[in]未使用。</span><span class="sxs-lookup"><span data-stu-id="3d8bc-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="3d8bc-109">[in]未使用。</span><span class="sxs-lookup"><span data-stu-id="3d8bc-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="3d8bc-110">[in]找不到組件。</span><span class="sxs-lookup"><span data-stu-id="3d8bc-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="3d8bc-111">[out]組件的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="3d8bc-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="3d8bc-112">[in]大小，以位元組為單位的`szName`。</span><span class="sxs-lookup"><span data-stu-id="3d8bc-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="3d8bc-113">[out]中實際傳回的字元數`szName`。</span><span class="sxs-lookup"><span data-stu-id="3d8bc-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d8bc-114">需求</span><span class="sxs-lookup"><span data-stu-id="3d8bc-114">Requirements</span></span>  
 <span data-ttu-id="3d8bc-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3d8bc-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d8bc-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3d8bc-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3d8bc-117">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3d8bc-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3d8bc-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d8bc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d8bc-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d8bc-119">See Also</span></span>  
 [<span data-ttu-id="3d8bc-120">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="3d8bc-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="3d8bc-121">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="3d8bc-121">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)

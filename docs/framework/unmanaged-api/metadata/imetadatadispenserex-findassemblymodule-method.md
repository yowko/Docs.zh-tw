---
title: IMetaDataDispenserEx::FindAssemblyModule 方法
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.FindAssemblyModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::FindAssemblyModule
helpviewer_keywords:
- FindAssemblyModule method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssemblyModule method [.NET Framework metadata]
ms.assetid: d1fb65e1-7e19-4513-85b1-44f87c294d3e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2d1d97e443be884f45187a2811ddfce106249515
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62044352"
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="2ac1f-102">IMetaDataDispenserEx::FindAssemblyModule 方法</span><span class="sxs-lookup"><span data-stu-id="2ac1f-102">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>
<span data-ttu-id="2ac1f-103">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="2ac1f-103">This method is not implemented.</span></span> <span data-ttu-id="2ac1f-104">如果呼叫，它會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="2ac1f-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ac1f-105">語法</span><span class="sxs-lookup"><span data-stu-id="2ac1f-105">Syntax</span></span>  
  
```  
HRESULT FindAssemblyModule(  
    [in]  LPCWSTR  szAppBase,  
    [in]  LPCWSTR  szPrivateBin,  
    [in]  LPCWSTR  szGlobalBin,  
    [in]  LPCWSTR  szAssemblyName,  
    [in]  LPCWSTR  szModuleName,  
    [out] LPCWSTR  szName,  
    [in]  ULONG    cchName,  
    [out] ULONG    *pcName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ac1f-106">參數</span><span class="sxs-lookup"><span data-stu-id="2ac1f-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="2ac1f-107">[in]不使用。</span><span class="sxs-lookup"><span data-stu-id="2ac1f-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="2ac1f-108">[in]不使用。</span><span class="sxs-lookup"><span data-stu-id="2ac1f-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="2ac1f-109">[in]不使用。</span><span class="sxs-lookup"><span data-stu-id="2ac1f-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="2ac1f-110">[in]模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="2ac1f-110">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="2ac1f-111">[in]要找的組件。</span><span class="sxs-lookup"><span data-stu-id="2ac1f-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="2ac1f-112">[out]組件的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="2ac1f-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="2ac1f-113">[in]大小，以位元組為單位的`szName`。</span><span class="sxs-lookup"><span data-stu-id="2ac1f-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="2ac1f-114">[out]中實際傳回的字元數`szName`。</span><span class="sxs-lookup"><span data-stu-id="2ac1f-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ac1f-115">需求</span><span class="sxs-lookup"><span data-stu-id="2ac1f-115">Requirements</span></span>  
 <span data-ttu-id="2ac1f-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2ac1f-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ac1f-117">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2ac1f-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2ac1f-118">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2ac1f-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2ac1f-119">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ac1f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ac1f-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ac1f-120">See also</span></span>

- [<span data-ttu-id="2ac1f-121">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="2ac1f-121">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="2ac1f-122">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="2ac1f-122">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)

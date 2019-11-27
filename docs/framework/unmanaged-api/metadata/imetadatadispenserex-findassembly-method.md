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
ms.openlocfilehash: 2d974b7368dd01062d2d310d076dce05e102eb81
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442287"
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="8d8e6-102">IMetaDataDispenserEx::FindAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="8d8e6-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="8d8e6-103">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="8d8e6-103">This method is not implemented.</span></span> <span data-ttu-id="8d8e6-104">如果呼叫，它會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="8d8e6-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d8e6-105">語法</span><span class="sxs-lookup"><span data-stu-id="8d8e6-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="8d8e6-106">參數</span><span class="sxs-lookup"><span data-stu-id="8d8e6-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="8d8e6-107">在未使用。</span><span class="sxs-lookup"><span data-stu-id="8d8e6-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="8d8e6-108">在未使用。</span><span class="sxs-lookup"><span data-stu-id="8d8e6-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="8d8e6-109">在未使用。</span><span class="sxs-lookup"><span data-stu-id="8d8e6-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="8d8e6-110">在要尋找的元件。</span><span class="sxs-lookup"><span data-stu-id="8d8e6-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="8d8e6-111">脫銷元件的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="8d8e6-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="8d8e6-112">在`szName`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="8d8e6-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="8d8e6-113">脫銷`szName`中實際傳回的字元數。</span><span class="sxs-lookup"><span data-stu-id="8d8e6-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d8e6-114">需求</span><span class="sxs-lookup"><span data-stu-id="8d8e6-114">Requirements</span></span>  
 <span data-ttu-id="8d8e6-115">**平臺：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8d8e6-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d8e6-116">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="8d8e6-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8d8e6-117">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="8d8e6-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8d8e6-118">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d8e6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d8e6-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="8d8e6-119">See also</span></span>

- [<span data-ttu-id="8d8e6-120">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="8d8e6-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="8d8e6-121">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="8d8e6-121">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)

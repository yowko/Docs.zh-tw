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
ms.openlocfilehash: 64f1e2a8f05616c7ca84bc130428629b1176e985
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006177"
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="189bf-102">IMetaDataDispenserEx::FindAssemblyModule 方法</span><span class="sxs-lookup"><span data-stu-id="189bf-102">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>
<span data-ttu-id="189bf-103">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="189bf-103">This method is not implemented.</span></span> <span data-ttu-id="189bf-104">如果呼叫，它會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="189bf-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="189bf-105">語法</span><span class="sxs-lookup"><span data-stu-id="189bf-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="189bf-106">參數</span><span class="sxs-lookup"><span data-stu-id="189bf-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="189bf-107">在未使用。</span><span class="sxs-lookup"><span data-stu-id="189bf-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="189bf-108">在未使用。</span><span class="sxs-lookup"><span data-stu-id="189bf-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="189bf-109">在未使用。</span><span class="sxs-lookup"><span data-stu-id="189bf-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="189bf-110">在模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="189bf-110">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="189bf-111">在要尋找的元件。</span><span class="sxs-lookup"><span data-stu-id="189bf-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="189bf-112">脫銷元件的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="189bf-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="189bf-113">在的大小（以位元組為單位） `szName` 。</span><span class="sxs-lookup"><span data-stu-id="189bf-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="189bf-114">脫銷中實際傳回的字元數 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="189bf-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="189bf-115">需求</span><span class="sxs-lookup"><span data-stu-id="189bf-115">Requirements</span></span>  
 <span data-ttu-id="189bf-116">**平臺：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="189bf-116">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="189bf-117">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="189bf-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="189bf-118">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="189bf-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="189bf-119">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="189bf-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="189bf-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="189bf-120">See also</span></span>

- [<span data-ttu-id="189bf-121">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="189bf-121">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="189bf-122">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="189bf-122">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)

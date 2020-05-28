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
ms.openlocfilehash: 50aebb09924b93a622e5b7d84e65e41ee91f6018
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006190"
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="bfe7b-102">IMetaDataDispenserEx::FindAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="bfe7b-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="bfe7b-103">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="bfe7b-103">This method is not implemented.</span></span> <span data-ttu-id="bfe7b-104">如果呼叫，它會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="bfe7b-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfe7b-105">語法</span><span class="sxs-lookup"><span data-stu-id="bfe7b-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="bfe7b-106">參數</span><span class="sxs-lookup"><span data-stu-id="bfe7b-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="bfe7b-107">在未使用。</span><span class="sxs-lookup"><span data-stu-id="bfe7b-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="bfe7b-108">在未使用。</span><span class="sxs-lookup"><span data-stu-id="bfe7b-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="bfe7b-109">在未使用。</span><span class="sxs-lookup"><span data-stu-id="bfe7b-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="bfe7b-110">在要尋找的元件。</span><span class="sxs-lookup"><span data-stu-id="bfe7b-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="bfe7b-111">脫銷元件的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="bfe7b-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="bfe7b-112">在的大小（以位元組為單位） `szName` 。</span><span class="sxs-lookup"><span data-stu-id="bfe7b-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="bfe7b-113">脫銷中實際傳回的字元數 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="bfe7b-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfe7b-114">需求</span><span class="sxs-lookup"><span data-stu-id="bfe7b-114">Requirements</span></span>  
 <span data-ttu-id="bfe7b-115">**平臺：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bfe7b-115">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfe7b-116">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="bfe7b-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bfe7b-117">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="bfe7b-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bfe7b-118">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfe7b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfe7b-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfe7b-119">See also</span></span>

- [<span data-ttu-id="bfe7b-120">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="bfe7b-120">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="bfe7b-121">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="bfe7b-121">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)

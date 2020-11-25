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
ms.openlocfilehash: 5bc622c013e62fa9c03476cc5927133682020426
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700596"
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="a5e64-102">IMetaDataDispenserEx::FindAssemblyModule 方法</span><span class="sxs-lookup"><span data-stu-id="a5e64-102">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>

<span data-ttu-id="a5e64-103">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="a5e64-103">This method is not implemented.</span></span> <span data-ttu-id="a5e64-104">如果呼叫，則會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="a5e64-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5e64-105">語法</span><span class="sxs-lookup"><span data-stu-id="a5e64-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a5e64-106">參數</span><span class="sxs-lookup"><span data-stu-id="a5e64-106">Parameters</span></span>  

 `szAppBase`  
 <span data-ttu-id="a5e64-107">在未使用。</span><span class="sxs-lookup"><span data-stu-id="a5e64-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="a5e64-108">在未使用。</span><span class="sxs-lookup"><span data-stu-id="a5e64-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="a5e64-109">在未使用。</span><span class="sxs-lookup"><span data-stu-id="a5e64-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="a5e64-110">在模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="a5e64-110">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="a5e64-111">在要尋找的元件。</span><span class="sxs-lookup"><span data-stu-id="a5e64-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="a5e64-112">擴展元件的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="a5e64-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="a5e64-113">在的大小（以位元組為單位） `szName` 。</span><span class="sxs-lookup"><span data-stu-id="a5e64-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="a5e64-114">擴展實際傳回的字元數 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="a5e64-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5e64-115">需求</span><span class="sxs-lookup"><span data-stu-id="a5e64-115">Requirements</span></span>  

 <span data-ttu-id="a5e64-116">**平臺：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a5e64-116">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5e64-117">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="a5e64-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a5e64-118">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="a5e64-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a5e64-119">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5e64-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5e64-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5e64-120">See also</span></span>

- [<span data-ttu-id="a5e64-121">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="a5e64-121">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="a5e64-122">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="a5e64-122">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)

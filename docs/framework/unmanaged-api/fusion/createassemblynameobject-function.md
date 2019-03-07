---
title: CreateAssemblyNameObject 函式
ms.date: 03/30/2017
api_name:
- CreateAssemblyNameObject
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyNameObject
helpviewer_keywords:
- CreateAssemblyNameObject function [.NET Framework fusion]
ms.assetid: 55c8b41e-fbe4-4ae0-aa29-68fbb2311691
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f7192b97b4fe1013c6ad4268f50288d6231e7f1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485586"
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="4534d-102">CreateAssemblyNameObject 函式</span><span class="sxs-lookup"><span data-stu-id="4534d-102">CreateAssemblyNameObject Function</span></span>
<span data-ttu-id="4534d-103">取得的介面指標[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)執行個體，表示具有指定名稱的組件的唯一識別。</span><span class="sxs-lookup"><span data-stu-id="4534d-103">Gets an interface pointer to an [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4534d-104">語法</span><span class="sxs-lookup"><span data-stu-id="4534d-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="4534d-105">參數</span><span class="sxs-lookup"><span data-stu-id="4534d-105">Parameters</span></span>  
 `ppAssemblyNameObj`  
 <span data-ttu-id="4534d-106">[out]傳回`IAssemblyName`。</span><span class="sxs-lookup"><span data-stu-id="4534d-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="4534d-107">[in]要建立新的組件名稱`IAssemblyName`執行個體。</span><span class="sxs-lookup"><span data-stu-id="4534d-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="4534d-108">[in]要傳遞給物件建構函式的旗標。</span><span class="sxs-lookup"><span data-stu-id="4534d-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="4534d-109">[in]保留供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="4534d-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="4534d-110">`pvReserved` 必須是 null 參考。</span><span class="sxs-lookup"><span data-stu-id="4534d-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4534d-111">需求</span><span class="sxs-lookup"><span data-stu-id="4534d-111">Requirements</span></span>  
 <span data-ttu-id="4534d-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4534d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4534d-113">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="4534d-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4534d-114">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4534d-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4534d-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4534d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4534d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4534d-116">See also</span></span>
- [<span data-ttu-id="4534d-117">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="4534d-117">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="4534d-118">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="4534d-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

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
ms.openlocfilehash: 00345f6c95c67f0494aa721c662f56a9e98cdd7f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108706"
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="a9979-102">CreateAssemblyNameObject 函式</span><span class="sxs-lookup"><span data-stu-id="a9979-102">CreateAssemblyNameObject Function</span></span>
<span data-ttu-id="a9979-103">取得[IAssemblyName](iassemblyname-interface.md)實例的介面指標，表示具有指定名稱之元件的唯一識別。</span><span class="sxs-lookup"><span data-stu-id="a9979-103">Gets an interface pointer to an [IAssemblyName](iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9979-104">語法</span><span class="sxs-lookup"><span data-stu-id="a9979-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9979-105">參數</span><span class="sxs-lookup"><span data-stu-id="a9979-105">Parameters</span></span>  
 `ppAssemblyNameObj`  
 <span data-ttu-id="a9979-106">脫銷傳回的 `IAssemblyName`。</span><span class="sxs-lookup"><span data-stu-id="a9979-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="a9979-107">在要建立新 `IAssemblyName` 實例之元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="a9979-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a9979-108">在要傳遞至物件的函式的旗標。</span><span class="sxs-lookup"><span data-stu-id="a9979-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="a9979-109">在保留以供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="a9979-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="a9979-110">`pvReserved` 必須是 null 參考。</span><span class="sxs-lookup"><span data-stu-id="a9979-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9979-111">需求</span><span class="sxs-lookup"><span data-stu-id="a9979-111">Requirements</span></span>  
 <span data-ttu-id="a9979-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a9979-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9979-113">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="a9979-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a9979-114">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a9979-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a9979-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9979-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9979-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="a9979-116">See also</span></span>

- [<span data-ttu-id="a9979-117">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="a9979-117">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="a9979-118">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="a9979-118">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)

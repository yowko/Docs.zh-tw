---
title: IAssemblyEnum::GetNextAssembly 方法
ms.date: 03/30/2017
api_name:
- IAssemblyEnum.GetNextAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyEnum::GetNextAssembly
helpviewer_keywords:
- GetNextAssembly method [.NET Framework fusion]
- IAssemblyEnum::GetNextAssembly method [.NET Framework fusion]
ms.assetid: 5d7a4ca2-5f46-4ef1-a9a2-257884e9dc11
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73c531378355100fdfca264ea9f96ff4d7c7ceda
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796683"
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="e8415-102">IAssemblyEnum::GetNextAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="e8415-102">IAssemblyEnum::GetNextAssembly Method</span></span>
<span data-ttu-id="e8415-103">取得包含在這個[IAssemblyEnum](iassemblyenum-interface.md)物件中的下一個[IAssemblyName](iassemblyname-interface.md)的指標。</span><span class="sxs-lookup"><span data-stu-id="e8415-103">Gets a pointer to the next [IAssemblyName](iassemblyname-interface.md) contained in this [IAssemblyEnum](iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8415-104">語法</span><span class="sxs-lookup"><span data-stu-id="e8415-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8415-105">參數</span><span class="sxs-lookup"><span data-stu-id="e8415-105">Parameters</span></span>  
 `pvReserved`  
 <span data-ttu-id="e8415-106">在保留以供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="e8415-106">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="e8415-107">`pvReserved`必須是 null 參考。</span><span class="sxs-lookup"><span data-stu-id="e8415-107">`pvReserved` must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="e8415-108">脫銷傳回`IAssemblyName`的指標。</span><span class="sxs-lookup"><span data-stu-id="e8415-108">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e8415-109">在保留以供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="e8415-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="e8415-110">`dwFlags`必須是0（零）。</span><span class="sxs-lookup"><span data-stu-id="e8415-110">`dwFlags` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8415-111">需求</span><span class="sxs-lookup"><span data-stu-id="e8415-111">Requirements</span></span>  
 <span data-ttu-id="e8415-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e8415-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8415-113">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="e8415-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e8415-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8415-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8415-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8415-115">See also</span></span>

- [<span data-ttu-id="e8415-116">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="e8415-116">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="e8415-117">IAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="e8415-117">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)

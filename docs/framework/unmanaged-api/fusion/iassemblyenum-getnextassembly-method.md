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
ms.openlocfilehash: ade404557d65fa073b6a0e66fe8234b41223ecde
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134442"
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="9647e-102">IAssemblyEnum::GetNextAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="9647e-102">IAssemblyEnum::GetNextAssembly Method</span></span>
<span data-ttu-id="9647e-103">取得包含在這個[IAssemblyEnum](iassemblyenum-interface.md)物件中的下一個[IAssemblyName](iassemblyname-interface.md)的指標。</span><span class="sxs-lookup"><span data-stu-id="9647e-103">Gets a pointer to the next [IAssemblyName](iassemblyname-interface.md) contained in this [IAssemblyEnum](iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9647e-104">語法</span><span class="sxs-lookup"><span data-stu-id="9647e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9647e-105">參數</span><span class="sxs-lookup"><span data-stu-id="9647e-105">Parameters</span></span>  
 `pvReserved`  
 <span data-ttu-id="9647e-106">在保留以供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="9647e-106">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="9647e-107">`pvReserved` 必須是 null 參考。</span><span class="sxs-lookup"><span data-stu-id="9647e-107">`pvReserved` must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="9647e-108">脫銷傳回的 `IAssemblyName` 指標。</span><span class="sxs-lookup"><span data-stu-id="9647e-108">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="9647e-109">在保留以供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="9647e-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="9647e-110">`dwFlags` 必須是0（零）。</span><span class="sxs-lookup"><span data-stu-id="9647e-110">`dwFlags` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9647e-111">需求</span><span class="sxs-lookup"><span data-stu-id="9647e-111">Requirements</span></span>  
 <span data-ttu-id="9647e-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9647e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9647e-113">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="9647e-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="9647e-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9647e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9647e-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="9647e-115">See also</span></span>

- [<span data-ttu-id="9647e-116">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="9647e-116">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="9647e-117">IAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="9647e-117">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)

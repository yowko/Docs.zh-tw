---
title: GetCurrentApartmentType 函式 （Unmanaged API 參考）
description: GetCurrentApartmentType 函式會擷取呼叫端執行的所在的 apartment 的型別。
ms.date: 11/06/2017
api_name:
- GetCurrentApartmentType
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetCurrentApartmentType
helpviewer_keywords:
- GetCurrentApartmentType function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca7b5fa5bf6d845d542d3e80c0571e59f3d4c1e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461720"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="ac814-103">GetCurrentApartmentType 函式</span><span class="sxs-lookup"><span data-stu-id="ac814-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="ac814-104">擷取的 apartment 呼叫者正在執行的所在的型別。</span><span class="sxs-lookup"><span data-stu-id="ac814-104">Retrieves the type of apartment in which the caller is executing.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="ac814-105">語法</span><span class="sxs-lookup"><span data-stu-id="ac814-105">Syntax</span></span>  
  
```  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a><span data-ttu-id="ac814-106">參數</span><span class="sxs-lookup"><span data-stu-id="ac814-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="ac814-107">[in]未使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="ac814-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="ac814-108">[in]指標[IComThreadingInfo](https://msdn.microsoft.com/library/windows/desktop/ms694502(v=vs.85).aspx)執行個體。</span><span class="sxs-lookup"><span data-stu-id="ac814-108">[in] A pointer to an [IComThreadingInfo](https://msdn.microsoft.com/library/windows/desktop/ms694502(v=vs.85).aspx) instance.</span></span>

`aptType`  
<span data-ttu-id="ac814-109">[out]指標[APTTYPE](https://msdn.microsoft.com/library/windows/desktop/ms693793(v=vs.85).aspx)列舉值，指出呼叫端的 apartment。</span><span class="sxs-lookup"><span data-stu-id="ac814-109">[out] A pointer to an [APTTYPE](https://msdn.microsoft.com/library/windows/desktop/ms693793(v=vs.85).aspx) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="ac814-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="ac814-110">Return value</span></span>


|<span data-ttu-id="ac814-111">常數</span><span class="sxs-lookup"><span data-stu-id="ac814-111">Constant</span></span>  |<span data-ttu-id="ac814-112">值</span><span class="sxs-lookup"><span data-stu-id="ac814-112">Value</span></span>  |<span data-ttu-id="ac814-113">描述</span><span class="sxs-lookup"><span data-stu-id="ac814-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="ac814-114">0</span><span class="sxs-lookup"><span data-stu-id="ac814-114">0</span></span> | <span data-ttu-id="ac814-115">已順利完成函式。</span><span class="sxs-lookup"><span data-stu-id="ac814-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="ac814-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="ac814-116">0x80000008</span></span> | <span data-ttu-id="ac814-117">呼叫端不在 apartment 中執行。</span><span class="sxs-lookup"><span data-stu-id="ac814-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="ac814-118">備註</span><span class="sxs-lookup"><span data-stu-id="ac814-118">Remarks</span></span>

<span data-ttu-id="ac814-119">此函式會包裝呼叫[IComThreadingInfo::GetCurrentApartmentType](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="ac814-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ac814-120">需求</span><span class="sxs-lookup"><span data-stu-id="ac814-120">Requirements</span></span>  
 <span data-ttu-id="ac814-121">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ac814-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac814-122">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="ac814-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="ac814-123">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ac814-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac814-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac814-124">See also</span></span>  
[<span data-ttu-id="ac814-125">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="ac814-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

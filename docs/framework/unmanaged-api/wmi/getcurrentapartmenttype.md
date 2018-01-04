---
title: "GetCurrentApartmentType 函式 （Unmanaged API 參考）"
description: "GetCurrentApartmentType 函式會擷取呼叫端執行的所在的 apartment 的型別。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetCurrentApartmentType
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetCurrentApartmentType
helpviewer_keywords: GetCurrentApartmentType function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a42c6c3c778dbdefd4b83621e65b81741b940ebe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="143a5-103">GetCurrentApartmentType 函式</span><span class="sxs-lookup"><span data-stu-id="143a5-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="143a5-104">擷取的 apartment 呼叫者正在執行的所在的型別。</span><span class="sxs-lookup"><span data-stu-id="143a5-104">Retrieves the type of apartment in which the caller is executing.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="143a5-105">語法</span><span class="sxs-lookup"><span data-stu-id="143a5-105">Syntax</span></span>  
  
```  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a><span data-ttu-id="143a5-106">參數</span><span class="sxs-lookup"><span data-stu-id="143a5-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="143a5-107">[in]未使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="143a5-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="143a5-108">[in]指標[IComThreadingInfo](https://msdn.microsoft.com/library/windows/desktop/ms694502(v=vs.85).aspx)執行個體。</span><span class="sxs-lookup"><span data-stu-id="143a5-108">[in] A pointer to an [IComThreadingInfo](https://msdn.microsoft.com/library/windows/desktop/ms694502(v=vs.85).aspx) instance.</span></span>

`aptType`  
<span data-ttu-id="143a5-109">[out]指標[APTTYPE](https://msdn.microsoft.com/library/windows/desktop/ms693793(v=vs.85).aspx)列舉值，指出呼叫端的 apartment。</span><span class="sxs-lookup"><span data-stu-id="143a5-109">[out] A pointer to an [APTTYPE](https://msdn.microsoft.com/library/windows/desktop/ms693793(v=vs.85).aspx) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="143a5-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="143a5-110">Return value</span></span>


|<span data-ttu-id="143a5-111">常數</span><span class="sxs-lookup"><span data-stu-id="143a5-111">Constant</span></span>  |<span data-ttu-id="143a5-112">值</span><span class="sxs-lookup"><span data-stu-id="143a5-112">Value</span></span>  |<span data-ttu-id="143a5-113">描述</span><span class="sxs-lookup"><span data-stu-id="143a5-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="143a5-114">0</span><span class="sxs-lookup"><span data-stu-id="143a5-114">0</span></span> | <span data-ttu-id="143a5-115">已順利完成函式。</span><span class="sxs-lookup"><span data-stu-id="143a5-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="143a5-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="143a5-116">0x80000008</span></span> | <span data-ttu-id="143a5-117">呼叫端不在 apartment 中執行。</span><span class="sxs-lookup"><span data-stu-id="143a5-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="143a5-118">備註</span><span class="sxs-lookup"><span data-stu-id="143a5-118">Remarks</span></span>

<span data-ttu-id="143a5-119">此函式會包裝呼叫[IComThreadingInfo::GetCurrentApartmentType](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="143a5-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="143a5-120">需求</span><span class="sxs-lookup"><span data-stu-id="143a5-120">Requirements</span></span>  
 <span data-ttu-id="143a5-121">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="143a5-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="143a5-122">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="143a5-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="143a5-123">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="143a5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="143a5-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="143a5-124">See also</span></span>  
[<span data-ttu-id="143a5-125">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="143a5-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

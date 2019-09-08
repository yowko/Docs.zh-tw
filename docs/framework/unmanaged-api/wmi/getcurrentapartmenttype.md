---
title: GetCurrentApartmentType 函式（非受控 API 參考）
description: GetCurrentApartmentType 函數會抓取呼叫者執行所在的公寓類型。
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
ms.openlocfilehash: ff64be47802a46979818ab54cc3efb4112dd05e0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798622"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="36bb0-103">GetCurrentApartmentType 函式</span><span class="sxs-lookup"><span data-stu-id="36bb0-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="36bb0-104">擷取呼叫者在其中執行之 Apartment 的型別。</span><span class="sxs-lookup"><span data-stu-id="36bb0-104">Retrieves the type of apartment in which the caller is executing.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="36bb0-105">語法</span><span class="sxs-lookup"><span data-stu-id="36bb0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a><span data-ttu-id="36bb0-106">參數</span><span class="sxs-lookup"><span data-stu-id="36bb0-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="36bb0-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="36bb0-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="36bb0-108">在[IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="36bb0-108">[in] A pointer to an [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instance.</span></span>

`aptType`  
<span data-ttu-id="36bb0-109">脫銷[APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype)列舉值的指標，指出呼叫端的單元。</span><span class="sxs-lookup"><span data-stu-id="36bb0-109">[out] A pointer to an [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="36bb0-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="36bb0-110">Return value</span></span>

|<span data-ttu-id="36bb0-111">常數</span><span class="sxs-lookup"><span data-stu-id="36bb0-111">Constant</span></span>  |<span data-ttu-id="36bb0-112">值</span><span class="sxs-lookup"><span data-stu-id="36bb0-112">Value</span></span>  |<span data-ttu-id="36bb0-113">描述</span><span class="sxs-lookup"><span data-stu-id="36bb0-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="36bb0-114">0</span><span class="sxs-lookup"><span data-stu-id="36bb0-114">0</span></span> | <span data-ttu-id="36bb0-115">函數已順利完成。</span><span class="sxs-lookup"><span data-stu-id="36bb0-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="36bb0-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="36bb0-116">0x80000008</span></span> | <span data-ttu-id="36bb0-117">呼叫端不是在單元中執行。</span><span class="sxs-lookup"><span data-stu-id="36bb0-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="36bb0-118">備註</span><span class="sxs-lookup"><span data-stu-id="36bb0-118">Remarks</span></span>

<span data-ttu-id="36bb0-119">此函式會包裝對[IComThreadingInfo：： GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="36bb0-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="36bb0-120">需求</span><span class="sxs-lookup"><span data-stu-id="36bb0-120">Requirements</span></span>  
 <span data-ttu-id="36bb0-121">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="36bb0-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36bb0-122">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="36bb0-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="36bb0-123">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="36bb0-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36bb0-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36bb0-124">See also</span></span>

- [<span data-ttu-id="36bb0-125">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="36bb0-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

---
title: 'GetCurrentApartmentType 函式 (非受控 API 參考) '
description: GetCurrentApartmentType 函式會抓取呼叫端執行所在的單元類型。
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
ms.openlocfilehash: 0832867d86b7dda80e037846d9aa66c1d37f87be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726193"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="f91d6-103">GetCurrentApartmentType 函式</span><span class="sxs-lookup"><span data-stu-id="f91d6-103">GetCurrentApartmentType function</span></span>

<span data-ttu-id="f91d6-104">擷取呼叫者在其中執行之 Apartment 的型別。</span><span class="sxs-lookup"><span data-stu-id="f91d6-104">Retrieves the type of apartment in which the caller is executing.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="f91d6-105">語法</span><span class="sxs-lookup"><span data-stu-id="f91d6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc,
   [in] IComThreadingInfo*    ptr,
   [out] APTTYPE*             aptType
);
```  

## <a name="parameters"></a><span data-ttu-id="f91d6-106">參數</span><span class="sxs-lookup"><span data-stu-id="f91d6-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f91d6-107">在此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="f91d6-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="f91d6-108">在 [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) 實例的指標。</span><span class="sxs-lookup"><span data-stu-id="f91d6-108">[in] A pointer to an [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instance.</span></span>

`aptType`  
<span data-ttu-id="f91d6-109">擴展 [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) 列舉值的指標，指出呼叫端的單元。</span><span class="sxs-lookup"><span data-stu-id="f91d6-109">[out] A pointer to an [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="f91d6-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="f91d6-110">Return value</span></span>

|<span data-ttu-id="f91d6-111">常數</span><span class="sxs-lookup"><span data-stu-id="f91d6-111">Constant</span></span>  |<span data-ttu-id="f91d6-112">值</span><span class="sxs-lookup"><span data-stu-id="f91d6-112">Value</span></span>  |<span data-ttu-id="f91d6-113">描述</span><span class="sxs-lookup"><span data-stu-id="f91d6-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="f91d6-114">0</span><span class="sxs-lookup"><span data-stu-id="f91d6-114">0</span></span> | <span data-ttu-id="f91d6-115">函數已順利完成。</span><span class="sxs-lookup"><span data-stu-id="f91d6-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="f91d6-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="f91d6-116">0x80000008</span></span> | <span data-ttu-id="f91d6-117">呼叫端並未在單元中執行。</span><span class="sxs-lookup"><span data-stu-id="f91d6-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="f91d6-118">備註</span><span class="sxs-lookup"><span data-stu-id="f91d6-118">Remarks</span></span>

<span data-ttu-id="f91d6-119">此函數會包裝對 [IComThreadingInfo：： GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="f91d6-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f91d6-120">需求</span><span class="sxs-lookup"><span data-stu-id="f91d6-120">Requirements</span></span>  

 <span data-ttu-id="f91d6-121">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f91d6-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f91d6-122">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="f91d6-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f91d6-123">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f91d6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f91d6-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f91d6-124">See also</span></span>

- [<span data-ttu-id="f91d6-125">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="f91d6-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

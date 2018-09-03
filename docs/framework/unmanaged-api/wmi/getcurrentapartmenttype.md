---
title: GetCurrentApartmentType 函式 （Unmanaged API 參考）
description: GetCurrentApartmentType 函式會擷取呼叫端執行所在的 apartment 的型別。
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
ms.openlocfilehash: 4de85eb310de70dc8fd61f7c06abca95ec267f87
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463087"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="2abdc-103">GetCurrentApartmentType 函式</span><span class="sxs-lookup"><span data-stu-id="2abdc-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="2abdc-104">擷取呼叫端執行所在的 apartment 的型別。</span><span class="sxs-lookup"><span data-stu-id="2abdc-104">Retrieves the type of apartment in which the caller is executing.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="2abdc-105">語法</span><span class="sxs-lookup"><span data-stu-id="2abdc-105">Syntax</span></span>  
  
```  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a><span data-ttu-id="2abdc-106">參數</span><span class="sxs-lookup"><span data-stu-id="2abdc-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="2abdc-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="2abdc-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="2abdc-108">[in]指標[IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo)執行個體。</span><span class="sxs-lookup"><span data-stu-id="2abdc-108">[in] A pointer to an [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instance.</span></span>

`aptType`  
<span data-ttu-id="2abdc-109">[out]指標[APTTYPE](/windows/desktop/api/objidlbase/ne-objidlbase-_apttype)列舉值，指出呼叫端的 apartment。</span><span class="sxs-lookup"><span data-stu-id="2abdc-109">[out] A pointer to an [APTTYPE](/windows/desktop/api/objidlbase/ne-objidlbase-_apttype) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="2abdc-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="2abdc-110">Return value</span></span>


|<span data-ttu-id="2abdc-111">常數</span><span class="sxs-lookup"><span data-stu-id="2abdc-111">Constant</span></span>  |<span data-ttu-id="2abdc-112">值</span><span class="sxs-lookup"><span data-stu-id="2abdc-112">Value</span></span>  |<span data-ttu-id="2abdc-113">描述</span><span class="sxs-lookup"><span data-stu-id="2abdc-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="2abdc-114">0</span><span class="sxs-lookup"><span data-stu-id="2abdc-114">0</span></span> | <span data-ttu-id="2abdc-115">已成功完成函式。</span><span class="sxs-lookup"><span data-stu-id="2abdc-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="2abdc-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="2abdc-116">0x80000008</span></span> | <span data-ttu-id="2abdc-117">呼叫端不在 apartment 中執行。</span><span class="sxs-lookup"><span data-stu-id="2abdc-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="2abdc-118">備註</span><span class="sxs-lookup"><span data-stu-id="2abdc-118">Remarks</span></span>

<span data-ttu-id="2abdc-119">此函式會包裝在呼叫[IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype)方法。</span><span class="sxs-lookup"><span data-stu-id="2abdc-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2abdc-120">需求</span><span class="sxs-lookup"><span data-stu-id="2abdc-120">Requirements</span></span>  
 <span data-ttu-id="2abdc-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2abdc-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2abdc-122">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="2abdc-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="2abdc-123">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2abdc-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2abdc-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2abdc-124">See also</span></span>  
[<span data-ttu-id="2abdc-125">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="2abdc-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

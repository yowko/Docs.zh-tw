---
title: 獲取當前公寓類型函數（非託管 API 參考）
description: GetCurrent公寓類型函數檢索調用方正在其中執行的公寓類型。
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
ms.openlocfilehash: 3fc88f7997ee5a6c25359243e1ee97a041050eb7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176821"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="5f3f9-103">GetCurrentApartmentType 函式</span><span class="sxs-lookup"><span data-stu-id="5f3f9-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="5f3f9-104">擷取呼叫者在其中執行之 Apartment 的型別。</span><span class="sxs-lookup"><span data-stu-id="5f3f9-104">Retrieves the type of apartment in which the caller is executing.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5f3f9-105">語法</span><span class="sxs-lookup"><span data-stu-id="5f3f9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc,
   [in] IComThreadingInfo*    ptr,
   [out] APTTYPE*             aptType
);
```  

## <a name="parameters"></a><span data-ttu-id="5f3f9-106">參數</span><span class="sxs-lookup"><span data-stu-id="5f3f9-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="5f3f9-107">[在]此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="5f3f9-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="5f3f9-108">[在]指向[IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="5f3f9-108">[in] A pointer to an [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instance.</span></span>

`aptType`  
<span data-ttu-id="5f3f9-109">[出]指向[APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype)枚舉值的指標，指示調用方的公寓。</span><span class="sxs-lookup"><span data-stu-id="5f3f9-109">[out] A pointer to an [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="5f3f9-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="5f3f9-110">Return value</span></span>

|<span data-ttu-id="5f3f9-111">持續性</span><span class="sxs-lookup"><span data-stu-id="5f3f9-111">Constant</span></span>  |<span data-ttu-id="5f3f9-112">值</span><span class="sxs-lookup"><span data-stu-id="5f3f9-112">Value</span></span>  |<span data-ttu-id="5f3f9-113">描述</span><span class="sxs-lookup"><span data-stu-id="5f3f9-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="5f3f9-114">0</span><span class="sxs-lookup"><span data-stu-id="5f3f9-114">0</span></span> | <span data-ttu-id="5f3f9-115">功能已成功完成。</span><span class="sxs-lookup"><span data-stu-id="5f3f9-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="5f3f9-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="5f3f9-116">0x80000008</span></span> | <span data-ttu-id="5f3f9-117">調用方未在公寓中執行。</span><span class="sxs-lookup"><span data-stu-id="5f3f9-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="5f3f9-118">備註</span><span class="sxs-lookup"><span data-stu-id="5f3f9-118">Remarks</span></span>

<span data-ttu-id="5f3f9-119">此函數將調用包起來到[IComThreadingInfo：：獲取當前公寓類型](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype)方法。</span><span class="sxs-lookup"><span data-stu-id="5f3f9-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5f3f9-120">需求</span><span class="sxs-lookup"><span data-stu-id="5f3f9-120">Requirements</span></span>  
 <span data-ttu-id="5f3f9-121">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5f3f9-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f3f9-122">**標題：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5f3f9-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5f3f9-123">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5f3f9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f3f9-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f3f9-124">See also</span></span>

- [<span data-ttu-id="5f3f9-125">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="5f3f9-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

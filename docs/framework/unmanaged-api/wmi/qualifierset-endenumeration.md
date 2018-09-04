---
title: QualifierSet_EndEnumeration 函式 （Unmanaged API 參考）
description: QualifierSet_EndEnumeration 函式會終止列舉型別。
ms.date: 11/06/2017
api_name:
- QualifierSet_EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_EndEnumeration
helpviewer_keywords:
- QualifierSet_EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbf47dbfddac7d48b78c9d52969de1ef03385c15
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524310"
---
# <a name="qualifiersetendenumeration-function"></a><span data-ttu-id="5db55-103">QualifierSet_EndEnumeration 函式</span><span class="sxs-lookup"><span data-stu-id="5db55-103">QualifierSet_EndEnumeration function</span></span>
<span data-ttu-id="5db55-104">結束藉由呼叫開始列舉[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)函式。</span><span class="sxs-lookup"><span data-stu-id="5db55-104">Terminates the enumeration begun with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5db55-105">語法</span><span class="sxs-lookup"><span data-stu-id="5db55-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a><span data-ttu-id="5db55-106">參數</span><span class="sxs-lookup"><span data-stu-id="5db55-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="5db55-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="5db55-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="5db55-108">[in]指標[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)執行個體。</span><span class="sxs-lookup"><span data-stu-id="5db55-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="5db55-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="5db55-109">Return value</span></span>

<span data-ttu-id="5db55-110">此函數所傳回的下列值定義在*WbemCli.h*標頭檔，或者您可以定義它做為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="5db55-110">The following value returned by this function is defined in the *WbemCli.h* header file, or you can define it as a constant in your code:</span></span>

|<span data-ttu-id="5db55-111">常數</span><span class="sxs-lookup"><span data-stu-id="5db55-111">Constant</span></span>  |<span data-ttu-id="5db55-112">值</span><span class="sxs-lookup"><span data-stu-id="5db55-112">Value</span></span>  |<span data-ttu-id="5db55-113">描述</span><span class="sxs-lookup"><span data-stu-id="5db55-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | <span data-ttu-id="5db55-114">0</span><span class="sxs-lookup"><span data-stu-id="5db55-114">0</span></span> | <span data-ttu-id="5db55-115">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="5db55-115">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="5db55-116">備註</span><span class="sxs-lookup"><span data-stu-id="5db55-116">Remarks</span></span>

<span data-ttu-id="5db55-117">此函式會包裝在呼叫[IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration)方法。</span><span class="sxs-lookup"><span data-stu-id="5db55-117">This function wraps a call to the [IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) method.</span></span>

<span data-ttu-id="5db55-118">這個呼叫是建議，但並非必要。</span><span class="sxs-lookup"><span data-stu-id="5db55-118">This call is recommended, but not required.</span></span> <span data-ttu-id="5db55-119">它會立即釋放與列舉相關聯的資源。</span><span class="sxs-lookup"><span data-stu-id="5db55-119">It immediately releases resources associated with the enumeration.</span></span>

## <a name="requirements"></a><span data-ttu-id="5db55-120">需求</span><span class="sxs-lookup"><span data-stu-id="5db55-120">Requirements</span></span>  

<span data-ttu-id="5db55-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5db55-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="5db55-122">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5db55-122">**Header:** WMINet_Utils.idl</span></span>  
  
<span data-ttu-id="5db55-123">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5db55-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5db55-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5db55-124">See also</span></span>  
[<span data-ttu-id="5db55-125">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="5db55-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

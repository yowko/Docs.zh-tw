---
title: QualifierSet_EndEnumeration 函式（非受控 API 參考）
description: QualifierSet_EndEnumeration 函數會終止列舉。
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
ms.openlocfilehash: 2c5a817174ec4c4e4407c19bb1d6d2d852d86dd2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798327"
---
# <a name="qualifierset_endenumeration-function"></a><span data-ttu-id="070da-103">QualifierSet_EndEnumeration 函式</span><span class="sxs-lookup"><span data-stu-id="070da-103">QualifierSet_EndEnumeration function</span></span>
<span data-ttu-id="070da-104">透過呼叫[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)函式，終止開始的列舉。</span><span class="sxs-lookup"><span data-stu-id="070da-104">Terminates the enumeration begun with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="070da-105">語法</span><span class="sxs-lookup"><span data-stu-id="070da-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a><span data-ttu-id="070da-106">參數</span><span class="sxs-lookup"><span data-stu-id="070da-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="070da-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="070da-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="070da-108">在[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="070da-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="070da-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="070da-109">Return value</span></span>

<span data-ttu-id="070da-110">這個函式所傳回的下列值是在*WbemCli*標頭檔中定義的，您也可以在程式碼中將它定義為常數：</span><span class="sxs-lookup"><span data-stu-id="070da-110">The following value returned by this function is defined in the *WbemCli.h* header file, or you can define it as a constant in your code:</span></span>

|<span data-ttu-id="070da-111">常數</span><span class="sxs-lookup"><span data-stu-id="070da-111">Constant</span></span>  |<span data-ttu-id="070da-112">值</span><span class="sxs-lookup"><span data-stu-id="070da-112">Value</span></span>  |<span data-ttu-id="070da-113">描述</span><span class="sxs-lookup"><span data-stu-id="070da-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | <span data-ttu-id="070da-114">0</span><span class="sxs-lookup"><span data-stu-id="070da-114">0</span></span> | <span data-ttu-id="070da-115">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="070da-115">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="070da-116">備註</span><span class="sxs-lookup"><span data-stu-id="070da-116">Remarks</span></span>

<span data-ttu-id="070da-117">此函式會包裝對[IWbemQualifierSet：： EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="070da-117">This function wraps a call to the [IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) method.</span></span>

<span data-ttu-id="070da-118">建議使用此呼叫，但不是必要的。</span><span class="sxs-lookup"><span data-stu-id="070da-118">This call is recommended, but not required.</span></span> <span data-ttu-id="070da-119">它會立即釋放與列舉相關聯的資源。</span><span class="sxs-lookup"><span data-stu-id="070da-119">It immediately releases resources associated with the enumeration.</span></span>

## <a name="requirements"></a><span data-ttu-id="070da-120">需求</span><span class="sxs-lookup"><span data-stu-id="070da-120">Requirements</span></span>  

<span data-ttu-id="070da-121">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="070da-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="070da-122">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="070da-122">**Header:** WMINet_Utils.idl</span></span>  
  
<span data-ttu-id="070da-123">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="070da-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="070da-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="070da-124">See also</span></span>

- [<span data-ttu-id="070da-125">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="070da-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

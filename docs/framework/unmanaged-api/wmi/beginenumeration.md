---
title: BeginEnumeration 函式 （Unmanaged API 參考）
description: BeginEnumeration 函式會查看的列舉值重設為列舉的開頭
ms.date: 11/06/2017
api_name:
- BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginEnumeration
helpviewer_keywords:
- BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4221dbea2b5ad98f889e04eb8a9b6d992b59066e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212293"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="17da3-103">BeginEnumeration 函式</span><span class="sxs-lookup"><span data-stu-id="17da3-103">BeginEnumeration function</span></span>
<span data-ttu-id="17da3-104">將列舉值重設回列舉的開頭。</span><span class="sxs-lookup"><span data-stu-id="17da3-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="17da3-105">語法</span><span class="sxs-lookup"><span data-stu-id="17da3-105">Syntax</span></span>  
  
```  
HRESULT BeginEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="17da3-106">參數</span><span class="sxs-lookup"><span data-stu-id="17da3-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="17da3-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="17da3-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="17da3-108">[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。</span><span class="sxs-lookup"><span data-stu-id="17da3-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`\
<span data-ttu-id="17da3-109">[in]中所述的旗標的位元組合[備註](#remarks)控制包含在列舉中的屬性的區段。</span><span class="sxs-lookup"><span data-stu-id="17da3-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="17da3-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="17da3-110">Return value</span></span>

<span data-ttu-id="17da3-111">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="17da3-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="17da3-112">常數</span><span class="sxs-lookup"><span data-stu-id="17da3-112">Constant</span></span>  |<span data-ttu-id="17da3-113">值</span><span class="sxs-lookup"><span data-stu-id="17da3-113">Value</span></span>  |<span data-ttu-id="17da3-114">描述</span><span class="sxs-lookup"><span data-stu-id="17da3-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="17da3-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="17da3-115">0x80041008</span></span> | <span data-ttu-id="17da3-116">中的旗標的組合`lEnumFlags`無效，或是無效的引數所指定。</span><span class="sxs-lookup"><span data-stu-id="17da3-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="17da3-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="17da3-117">0x8004101d</span></span> | <span data-ttu-id="17da3-118">第二次呼叫`BeginEnumeration`而不需要的介入呼叫進行[ `EndEnumeration` ](endenumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="17da3-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="17da3-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="17da3-119">0x80041006</span></span> | <span data-ttu-id="17da3-120">沒有足夠的記憶體可供開始新的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="17da3-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="17da3-121">0</span><span class="sxs-lookup"><span data-stu-id="17da3-121">0</span></span> | <span data-ttu-id="17da3-122">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="17da3-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="17da3-123">備註</span><span class="sxs-lookup"><span data-stu-id="17da3-123">Remarks</span></span>

<span data-ttu-id="17da3-124">此函式會包裝在呼叫[IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)方法。</span><span class="sxs-lookup"><span data-stu-id="17da3-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="17da3-125">可以做為傳遞的旗標`lEnumFlags`中所定義的引數*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼。</span><span class="sxs-lookup"><span data-stu-id="17da3-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="17da3-126">您可以結合任何其他群組的任何旗標的每個群組中的一個旗標。</span><span class="sxs-lookup"><span data-stu-id="17da3-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="17da3-127">不過，從相同的群組的旗標是互斥的。</span><span class="sxs-lookup"><span data-stu-id="17da3-127">However, flags from the same group are mutually exclusive.</span></span> 

**<span data-ttu-id="17da3-128">群組 1</span><span class="sxs-lookup"><span data-stu-id="17da3-128">Group 1</span></span>**

|<span data-ttu-id="17da3-129">常數</span><span class="sxs-lookup"><span data-stu-id="17da3-129">Constant</span></span>  |<span data-ttu-id="17da3-130">值</span><span class="sxs-lookup"><span data-stu-id="17da3-130">Value</span></span>  |<span data-ttu-id="17da3-131">描述</span><span class="sxs-lookup"><span data-stu-id="17da3-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="17da3-132">0x4</span><span class="sxs-lookup"><span data-stu-id="17da3-132">0x4</span></span> | <span data-ttu-id="17da3-133">包含構成只在索引鍵的屬性。</span><span class="sxs-lookup"><span data-stu-id="17da3-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="17da3-134">0x8</span><span class="sxs-lookup"><span data-stu-id="17da3-134">0x8</span></span> | <span data-ttu-id="17da3-135">包含僅限物件參考的屬性。</span><span class="sxs-lookup"><span data-stu-id="17da3-135">Include properties that are object references only.</span></span> |

**<span data-ttu-id="17da3-136">群組 2</span><span class="sxs-lookup"><span data-stu-id="17da3-136">Group 2</span></span>**

<span data-ttu-id="17da3-137">常數</span><span class="sxs-lookup"><span data-stu-id="17da3-137">Constant</span></span>  |<span data-ttu-id="17da3-138">值</span><span class="sxs-lookup"><span data-stu-id="17da3-138">Value</span></span>  |<span data-ttu-id="17da3-139">描述</span><span class="sxs-lookup"><span data-stu-id="17da3-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="17da3-140">0x30</span><span class="sxs-lookup"><span data-stu-id="17da3-140">0x30</span></span> | <span data-ttu-id="17da3-141">限制僅限系統屬性的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="17da3-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="17da3-142">0x40</span><span class="sxs-lookup"><span data-stu-id="17da3-142">0x40</span></span> | <span data-ttu-id="17da3-143">包含本機和傳播屬性，但排除列舉中的系統屬性。</span><span class="sxs-lookup"><span data-stu-id="17da3-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="17da3-144">針對類別：</span><span class="sxs-lookup"><span data-stu-id="17da3-144">For classes:</span></span>

<span data-ttu-id="17da3-145">常數</span><span class="sxs-lookup"><span data-stu-id="17da3-145">Constant</span></span>  |<span data-ttu-id="17da3-146">值</span><span class="sxs-lookup"><span data-stu-id="17da3-146">Value</span></span>  |<span data-ttu-id="17da3-147">描述</span><span class="sxs-lookup"><span data-stu-id="17da3-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="17da3-148">0x100</span><span class="sxs-lookup"><span data-stu-id="17da3-148">0x100</span></span> | <span data-ttu-id="17da3-149">限制覆寫在類別定義中的屬性的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="17da3-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="17da3-150">0x100</span><span class="sxs-lookup"><span data-stu-id="17da3-150">0x100</span></span> | <span data-ttu-id="17da3-151">限制覆寫目前的類別定義中的屬性並在類別中定義的新屬性的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="17da3-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="17da3-152">0x300</span><span class="sxs-lookup"><span data-stu-id="17da3-152">0x300</span></span> | <span data-ttu-id="17da3-153">遮罩 （而不是一個旗標），若要針對套用`lEnumFlags`值來檢查是否有任一`WBEM_FLAG_CLASS_OVERRIDES_ONLY`或`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES`設定。</span><span class="sxs-lookup"><span data-stu-id="17da3-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="17da3-154">0x10</span><span class="sxs-lookup"><span data-stu-id="17da3-154">0x10</span></span> | <span data-ttu-id="17da3-155">限制屬性所定義或修改在類別本身的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="17da3-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="17da3-156">0x20</span><span class="sxs-lookup"><span data-stu-id="17da3-156">0x20</span></span> | <span data-ttu-id="17da3-157">限制列舉型別繼承自基底類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="17da3-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="17da3-158">執行個體：</span><span class="sxs-lookup"><span data-stu-id="17da3-158">For instances:</span></span>

<span data-ttu-id="17da3-159">常數</span><span class="sxs-lookup"><span data-stu-id="17da3-159">Constant</span></span>  |<span data-ttu-id="17da3-160">值</span><span class="sxs-lookup"><span data-stu-id="17da3-160">Value</span></span>  |<span data-ttu-id="17da3-161">描述</span><span class="sxs-lookup"><span data-stu-id="17da3-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="17da3-162">0x10</span><span class="sxs-lookup"><span data-stu-id="17da3-162">0x10</span></span> | <span data-ttu-id="17da3-163">限制屬性所定義或修改在類別本身的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="17da3-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="17da3-164">0x20</span><span class="sxs-lookup"><span data-stu-id="17da3-164">0x20</span></span> | <span data-ttu-id="17da3-165">限制列舉型別繼承自基底類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="17da3-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="17da3-166">需求</span><span class="sxs-lookup"><span data-stu-id="17da3-166">Requirements</span></span>  
 <span data-ttu-id="17da3-167">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="17da3-167">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17da3-168">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="17da3-168">**Header:** WMINet_Utils.idl</span></span>  
  
 **<span data-ttu-id="17da3-169">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="17da3-169">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="17da3-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17da3-170">See also</span></span>

- [<span data-ttu-id="17da3-171">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="17da3-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
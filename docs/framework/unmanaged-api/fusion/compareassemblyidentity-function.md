---
title: CompareAssemblyIdentity 函式
ms.date: 03/30/2017
api_name:
- CompareAssemblyIdentity
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CompareAssemblyIdentity
helpviewer_keywords:
- CompareAssemblyIdentity function [.NET Framework fusion]
ms.assetid: 8b364ae1-8efa-4744-a7da-81fd093d84d6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a523a58a137f8276df854da956b3ab0b75cbcec9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571622"
---
# <a name="compareassemblyidentity-function"></a><span data-ttu-id="48f76-102">CompareAssemblyIdentity 函式</span><span class="sxs-lookup"><span data-stu-id="48f76-102">CompareAssemblyIdentity Function</span></span>
<span data-ttu-id="48f76-103">比較兩個組件身分識別，以判斷它們是否相等。</span><span class="sxs-lookup"><span data-stu-id="48f76-103">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48f76-104">語法</span><span class="sxs-lookup"><span data-stu-id="48f76-104">Syntax</span></span>  
  
```  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48f76-105">參數</span><span class="sxs-lookup"><span data-stu-id="48f76-105">Parameters</span></span>  
 `pwzAssemblyIdentity1`  
 <span data-ttu-id="48f76-106">[in]文字中比較的第一個組件識別。</span><span class="sxs-lookup"><span data-stu-id="48f76-106">[in] The textual identity of the first assembly in the comparison.</span></span>  
  
 `fUnified1`  
 <span data-ttu-id="48f76-107">[in]布林值的旗標，指出使用者指定的統一`pwzAssemblyIdentity1`。</span><span class="sxs-lookup"><span data-stu-id="48f76-107">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity1`.</span></span>  
  
 `pwzAssemblyIdentity2`  
 <span data-ttu-id="48f76-108">[in]文字中比較的第二個組件識別。</span><span class="sxs-lookup"><span data-stu-id="48f76-108">[in] The textual identity of the second assembly in the comparison.</span></span>  
  
 `fUnified2`  
 <span data-ttu-id="48f76-109">[in]布林值的旗標，指出使用者指定的統一`pwzAssemblyIdentity2`。</span><span class="sxs-lookup"><span data-stu-id="48f76-109">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity2`.</span></span>  
  
 `pfEquivalent`  
 <span data-ttu-id="48f76-110">[out]布林值旗標，指出兩個組件是否相等。</span><span class="sxs-lookup"><span data-stu-id="48f76-110">[out] A Boolean flag that indicates whether the two assemblies are equivalent.</span></span>  
  
 `pResult`  
 <span data-ttu-id="48f76-111">[out][AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)包含比較的詳細的資訊的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="48f76-111">[out] An [AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md) enumeration that contains detailed information about the comparison.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48f76-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="48f76-112">Return Value</span></span>  
 <span data-ttu-id="48f76-113">`pfEquivalent` 傳回布林值，指出兩個組件是否相等。</span><span class="sxs-lookup"><span data-stu-id="48f76-113">`pfEquivalent` returns a Boolean value that indicates whether the two assemblies are equivalent.</span></span> <span data-ttu-id="48f76-114">`pResult` 傳回的其中一個`AssemblyComparisonResult`值，以提供值的詳細的原因`pfEquivalent`。</span><span class="sxs-lookup"><span data-stu-id="48f76-114">`pResult` returns one of the `AssemblyComparisonResult` values, to give a more detailed reason for the value of `pfEquivalent`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48f76-115">備註</span><span class="sxs-lookup"><span data-stu-id="48f76-115">Remarks</span></span>  
 <span data-ttu-id="48f76-116">`CompareAssemblyIdentity` 檢查是否`pwzAssemblyIdentity1`和`pwzAssemblyIdentity2`相等。</span><span class="sxs-lookup"><span data-stu-id="48f76-116">`CompareAssemblyIdentity` checks whether `pwzAssemblyIdentity1` and `pwzAssemblyIdentity2` are equivalent.</span></span> <span data-ttu-id="48f76-117">`pfEquivalent` 設定為`true`下有一或多個下列條件：</span><span class="sxs-lookup"><span data-stu-id="48f76-117">`pfEquivalent` is set to `true` under one or more of the following conditions:</span></span>  
  
-   <span data-ttu-id="48f76-118">兩個組件身分識別是相等的。</span><span class="sxs-lookup"><span data-stu-id="48f76-118">The two assembly identities are equivalent.</span></span> <span data-ttu-id="48f76-119">針對強式名稱組件，對應項會需要的組件名稱、 版本、 公開金鑰語彙基元和文化特性相同。</span><span class="sxs-lookup"><span data-stu-id="48f76-119">For strongly named assemblies, equivalency requires the assembly name, version, public key token, and culture to be identical.</span></span> <span data-ttu-id="48f76-120">針對簡單名稱的組件，相等的條件比對的組件名稱和文化特性。</span><span class="sxs-lookup"><span data-stu-id="48f76-120">For simply named assemblies, equivalency requires a match on the assembly name and culture.</span></span>  
  
-   <span data-ttu-id="48f76-121">這兩個組件身分識別，請參閱.NET Framework 執行的組件。</span><span class="sxs-lookup"><span data-stu-id="48f76-121">Both assembly identities refer to assemblies that run on the .NET Framework.</span></span> <span data-ttu-id="48f76-122">這種狀況傳回`true`即使組件版本號碼不相符。</span><span class="sxs-lookup"><span data-stu-id="48f76-122">This condition returns `true` even if the assembly version numbers do not match.</span></span>  
  
-   <span data-ttu-id="48f76-123">兩個組件不是 managed 組件，但`fUnified1`或是`fUnified2`已設為`true`。</span><span class="sxs-lookup"><span data-stu-id="48f76-123">The two assemblies are not managed assemblies, but `fUnified1` or `fUnified2` was set to `true`.</span></span>  
  
 <span data-ttu-id="48f76-124">`fUnified`旗標表示強式名稱組件的版本號碼的所有版本號碼都都視為相等的強式名稱組件。</span><span class="sxs-lookup"><span data-stu-id="48f76-124">The `fUnified` flag indicates that all version numbers up to the version number of the strongly named assembly are considered equivalent to the strongly named assembly.</span></span> <span data-ttu-id="48f76-125">比方說，如果值`pwzAssemblyIndentity1`是"MyAssembly，版本 version=3.0.0.0，culture = neutral，publicKeyToken =...」，和值`fUnified1`是`true`，這表示，應該是 MyAssembly 從 0.0.0.0 到 3.0.0.0 版開始的所有版本視為對等項目。</span><span class="sxs-lookup"><span data-stu-id="48f76-125">For example, if the value of `pwzAssemblyIndentity1` is "MyAssembly, version=3.0.0.0, culture=neutral, publicKeyToken=....", and the value of `fUnified1` is `true`, this indicates that all versions of MyAssembly from version 0.0.0.0 to 3.0.0.0 should be treated as equivalent.</span></span> <span data-ttu-id="48f76-126">在此情況下，如果`pwzAssemblyIndentity2`相同的組件是指`pwzAssemblyIndentity1`，不同之處在於它有較低的版本號碼，`pfEquivalent`設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="48f76-126">In such a case, if `pwzAssemblyIndentity2` refers to the same assembly as `pwzAssemblyIndentity1`, except that it has a lower version number, `pfEquivalent` is set to `true`.</span></span> <span data-ttu-id="48f76-127">如果`pwzAssemblyIdentity2`更高的版本號碼，是指`pfEquivalent`設為`true`才的值`fUnified2`是`true`。</span><span class="sxs-lookup"><span data-stu-id="48f76-127">If `pwzAssemblyIdentity2` refers to a higher version number, `pfEquivalent` is set to `true` only if the value of `fUnified2` is `true`.</span></span>  
  
 <span data-ttu-id="48f76-128">`pResult`參數包含相等或不相等的兩個組件視為原因的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="48f76-128">The `pResult` parameter includes specific information about why the two assemblies are considered equivalent or not equivalent.</span></span> <span data-ttu-id="48f76-129">如需詳細資訊，請參閱 < [AssemblyComparisonResult 列舉](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="48f76-129">For more information, see [AssemblyComparisonResult Enumeration](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48f76-130">需求</span><span class="sxs-lookup"><span data-stu-id="48f76-130">Requirements</span></span>  
 <span data-ttu-id="48f76-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="48f76-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48f76-132">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="48f76-132">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="48f76-133">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="48f76-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="48f76-134">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48f76-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48f76-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48f76-135">See also</span></span>
- [<span data-ttu-id="48f76-136">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="48f76-136">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [<span data-ttu-id="48f76-137">AssemblyComparisonResult 列舉</span><span class="sxs-lookup"><span data-stu-id="48f76-137">AssemblyComparisonResult Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)

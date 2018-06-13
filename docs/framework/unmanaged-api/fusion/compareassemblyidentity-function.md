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
ms.openlocfilehash: 1b48adcb8e9de49a312af77c8a9b80a07455ebfe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432982"
---
# <a name="compareassemblyidentity-function"></a><span data-ttu-id="a773e-102">CompareAssemblyIdentity 函式</span><span class="sxs-lookup"><span data-stu-id="a773e-102">CompareAssemblyIdentity Function</span></span>
<span data-ttu-id="a773e-103">比較兩個組件識別，以判斷它們是否相等。</span><span class="sxs-lookup"><span data-stu-id="a773e-103">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a773e-104">語法</span><span class="sxs-lookup"><span data-stu-id="a773e-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="a773e-105">參數</span><span class="sxs-lookup"><span data-stu-id="a773e-105">Parameters</span></span>  
 `pwzAssemblyIdentity1`  
 <span data-ttu-id="a773e-106">[in]文字中比較的第一個組件識別。</span><span class="sxs-lookup"><span data-stu-id="a773e-106">[in] The textual identity of the first assembly in the comparison.</span></span>  
  
 `fUnified1`  
 <span data-ttu-id="a773e-107">[in]布林旗標，指出使用者指定的統一`pwzAssemblyIdentity1`。</span><span class="sxs-lookup"><span data-stu-id="a773e-107">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity1`.</span></span>  
  
 `pwzAssemblyIdentity2`  
 <span data-ttu-id="a773e-108">[in]文字中比較的第二個組件識別。</span><span class="sxs-lookup"><span data-stu-id="a773e-108">[in] The textual identity of the second assembly in the comparison.</span></span>  
  
 `fUnified2`  
 <span data-ttu-id="a773e-109">[in]布林旗標，指出使用者指定的統一`pwzAssemblyIdentity2`。</span><span class="sxs-lookup"><span data-stu-id="a773e-109">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity2`.</span></span>  
  
 `pfEquivalent`  
 <span data-ttu-id="a773e-110">[out]布林值旗標，指出兩個組件是否相等。</span><span class="sxs-lookup"><span data-stu-id="a773e-110">[out] A Boolean flag that indicates whether the two assemblies are equivalent.</span></span>  
  
 `pResult`  
 <span data-ttu-id="a773e-111">[out][AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)列舉，其中包含比較的詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="a773e-111">[out] An [AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md) enumeration that contains detailed information about the comparison.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a773e-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="a773e-112">Return Value</span></span>  
 <span data-ttu-id="a773e-113">`pfEquivalent` 傳回布林值，指出兩個組件是否相等。</span><span class="sxs-lookup"><span data-stu-id="a773e-113">`pfEquivalent` returns a Boolean value that indicates whether the two assemblies are equivalent.</span></span> <span data-ttu-id="a773e-114">`pResult` 傳回的其中一個`AssemblyComparisonResult`值，來提供深度的值的詳細的原因`pfEquivalent`。</span><span class="sxs-lookup"><span data-stu-id="a773e-114">`pResult` returns one of the `AssemblyComparisonResult` values, to give a more detailed reason for the value of `pfEquivalent`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a773e-115">備註</span><span class="sxs-lookup"><span data-stu-id="a773e-115">Remarks</span></span>  
 <span data-ttu-id="a773e-116">`CompareAssemblyIdentity` 檢查是否`pwzAssemblyIdentity1`和`pwzAssemblyIdentity2`相等。</span><span class="sxs-lookup"><span data-stu-id="a773e-116">`CompareAssemblyIdentity` checks whether `pwzAssemblyIdentity1` and `pwzAssemblyIdentity2` are equivalent.</span></span> <span data-ttu-id="a773e-117">`pfEquivalent` 設定為`true`在一或多個下列條件：</span><span class="sxs-lookup"><span data-stu-id="a773e-117">`pfEquivalent` is set to `true` under one or more of the following conditions:</span></span>  
  
-   <span data-ttu-id="a773e-118">兩個組件識別是相等的。</span><span class="sxs-lookup"><span data-stu-id="a773e-118">The two assembly identities are equivalent.</span></span> <span data-ttu-id="a773e-119">強式名稱組件，相等的條件組件名稱、 版本、 公開金鑰語彙基元和文化特性相同。</span><span class="sxs-lookup"><span data-stu-id="a773e-119">For strongly named assemblies, equivalency requires the assembly name, version, public key token, and culture to be identical.</span></span> <span data-ttu-id="a773e-120">簡單名稱的組件為相等的條件相符的組件名稱和文化特性。</span><span class="sxs-lookup"><span data-stu-id="a773e-120">For simply named assemblies, equivalency requires a match on the assembly name and culture.</span></span>  
  
-   <span data-ttu-id="a773e-121">這兩個組件識別是指.NET Framework 執行的組件。</span><span class="sxs-lookup"><span data-stu-id="a773e-121">Both assembly identities refer to assemblies that run on the .NET Framework.</span></span> <span data-ttu-id="a773e-122">此條件傳回`true`即使組件版本號碼不相符。</span><span class="sxs-lookup"><span data-stu-id="a773e-122">This condition returns `true` even if the assembly version numbers do not match.</span></span>  
  
-   <span data-ttu-id="a773e-123">兩個組件不是 managed 組件，但`fUnified1`或`fUnified2`設`true`。</span><span class="sxs-lookup"><span data-stu-id="a773e-123">The two assemblies are not managed assemblies, but `fUnified1` or `fUnified2` was set to `true`.</span></span>  
  
 <span data-ttu-id="a773e-124">`fUnified`旗標指出強式名稱組件的版本號碼的所有版本號碼會都視為等於強式名稱組件。</span><span class="sxs-lookup"><span data-stu-id="a773e-124">The `fUnified` flag indicates that all version numbers up to the version number of the strongly named assembly are considered equivalent to the strongly named assembly.</span></span> <span data-ttu-id="a773e-125">例如，如果的值`pwzAssemblyIndentity1`是"MyAssembly，版本 = 3.0.0.0，culture = neutral，publicKeyToken =..."，和值`fUnified1`是`true`，這表示應該從版本 0.0.0.0 3.0.0.0 開始 MyAssembly 的所有版本視為對等項目。</span><span class="sxs-lookup"><span data-stu-id="a773e-125">For example, if the value of `pwzAssemblyIndentity1` is "MyAssembly, version=3.0.0.0, culture=neutral, publicKeyToken=....", and the value of `fUnified1` is `true`, this indicates that all versions of MyAssembly from version 0.0.0.0 to 3.0.0.0 should be treated as equivalent.</span></span> <span data-ttu-id="a773e-126">在這種情況下，如果`pwzAssemblyIndentity2`指的是相同的組件`pwzAssemblyIndentity1`，不同之處在於它有較低的版本號碼，`pfEquivalent`設`true`。</span><span class="sxs-lookup"><span data-stu-id="a773e-126">In such a case, if `pwzAssemblyIndentity2` refers to the same assembly as `pwzAssemblyIndentity1`, except that it has a lower version number, `pfEquivalent` is set to `true`.</span></span> <span data-ttu-id="a773e-127">如果`pwzAssemblyIdentity2`較高的版本號碼，是指`pfEquivalent`設`true`才值`fUnified2`是`true`。</span><span class="sxs-lookup"><span data-stu-id="a773e-127">If `pwzAssemblyIdentity2` refers to a higher version number, `pfEquivalent` is set to `true` only if the value of `fUnified2` is `true`.</span></span>  
  
 <span data-ttu-id="a773e-128">`pResult`參數包含兩個組件為何被視為相等或不相等的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="a773e-128">The `pResult` parameter includes specific information about why the two assemblies are considered equivalent or not equivalent.</span></span> <span data-ttu-id="a773e-129">如需詳細資訊，請參閱[AssemblyComparisonResult 列舉](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="a773e-129">For more information, see [AssemblyComparisonResult Enumeration](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a773e-130">需求</span><span class="sxs-lookup"><span data-stu-id="a773e-130">Requirements</span></span>  
 <span data-ttu-id="a773e-131">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a773e-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a773e-132">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="a773e-132">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a773e-133">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a773e-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a773e-134">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a773e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a773e-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a773e-135">See Also</span></span>  
 [<span data-ttu-id="a773e-136">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="a773e-136">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [<span data-ttu-id="a773e-137">AssemblyComparisonResult 列舉</span><span class="sxs-lookup"><span data-stu-id="a773e-137">AssemblyComparisonResult Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)

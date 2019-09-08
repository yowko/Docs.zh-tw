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
ms.openlocfilehash: b52d3af38bd09ce5864c25d27e148dbd7f4639b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795453"
---
# <a name="compareassemblyidentity-function"></a><span data-ttu-id="6efae-102">CompareAssemblyIdentity 函式</span><span class="sxs-lookup"><span data-stu-id="6efae-102">CompareAssemblyIdentity Function</span></span>
<span data-ttu-id="6efae-103">比較兩個元件識別，以判斷它們是否相等。</span><span class="sxs-lookup"><span data-stu-id="6efae-103">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6efae-104">語法</span><span class="sxs-lookup"><span data-stu-id="6efae-104">Syntax</span></span>  
  
```cpp  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="6efae-105">參數</span><span class="sxs-lookup"><span data-stu-id="6efae-105">Parameters</span></span>  
 `pwzAssemblyIdentity1`  
 <span data-ttu-id="6efae-106">在比較中第一個元件的文字識別。</span><span class="sxs-lookup"><span data-stu-id="6efae-106">[in] The textual identity of the first assembly in the comparison.</span></span>  
  
 `fUnified1`  
 <span data-ttu-id="6efae-107">在布林值旗標，表示的使用者指定的`pwzAssemblyIdentity1`統一。</span><span class="sxs-lookup"><span data-stu-id="6efae-107">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity1`.</span></span>  
  
 `pwzAssemblyIdentity2`  
 <span data-ttu-id="6efae-108">在比較中第二個元件的文字識別。</span><span class="sxs-lookup"><span data-stu-id="6efae-108">[in] The textual identity of the second assembly in the comparison.</span></span>  
  
 `fUnified2`  
 <span data-ttu-id="6efae-109">在布林值旗標，表示的使用者指定的`pwzAssemblyIdentity2`統一。</span><span class="sxs-lookup"><span data-stu-id="6efae-109">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity2`.</span></span>  
  
 `pfEquivalent`  
 <span data-ttu-id="6efae-110">脫銷指出兩個元件是否相等的布林值旗標。</span><span class="sxs-lookup"><span data-stu-id="6efae-110">[out] A Boolean flag that indicates whether the two assemblies are equivalent.</span></span>  
  
 `pResult`  
 <span data-ttu-id="6efae-111">脫銷包含比較之詳細資訊的[AssemblyComparisonResult](assemblycomparisonresult-enumeration.md)列舉。</span><span class="sxs-lookup"><span data-stu-id="6efae-111">[out] An [AssemblyComparisonResult](assemblycomparisonresult-enumeration.md) enumeration that contains detailed information about the comparison.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6efae-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="6efae-112">Return Value</span></span>  
 <span data-ttu-id="6efae-113">`pfEquivalent`傳回布林值，指出兩個元件是否相等。</span><span class="sxs-lookup"><span data-stu-id="6efae-113">`pfEquivalent` returns a Boolean value that indicates whether the two assemblies are equivalent.</span></span> <span data-ttu-id="6efae-114">`pResult`傳回其中一個`AssemblyComparisonResult`值，以提供更詳細的`pfEquivalent`值原因。</span><span class="sxs-lookup"><span data-stu-id="6efae-114">`pResult` returns one of the `AssemblyComparisonResult` values, to give a more detailed reason for the value of `pfEquivalent`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6efae-115">備註</span><span class="sxs-lookup"><span data-stu-id="6efae-115">Remarks</span></span>  
 <span data-ttu-id="6efae-116">`CompareAssemblyIdentity``pwzAssemblyIdentity1`檢查和`pwzAssemblyIdentity2`是否相等。</span><span class="sxs-lookup"><span data-stu-id="6efae-116">`CompareAssemblyIdentity` checks whether `pwzAssemblyIdentity1` and `pwzAssemblyIdentity2` are equivalent.</span></span> <span data-ttu-id="6efae-117">`pfEquivalent`在下列一個`true`或多個情況下，會設為：</span><span class="sxs-lookup"><span data-stu-id="6efae-117">`pfEquivalent` is set to `true` under one or more of the following conditions:</span></span>  
  
- <span data-ttu-id="6efae-118">這兩個元件身分識別是相等的。</span><span class="sxs-lookup"><span data-stu-id="6efae-118">The two assembly identities are equivalent.</span></span> <span data-ttu-id="6efae-119">若為強式名稱元件，則對等需要元件名稱、版本、公開金鑰標記和文化特性都相同。</span><span class="sxs-lookup"><span data-stu-id="6efae-119">For strongly named assemblies, equivalency requires the assembly name, version, public key token, and culture to be identical.</span></span> <span data-ttu-id="6efae-120">對於簡單命名的元件而言，對等的必須符合元件名稱和文化特性。</span><span class="sxs-lookup"><span data-stu-id="6efae-120">For simply named assemblies, equivalency requires a match on the assembly name and culture.</span></span>  
  
- <span data-ttu-id="6efae-121">這兩個元件識別都會參考在 .NET Framework 上執行的元件。</span><span class="sxs-lookup"><span data-stu-id="6efae-121">Both assembly identities refer to assemblies that run on the .NET Framework.</span></span> <span data-ttu-id="6efae-122">`true`即使元件版本號碼不相符，這個條件也會傳回。</span><span class="sxs-lookup"><span data-stu-id="6efae-122">This condition returns `true` even if the assembly version numbers do not match.</span></span>  
  
- <span data-ttu-id="6efae-123">這兩個元件不是 managed 元件， `fUnified1`而`fUnified2`是或已`true`設定為。</span><span class="sxs-lookup"><span data-stu-id="6efae-123">The two assemblies are not managed assemblies, but `fUnified1` or `fUnified2` was set to `true`.</span></span>  
  
 <span data-ttu-id="6efae-124">`fUnified`旗標指出，最高至強式名稱元件版本號碼的所有版本號碼，都視為與強式名稱元件相等。</span><span class="sxs-lookup"><span data-stu-id="6efae-124">The `fUnified` flag indicates that all version numbers up to the version number of the strongly named assembly are considered equivalent to the strongly named assembly.</span></span> <span data-ttu-id="6efae-125">例如，如果的值`pwzAssemblyIndentity1`為 "MyAssembly，version = 3.0.0.0，culture = 中性，publicKeyToken = ..."，且的`fUnified1`值為`true`，則表示從0.0.0.0 到3.0.0.0 的所有 MyAssembly 版本都應該是視為對等。</span><span class="sxs-lookup"><span data-stu-id="6efae-125">For example, if the value of `pwzAssemblyIndentity1` is "MyAssembly, version=3.0.0.0, culture=neutral, publicKeyToken=....", and the value of `fUnified1` is `true`, this indicates that all versions of MyAssembly from version 0.0.0.0 to 3.0.0.0 should be treated as equivalent.</span></span> <span data-ttu-id="6efae-126">在這種情況下， `pwzAssemblyIndentity2`如果參考與相同的`pwzAssemblyIndentity1`元件，但其版本號碼較低， `pfEquivalent`則會設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="6efae-126">In such a case, if `pwzAssemblyIndentity2` refers to the same assembly as `pwzAssemblyIndentity1`, except that it has a lower version number, `pfEquivalent` is set to `true`.</span></span> <span data-ttu-id="6efae-127">如果`pwzAssemblyIdentity2`參考較高的版本號碼， `pfEquivalent`只有在的`true`值`fUnified2`為時`true`，才會設定為。</span><span class="sxs-lookup"><span data-stu-id="6efae-127">If `pwzAssemblyIdentity2` refers to a higher version number, `pfEquivalent` is set to `true` only if the value of `fUnified2` is `true`.</span></span>  
  
 <span data-ttu-id="6efae-128">`pResult`參數包含為何將兩個元件視為相等或不相等的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="6efae-128">The `pResult` parameter includes specific information about why the two assemblies are considered equivalent or not equivalent.</span></span> <span data-ttu-id="6efae-129">如需詳細資訊，請參閱[AssemblyComparisonResult 列舉](assemblycomparisonresult-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="6efae-129">For more information, see [AssemblyComparisonResult Enumeration](assemblycomparisonresult-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6efae-130">需求</span><span class="sxs-lookup"><span data-stu-id="6efae-130">Requirements</span></span>  
 <span data-ttu-id="6efae-131">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6efae-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6efae-132">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="6efae-132">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="6efae-133">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6efae-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6efae-134">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6efae-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6efae-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6efae-135">See also</span></span>

- [<span data-ttu-id="6efae-136">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="6efae-136">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="6efae-137">AssemblyComparisonResult 列舉</span><span class="sxs-lookup"><span data-stu-id="6efae-137">AssemblyComparisonResult Enumeration</span></span>](assemblycomparisonresult-enumeration.md)

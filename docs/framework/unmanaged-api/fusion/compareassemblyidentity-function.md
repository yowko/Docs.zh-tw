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
ms.openlocfilehash: f6711902fb9d5c5c16084057b731746843cf0230
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108914"
---
# <a name="compareassemblyidentity-function"></a><span data-ttu-id="091c6-102">CompareAssemblyIdentity 函式</span><span class="sxs-lookup"><span data-stu-id="091c6-102">CompareAssemblyIdentity Function</span></span>
<span data-ttu-id="091c6-103">比較兩個元件識別，以判斷它們是否相等。</span><span class="sxs-lookup"><span data-stu-id="091c6-103">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="091c6-104">語法</span><span class="sxs-lookup"><span data-stu-id="091c6-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="091c6-105">參數</span><span class="sxs-lookup"><span data-stu-id="091c6-105">Parameters</span></span>  
 `pwzAssemblyIdentity1`  
 <span data-ttu-id="091c6-106">在比較中第一個元件的文字識別。</span><span class="sxs-lookup"><span data-stu-id="091c6-106">[in] The textual identity of the first assembly in the comparison.</span></span>  
  
 `fUnified1`  
 <span data-ttu-id="091c6-107">在布林值旗標，表示 `pwzAssemblyIdentity1`的使用者指定的統一。</span><span class="sxs-lookup"><span data-stu-id="091c6-107">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity1`.</span></span>  
  
 `pwzAssemblyIdentity2`  
 <span data-ttu-id="091c6-108">在比較中第二個元件的文字識別。</span><span class="sxs-lookup"><span data-stu-id="091c6-108">[in] The textual identity of the second assembly in the comparison.</span></span>  
  
 `fUnified2`  
 <span data-ttu-id="091c6-109">在布林值旗標，表示 `pwzAssemblyIdentity2`的使用者指定的統一。</span><span class="sxs-lookup"><span data-stu-id="091c6-109">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity2`.</span></span>  
  
 `pfEquivalent`  
 <span data-ttu-id="091c6-110">脫銷指出兩個元件是否相等的布林值旗標。</span><span class="sxs-lookup"><span data-stu-id="091c6-110">[out] A Boolean flag that indicates whether the two assemblies are equivalent.</span></span>  
  
 `pResult`  
 <span data-ttu-id="091c6-111">脫銷包含比較之詳細資訊的[AssemblyComparisonResult](assemblycomparisonresult-enumeration.md)列舉。</span><span class="sxs-lookup"><span data-stu-id="091c6-111">[out] An [AssemblyComparisonResult](assemblycomparisonresult-enumeration.md) enumeration that contains detailed information about the comparison.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="091c6-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="091c6-112">Return Value</span></span>  
 <span data-ttu-id="091c6-113">`pfEquivalent` 會傳回布林值，指出兩個元件是否相等。</span><span class="sxs-lookup"><span data-stu-id="091c6-113">`pfEquivalent` returns a Boolean value that indicates whether the two assemblies are equivalent.</span></span> <span data-ttu-id="091c6-114">`pResult` 會傳回其中一個 `AssemblyComparisonResult` 值，以提供更詳細的 `pfEquivalent`值原因。</span><span class="sxs-lookup"><span data-stu-id="091c6-114">`pResult` returns one of the `AssemblyComparisonResult` values, to give a more detailed reason for the value of `pfEquivalent`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="091c6-115">備註</span><span class="sxs-lookup"><span data-stu-id="091c6-115">Remarks</span></span>  
 <span data-ttu-id="091c6-116">`CompareAssemblyIdentity` 檢查 `pwzAssemblyIdentity1` 和 `pwzAssemblyIdentity2` 是否相等。</span><span class="sxs-lookup"><span data-stu-id="091c6-116">`CompareAssemblyIdentity` checks whether `pwzAssemblyIdentity1` and `pwzAssemblyIdentity2` are equivalent.</span></span> <span data-ttu-id="091c6-117">在下列一個或多個情況下，`pfEquivalent` 設定為 `true`：</span><span class="sxs-lookup"><span data-stu-id="091c6-117">`pfEquivalent` is set to `true` under one or more of the following conditions:</span></span>  
  
- <span data-ttu-id="091c6-118">這兩個元件身分識別是相等的。</span><span class="sxs-lookup"><span data-stu-id="091c6-118">The two assembly identities are equivalent.</span></span> <span data-ttu-id="091c6-119">若為強式名稱元件，則對等需要元件名稱、版本、公開金鑰標記和文化特性都相同。</span><span class="sxs-lookup"><span data-stu-id="091c6-119">For strongly named assemblies, equivalency requires the assembly name, version, public key token, and culture to be identical.</span></span> <span data-ttu-id="091c6-120">對於簡單命名的元件而言，對等的必須符合元件名稱和文化特性。</span><span class="sxs-lookup"><span data-stu-id="091c6-120">For simply named assemblies, equivalency requires a match on the assembly name and culture.</span></span>  
  
- <span data-ttu-id="091c6-121">這兩個元件識別都會參考在 .NET Framework 上執行的元件。</span><span class="sxs-lookup"><span data-stu-id="091c6-121">Both assembly identities refer to assemblies that run on the .NET Framework.</span></span> <span data-ttu-id="091c6-122">即使元件版本號碼不相符，這個條件也會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="091c6-122">This condition returns `true` even if the assembly version numbers do not match.</span></span>  
  
- <span data-ttu-id="091c6-123">這兩個元件不是 managed 元件，但是 `fUnified1` 或 `fUnified2` 設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="091c6-123">The two assemblies are not managed assemblies, but `fUnified1` or `fUnified2` was set to `true`.</span></span>  
  
 <span data-ttu-id="091c6-124">`fUnified` 旗標表示，最高至強式名稱元件之版本號碼的所有版本號碼，都會被視為與強式名稱元件相等。</span><span class="sxs-lookup"><span data-stu-id="091c6-124">The `fUnified` flag indicates that all version numbers up to the version number of the strongly named assembly are considered equivalent to the strongly named assembly.</span></span> <span data-ttu-id="091c6-125">例如，如果 `pwzAssemblyIndentity1` 的值為 "MyAssembly，version = 3.0.0.0，culture = 中性，publicKeyToken = ..."，且 `fUnified1` 的值為 `true`，這表示從0.0.0.0 到3.0.0.0 的所有 MyAssembly 版本都應該視為價額.</span><span class="sxs-lookup"><span data-stu-id="091c6-125">For example, if the value of `pwzAssemblyIndentity1` is "MyAssembly, version=3.0.0.0, culture=neutral, publicKeyToken=....", and the value of `fUnified1` is `true`, this indicates that all versions of MyAssembly from version 0.0.0.0 to 3.0.0.0 should be treated as equivalent.</span></span> <span data-ttu-id="091c6-126">在這種情況下，如果 `pwzAssemblyIndentity2` 指的是與 `pwzAssemblyIndentity1`相同的元件，但其版本號碼較低，`pfEquivalent` 會設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="091c6-126">In such a case, if `pwzAssemblyIndentity2` refers to the same assembly as `pwzAssemblyIndentity1`, except that it has a lower version number, `pfEquivalent` is set to `true`.</span></span> <span data-ttu-id="091c6-127">如果 `pwzAssemblyIdentity2` 指的是較高的版本號碼，只有在 `fUnified2` 的值是 `true`時，才會將 `pfEquivalent` 設定為 [`true`]。</span><span class="sxs-lookup"><span data-stu-id="091c6-127">If `pwzAssemblyIdentity2` refers to a higher version number, `pfEquivalent` is set to `true` only if the value of `fUnified2` is `true`.</span></span>  
  
 <span data-ttu-id="091c6-128">`pResult` 參數包含為何將兩個元件視為相等或不相等的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="091c6-128">The `pResult` parameter includes specific information about why the two assemblies are considered equivalent or not equivalent.</span></span> <span data-ttu-id="091c6-129">如需詳細資訊，請參閱[AssemblyComparisonResult 列舉](assemblycomparisonresult-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="091c6-129">For more information, see [AssemblyComparisonResult Enumeration](assemblycomparisonresult-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="091c6-130">需求</span><span class="sxs-lookup"><span data-stu-id="091c6-130">Requirements</span></span>  
 <span data-ttu-id="091c6-131">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="091c6-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="091c6-132">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="091c6-132">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="091c6-133">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="091c6-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="091c6-134">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="091c6-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="091c6-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="091c6-135">See also</span></span>

- [<span data-ttu-id="091c6-136">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="091c6-136">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="091c6-137">AssemblyComparisonResult 列舉</span><span class="sxs-lookup"><span data-stu-id="091c6-137">AssemblyComparisonResult Enumeration</span></span>](assemblycomparisonresult-enumeration.md)

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
ms.openlocfilehash: da32ce6a40378a6f88cf71bd7707be2079d71068
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717587"
---
# <a name="compareassemblyidentity-function"></a><span data-ttu-id="d92e9-102">CompareAssemblyIdentity 函式</span><span class="sxs-lookup"><span data-stu-id="d92e9-102">CompareAssemblyIdentity Function</span></span>

<span data-ttu-id="d92e9-103">比較兩個元件身分識別，以判斷它們是否相等。</span><span class="sxs-lookup"><span data-stu-id="d92e9-103">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d92e9-104">語法</span><span class="sxs-lookup"><span data-stu-id="d92e9-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d92e9-105">參數</span><span class="sxs-lookup"><span data-stu-id="d92e9-105">Parameters</span></span>  

 `pwzAssemblyIdentity1`  
 <span data-ttu-id="d92e9-106">在比較中第一個元件的文字識別。</span><span class="sxs-lookup"><span data-stu-id="d92e9-106">[in] The textual identity of the first assembly in the comparison.</span></span>  
  
 `fUnified1`  
 <span data-ttu-id="d92e9-107">在指出使用者指定之統一的布林值旗標 `pwzAssemblyIdentity1` 。</span><span class="sxs-lookup"><span data-stu-id="d92e9-107">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity1`.</span></span>  
  
 `pwzAssemblyIdentity2`  
 <span data-ttu-id="d92e9-108">在比較中第二個元件的文字識別。</span><span class="sxs-lookup"><span data-stu-id="d92e9-108">[in] The textual identity of the second assembly in the comparison.</span></span>  
  
 `fUnified2`  
 <span data-ttu-id="d92e9-109">在指出使用者指定之統一的布林值旗標 `pwzAssemblyIdentity2` 。</span><span class="sxs-lookup"><span data-stu-id="d92e9-109">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity2`.</span></span>  
  
 `pfEquivalent`  
 <span data-ttu-id="d92e9-110">擴展指出兩個元件是否相等的布林旗標。</span><span class="sxs-lookup"><span data-stu-id="d92e9-110">[out] A Boolean flag that indicates whether the two assemblies are equivalent.</span></span>  
  
 `pResult`  
 <span data-ttu-id="d92e9-111">擴展包含比較之詳細資訊的 [AssemblyComparisonResult](assemblycomparisonresult-enumeration.md) 列舉。</span><span class="sxs-lookup"><span data-stu-id="d92e9-111">[out] An [AssemblyComparisonResult](assemblycomparisonresult-enumeration.md) enumeration that contains detailed information about the comparison.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d92e9-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="d92e9-112">Return Value</span></span>  

 <span data-ttu-id="d92e9-113">`pfEquivalent` 傳回布林值，指出兩個元件是否相等。</span><span class="sxs-lookup"><span data-stu-id="d92e9-113">`pfEquivalent` returns a Boolean value that indicates whether the two assemblies are equivalent.</span></span> <span data-ttu-id="d92e9-114">`pResult` 傳回其中一個 `AssemblyComparisonResult` 值，以提供更詳細的值原因 `pfEquivalent` 。</span><span class="sxs-lookup"><span data-stu-id="d92e9-114">`pResult` returns one of the `AssemblyComparisonResult` values, to give a more detailed reason for the value of `pfEquivalent`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d92e9-115">備註</span><span class="sxs-lookup"><span data-stu-id="d92e9-115">Remarks</span></span>  

 <span data-ttu-id="d92e9-116">`CompareAssemblyIdentity` 檢查 `pwzAssemblyIdentity1` 和是否 `pwzAssemblyIdentity2` 相等。</span><span class="sxs-lookup"><span data-stu-id="d92e9-116">`CompareAssemblyIdentity` checks whether `pwzAssemblyIdentity1` and `pwzAssemblyIdentity2` are equivalent.</span></span> <span data-ttu-id="d92e9-117">`pfEquivalent``true`在下列一或多個情況下，會設定為：</span><span class="sxs-lookup"><span data-stu-id="d92e9-117">`pfEquivalent` is set to `true` under one or more of the following conditions:</span></span>  
  
- <span data-ttu-id="d92e9-118">這兩個元件身分識別是相等的。</span><span class="sxs-lookup"><span data-stu-id="d92e9-118">The two assembly identities are equivalent.</span></span> <span data-ttu-id="d92e9-119">針對強式名稱元件，相等要求元件名稱、版本、公開金鑰 token 和文化特性必須相同。</span><span class="sxs-lookup"><span data-stu-id="d92e9-119">For strongly named assemblies, equivalency requires the assembly name, version, public key token, and culture to be identical.</span></span> <span data-ttu-id="d92e9-120">針對簡單命名的元件，等的需要符合元件名稱和文化特性。</span><span class="sxs-lookup"><span data-stu-id="d92e9-120">For simply named assemblies, equivalency requires a match on the assembly name and culture.</span></span>  
  
- <span data-ttu-id="d92e9-121">這兩個元件身分識別都會參考在 .NET Framework 上執行的元件。</span><span class="sxs-lookup"><span data-stu-id="d92e9-121">Both assembly identities refer to assemblies that run on the .NET Framework.</span></span> <span data-ttu-id="d92e9-122">`true`即使元件版本號碼不相符，也會傳回這個條件。</span><span class="sxs-lookup"><span data-stu-id="d92e9-122">This condition returns `true` even if the assembly version numbers do not match.</span></span>  
  
- <span data-ttu-id="d92e9-123">這兩個元件並非 managed 元件，而 `fUnified1` 是 `fUnified2` 設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="d92e9-123">The two assemblies are not managed assemblies, but `fUnified1` or `fUnified2` was set to `true`.</span></span>  
  
 <span data-ttu-id="d92e9-124">`fUnified`旗標會指出強式名稱元件的版本號碼最多會視為相當於強式名稱元件。</span><span class="sxs-lookup"><span data-stu-id="d92e9-124">The `fUnified` flag indicates that all version numbers up to the version number of the strongly named assembly are considered equivalent to the strongly named assembly.</span></span> <span data-ttu-id="d92e9-125">例如，如果的值 `pwzAssemblyIndentity1` 為 "MyAssembly，version = 3.0.0.0，culture = 中性，publicKeyToken = ..."，而的值 `fUnified1` 為 `true` ，則這表示從0.0.0.0 到3.0.0.0 的所有 MyAssembly 版本都應視為相等。</span><span class="sxs-lookup"><span data-stu-id="d92e9-125">For example, if the value of `pwzAssemblyIndentity1` is "MyAssembly, version=3.0.0.0, culture=neutral, publicKeyToken=....", and the value of `fUnified1` is `true`, this indicates that all versions of MyAssembly from version 0.0.0.0 to 3.0.0.0 should be treated as equivalent.</span></span> <span data-ttu-id="d92e9-126">在這種情況下，如果 `pwzAssemblyIndentity2` 參考相同的元件 `pwzAssemblyIndentity1` ，但它的版本號碼較低， `pfEquivalent` 則會設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="d92e9-126">In such a case, if `pwzAssemblyIndentity2` refers to the same assembly as `pwzAssemblyIndentity1`, except that it has a lower version number, `pfEquivalent` is set to `true`.</span></span> <span data-ttu-id="d92e9-127">如果 `pwzAssemblyIdentity2` 參考較高的版本號碼， `pfEquivalent` 則 `true` 只有當的值為時，才會設定為 `fUnified2` `true` 。</span><span class="sxs-lookup"><span data-stu-id="d92e9-127">If `pwzAssemblyIdentity2` refers to a higher version number, `pfEquivalent` is set to `true` only if the value of `fUnified2` is `true`.</span></span>  
  
 <span data-ttu-id="d92e9-128">`pResult`參數包含為何將兩個元件視為相等或不相等的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="d92e9-128">The `pResult` parameter includes specific information about why the two assemblies are considered equivalent or not equivalent.</span></span> <span data-ttu-id="d92e9-129">如需詳細資訊，請參閱 [AssemblyComparisonResult 列舉](assemblycomparisonresult-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="d92e9-129">For more information, see [AssemblyComparisonResult Enumeration](assemblycomparisonresult-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d92e9-130">需求</span><span class="sxs-lookup"><span data-stu-id="d92e9-130">Requirements</span></span>  

 <span data-ttu-id="d92e9-131">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d92e9-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d92e9-132">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="d92e9-132">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d92e9-133">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="d92e9-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d92e9-134">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d92e9-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d92e9-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d92e9-135">See also</span></span>

- [<span data-ttu-id="d92e9-136">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="d92e9-136">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="d92e9-137">AssemblyComparisonResult 列舉</span><span class="sxs-lookup"><span data-stu-id="d92e9-137">AssemblyComparisonResult Enumeration</span></span>](assemblycomparisonresult-enumeration.md)

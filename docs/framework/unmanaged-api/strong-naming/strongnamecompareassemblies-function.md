---
title: StrongNameCompareAssemblies 函式
ms.date: 03/30/2017
api_name:
- StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameCompareAssemblies
helpviewer_keywords:
- StrongNameCompareAssemblies function [.NET Framework strong naming]
ms.assetid: 763f2375-efc6-4219-8806-a3b0567ef72b
topic_type:
- apiref
ms.openlocfilehash: e7292635ea0344f1c77c8d44908a9a811e464ff9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732303"
---
# <a name="strongnamecompareassemblies-function"></a><span data-ttu-id="15aa5-102">StrongNameCompareAssemblies 函式</span><span class="sxs-lookup"><span data-stu-id="15aa5-102">StrongNameCompareAssemblies Function</span></span>

<span data-ttu-id="15aa5-103">判斷兩個組件是否只有強制名稱簽章不同。</span><span class="sxs-lookup"><span data-stu-id="15aa5-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
 <span data-ttu-id="15aa5-104">此函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="15aa5-104">This function has been deprecated.</span></span> <span data-ttu-id="15aa5-105">請改用 [ICLRStrongName：： StrongNameCompareAssemblies](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="15aa5-105">Use the [ICLRStrongName::StrongNameCompareAssemblies](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15aa5-106">語法</span><span class="sxs-lookup"><span data-stu-id="15aa5-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15aa5-107">參數</span><span class="sxs-lookup"><span data-stu-id="15aa5-107">Parameters</span></span>  

 `wszAssembly1`  
 <span data-ttu-id="15aa5-108">在第一個元件的路徑。</span><span class="sxs-lookup"><span data-stu-id="15aa5-108">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="15aa5-109">在第二個元件的路徑。</span><span class="sxs-lookup"><span data-stu-id="15aa5-109">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="15aa5-110">擴展下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="15aa5-110">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="15aa5-111">`SN_CMP_DIFFERENT` (0) -指定元件包含不同的資料。</span><span class="sxs-lookup"><span data-stu-id="15aa5-111">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="15aa5-112">`SN_CMP_IDENTICAL` (1) -指定元件完全相同，包括其簽章和總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="15aa5-112">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="15aa5-113">`SN_CMP_SIGONLY` (2) -指定元件只有簽章和總和檢查碼不同。</span><span class="sxs-lookup"><span data-stu-id="15aa5-113">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="15aa5-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="15aa5-114">Return Value</span></span>  

 <span data-ttu-id="15aa5-115">`true` 成功完成時;否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="15aa5-115">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15aa5-116">需求</span><span class="sxs-lookup"><span data-stu-id="15aa5-116">Requirements</span></span>  

 <span data-ttu-id="15aa5-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="15aa5-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15aa5-118">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="15aa5-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="15aa5-119">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="15aa5-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="15aa5-120">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15aa5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15aa5-121">備註</span><span class="sxs-lookup"><span data-stu-id="15aa5-121">Remarks</span></span>  

 <span data-ttu-id="15aa5-122">元件的強式名稱簽章是由元件的文字名稱、版本、文化特性和公開金鑰 token 所組成。</span><span class="sxs-lookup"><span data-stu-id="15aa5-122">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
 <span data-ttu-id="15aa5-123">如果函式 `StrongNameCompareAssemblies` 未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式來取出最後產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="15aa5-123">If the `StrongNameCompareAssemblies` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15aa5-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15aa5-124">See also</span></span>

- [<span data-ttu-id="15aa5-125">StrongNameCompareAssemblies 方法</span><span class="sxs-lookup"><span data-stu-id="15aa5-125">StrongNameCompareAssemblies Method</span></span>](../hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [<span data-ttu-id="15aa5-126">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="15aa5-126">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)

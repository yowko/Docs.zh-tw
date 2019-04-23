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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a49252d00f75b4d0b6325aeae0aab22f8ada5e4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191376"
---
# <a name="strongnamecompareassemblies-function"></a><span data-ttu-id="11e8e-102">StrongNameCompareAssemblies 函式</span><span class="sxs-lookup"><span data-stu-id="11e8e-102">StrongNameCompareAssemblies Function</span></span>
<span data-ttu-id="11e8e-103">判斷兩個組件是否只有強制名稱簽章不同。</span><span class="sxs-lookup"><span data-stu-id="11e8e-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
 <span data-ttu-id="11e8e-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="11e8e-104">This function has been deprecated.</span></span> <span data-ttu-id="11e8e-105">使用[iclrstrongname:: Strongnamecompareassemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="11e8e-105">Use the [ICLRStrongName::StrongNameCompareAssemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11e8e-106">語法</span><span class="sxs-lookup"><span data-stu-id="11e8e-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11e8e-107">參數</span><span class="sxs-lookup"><span data-stu-id="11e8e-107">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="11e8e-108">[in]第一個組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="11e8e-108">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="11e8e-109">[in]第二個組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="11e8e-109">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="11e8e-110">[out]下列值之一：</span><span class="sxs-lookup"><span data-stu-id="11e8e-110">[out] One of the following values:</span></span>  
  
-   <span data-ttu-id="11e8e-111">`SN_CMP_DIFFERENT` (0): 指定組件包含不同的資料。</span><span class="sxs-lookup"><span data-stu-id="11e8e-111">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
-   <span data-ttu-id="11e8e-112">`SN_CMP_IDENTICAL` (1)-指定的組件完全相同，包括其簽章和總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="11e8e-112">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
-   <span data-ttu-id="11e8e-113">`SN_CMP_SIGONLY` (2)-指定只要簽章與總和檢查碼不同組件。</span><span class="sxs-lookup"><span data-stu-id="11e8e-113">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11e8e-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="11e8e-114">Return Value</span></span>  
 <span data-ttu-id="11e8e-115">`true` 如果成功地完成;否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="11e8e-115">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11e8e-116">需求</span><span class="sxs-lookup"><span data-stu-id="11e8e-116">Requirements</span></span>  
 <span data-ttu-id="11e8e-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="11e8e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11e8e-118">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="11e8e-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="11e8e-119">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="11e8e-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="11e8e-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11e8e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11e8e-121">備註</span><span class="sxs-lookup"><span data-stu-id="11e8e-121">Remarks</span></span>  
 <span data-ttu-id="11e8e-122">組件的強式名稱簽章是由組件的文字名稱、 版本、 文化特性和公開金鑰 token 所組成。</span><span class="sxs-lookup"><span data-stu-id="11e8e-122">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
 <span data-ttu-id="11e8e-123">如果`StrongNameCompareAssemblies`函式未順利完成，請呼叫[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函式來擷取最後一個產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="11e8e-123">If the `StrongNameCompareAssemblies` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11e8e-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11e8e-124">See also</span></span>

- [<span data-ttu-id="11e8e-125">StrongNameCompareAssemblies 方法</span><span class="sxs-lookup"><span data-stu-id="11e8e-125">StrongNameCompareAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [<span data-ttu-id="11e8e-126">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="11e8e-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

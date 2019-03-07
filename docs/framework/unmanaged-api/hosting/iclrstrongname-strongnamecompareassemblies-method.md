---
title: ICLRStrongName::StrongNameCompareAssemblies 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameCompareAssemblies
helpviewer_keywords:
- ICLRStrongName::StrongNameCompareAssemblies method [.NET Framework hosting]
- StrongNameCompareAssemblies method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: b1fb356c-72cf-4aa4-8376-f291a6d97c01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de4e55c8e1a13daf07a8a75a19a44127779d5c05
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481608"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a><span data-ttu-id="e15fa-102">ICLRStrongName::StrongNameCompareAssemblies 方法</span><span class="sxs-lookup"><span data-stu-id="e15fa-102">ICLRStrongName::StrongNameCompareAssemblies Method</span></span>
<span data-ttu-id="e15fa-103">判斷兩個組件是否只有強制名稱簽章不同。</span><span class="sxs-lookup"><span data-stu-id="e15fa-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e15fa-104">語法</span><span class="sxs-lookup"><span data-stu-id="e15fa-104">Syntax</span></span>  
  
```  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e15fa-105">參數</span><span class="sxs-lookup"><span data-stu-id="e15fa-105">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="e15fa-106">[in]第一個組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="e15fa-106">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="e15fa-107">[in]第二個組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="e15fa-107">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="e15fa-108">[out]下列值之一：</span><span class="sxs-lookup"><span data-stu-id="e15fa-108">[out] One of the following values:</span></span>  
  
-   <span data-ttu-id="e15fa-109">`SN_CMP_DIFFERENT` (0): 指定組件包含不同的資料。</span><span class="sxs-lookup"><span data-stu-id="e15fa-109">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
-   <span data-ttu-id="e15fa-110">`SN_CMP_IDENTICAL` (1)-指定的組件完全相同，包括其簽章和總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="e15fa-110">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
-   <span data-ttu-id="e15fa-111">`SN_CMP_SIGONLY` (2)-指定只要簽章與總和檢查碼不同組件。</span><span class="sxs-lookup"><span data-stu-id="e15fa-111">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e15fa-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="e15fa-112">Return Value</span></span>  
 <span data-ttu-id="e15fa-113">`S_OK` 如果這個方法順利完成否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="e15fa-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e15fa-114">需求</span><span class="sxs-lookup"><span data-stu-id="e15fa-114">Requirements</span></span>  
 <span data-ttu-id="e15fa-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e15fa-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e15fa-116">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e15fa-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e15fa-117">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e15fa-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e15fa-118">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e15fa-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e15fa-119">備註</span><span class="sxs-lookup"><span data-stu-id="e15fa-119">Remarks</span></span>  
 <span data-ttu-id="e15fa-120">組件的強式名稱簽章是由組件的文字名稱、 版本、 文化特性和公開金鑰 token 所組成。</span><span class="sxs-lookup"><span data-stu-id="e15fa-120">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e15fa-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e15fa-121">See also</span></span>
- [<span data-ttu-id="e15fa-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="e15fa-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

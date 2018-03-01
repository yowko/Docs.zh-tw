---
title: "ICLRStrongName::StrongNameCompareAssemblies 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 96fbeccf76de87a3582bf8c2084d0ca9ad7d27f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a><span data-ttu-id="f6624-102">ICLRStrongName::StrongNameCompareAssemblies 方法</span><span class="sxs-lookup"><span data-stu-id="f6624-102">ICLRStrongName::StrongNameCompareAssemblies Method</span></span>
<span data-ttu-id="f6624-103">判斷兩個組件是否只有其強式名稱簽章不同。</span><span class="sxs-lookup"><span data-stu-id="f6624-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6624-104">語法</span><span class="sxs-lookup"><span data-stu-id="f6624-104">Syntax</span></span>  
  
```  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f6624-105">參數</span><span class="sxs-lookup"><span data-stu-id="f6624-105">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="f6624-106">[in]第一個組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="f6624-106">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="f6624-107">[in]第二個組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="f6624-107">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="f6624-108">[out]下列值之一：</span><span class="sxs-lookup"><span data-stu-id="f6624-108">[out] One of the following values:</span></span>  
  
-   <span data-ttu-id="f6624-109">`SN_CMP_DIFFERENT`(0)-指定的組件包含不同的資料。</span><span class="sxs-lookup"><span data-stu-id="f6624-109">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
-   <span data-ttu-id="f6624-110">`SN_CMP_IDENTICAL`(1)-指定的組件完全相同，包括其簽章與總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="f6624-110">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
-   <span data-ttu-id="f6624-111">`SN_CMP_SIGONLY`(2)-指定只要簽章與總和檢查碼不同組件。</span><span class="sxs-lookup"><span data-stu-id="f6624-111">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6624-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="f6624-112">Return Value</span></span>  
 <span data-ttu-id="f6624-113">`S_OK`如果方法成功。否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](http://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="f6624-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6624-114">需求</span><span class="sxs-lookup"><span data-stu-id="f6624-114">Requirements</span></span>  
 <span data-ttu-id="f6624-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f6624-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6624-116">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f6624-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f6624-117">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f6624-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6624-118">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6624-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6624-119">備註</span><span class="sxs-lookup"><span data-stu-id="f6624-119">Remarks</span></span>  
 <span data-ttu-id="f6624-120">組件的強式名稱簽章包含組件的文字名稱、 版本、 文化特性和公開金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f6624-120">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6624-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="f6624-121">See Also</span></span>  
 [<span data-ttu-id="f6624-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="f6624-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

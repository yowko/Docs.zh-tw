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
ms.openlocfilehash: 0087636c68d0748ad2b143de9b132278ab9d43f5
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762054"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a><span data-ttu-id="6aae4-102">ICLRStrongName::StrongNameCompareAssemblies 方法</span><span class="sxs-lookup"><span data-stu-id="6aae4-102">ICLRStrongName::StrongNameCompareAssemblies Method</span></span>
<span data-ttu-id="6aae4-103">判斷兩個組件是否只有強制名稱簽章不同。</span><span class="sxs-lookup"><span data-stu-id="6aae4-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6aae4-104">語法</span><span class="sxs-lookup"><span data-stu-id="6aae4-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6aae4-105">參數</span><span class="sxs-lookup"><span data-stu-id="6aae4-105">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="6aae4-106">在第一個元件的路徑。</span><span class="sxs-lookup"><span data-stu-id="6aae4-106">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="6aae4-107">在第二個元件的路徑。</span><span class="sxs-lookup"><span data-stu-id="6aae4-107">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="6aae4-108">脫銷下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="6aae4-108">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="6aae4-109">`SN_CMP_DIFFERENT`（0）-指定元件包含不同的資料。</span><span class="sxs-lookup"><span data-stu-id="6aae4-109">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="6aae4-110">`SN_CMP_IDENTICAL`（1）-指定元件完全相同，包括其簽章和總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="6aae4-110">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="6aae4-111">`SN_CMP_SIGONLY`（2）-指定元件只有簽章和總和檢查碼不同。</span><span class="sxs-lookup"><span data-stu-id="6aae4-111">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6aae4-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="6aae4-112">Return Value</span></span>  
 <span data-ttu-id="6aae4-113">`S_OK`如果方法已成功完成，則為，否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="6aae4-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6aae4-114">規格需求</span><span class="sxs-lookup"><span data-stu-id="6aae4-114">Requirements</span></span>  
 <span data-ttu-id="6aae4-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6aae4-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6aae4-116">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="6aae4-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6aae4-117">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6aae4-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6aae4-118">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6aae4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6aae4-119">備註</span><span class="sxs-lookup"><span data-stu-id="6aae4-119">Remarks</span></span>  
 <span data-ttu-id="6aae4-120">元件的強式名稱簽章是由元件的文字名稱、版本、文化特性和公開金鑰 token 所組成。</span><span class="sxs-lookup"><span data-stu-id="6aae4-120">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aae4-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6aae4-121">See also</span></span>

- [<span data-ttu-id="6aae4-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="6aae4-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)

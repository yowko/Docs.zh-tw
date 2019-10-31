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
ms.openlocfilehash: fdca03b781e07b709cbc54e673dbaa2a1130fbe3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135153"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a><span data-ttu-id="d1de4-102">ICLRStrongName::StrongNameCompareAssemblies 方法</span><span class="sxs-lookup"><span data-stu-id="d1de4-102">ICLRStrongName::StrongNameCompareAssemblies Method</span></span>
<span data-ttu-id="d1de4-103">判斷兩個組件是否只有強制名稱簽章不同。</span><span class="sxs-lookup"><span data-stu-id="d1de4-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1de4-104">語法</span><span class="sxs-lookup"><span data-stu-id="d1de4-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1de4-105">參數</span><span class="sxs-lookup"><span data-stu-id="d1de4-105">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="d1de4-106">在第一個元件的路徑。</span><span class="sxs-lookup"><span data-stu-id="d1de4-106">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="d1de4-107">在第二個元件的路徑。</span><span class="sxs-lookup"><span data-stu-id="d1de4-107">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="d1de4-108">脫銷下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="d1de4-108">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="d1de4-109">`SN_CMP_DIFFERENT` （0）-指定元件包含不同的資料。</span><span class="sxs-lookup"><span data-stu-id="d1de4-109">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="d1de4-110">`SN_CMP_IDENTICAL` （1）-指定元件完全相同，包括其簽章和總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="d1de4-110">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="d1de4-111">`SN_CMP_SIGONLY` （2）-指定元件只有簽章和總和檢查碼不同。</span><span class="sxs-lookup"><span data-stu-id="d1de4-111">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1de4-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="d1de4-112">Return Value</span></span>  
 <span data-ttu-id="d1de4-113">如果方法順利完成，`S_OK`;否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)）。</span><span class="sxs-lookup"><span data-stu-id="d1de4-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1de4-114">需求</span><span class="sxs-lookup"><span data-stu-id="d1de4-114">Requirements</span></span>  
 <span data-ttu-id="d1de4-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d1de4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1de4-116">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="d1de4-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d1de4-117">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d1de4-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1de4-118">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1de4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1de4-119">備註</span><span class="sxs-lookup"><span data-stu-id="d1de4-119">Remarks</span></span>  
 <span data-ttu-id="d1de4-120">元件的強式名稱簽章是由元件的文字名稱、版本、文化特性和公開金鑰 token 所組成。</span><span class="sxs-lookup"><span data-stu-id="d1de4-120">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1de4-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="d1de4-121">See also</span></span>

- [<span data-ttu-id="d1de4-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="d1de4-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

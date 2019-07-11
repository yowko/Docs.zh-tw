---
title: ICLRStrongName::StrongNameTokenFromAssembly 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly method [.NET Framework hosting]
- StrongNameTokenFromAssembly method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: fc725afb-b66b-4015-aa44-1c0d1304197f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb399b9fee5ea3e094aa9e1842a493b10eb39def
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759199"
---
# <a name="iclrstrongnamestrongnametokenfromassembly-method"></a><span data-ttu-id="1ecc9-102">ICLRStrongName::StrongNameTokenFromAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="1ecc9-102">ICLRStrongName::StrongNameTokenFromAssembly Method</span></span>
<span data-ttu-id="1ecc9-103">從指定的組件檔案建立強式名稱權杖。</span><span class="sxs-lookup"><span data-stu-id="1ecc9-103">Creates a strong name token from the specified assembly file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ecc9-104">語法</span><span class="sxs-lookup"><span data-stu-id="1ecc9-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ecc9-105">參數</span><span class="sxs-lookup"><span data-stu-id="1ecc9-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="1ecc9-106">[in]組件的可攜式執行檔 (PE) 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="1ecc9-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="1ecc9-107">[out]傳回的強式名稱語彙基元。</span><span class="sxs-lookup"><span data-stu-id="1ecc9-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="1ecc9-108">[out]大小，以位元組為單位的強式名稱語彙基元。</span><span class="sxs-lookup"><span data-stu-id="1ecc9-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ecc9-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="1ecc9-109">Return Value</span></span>  
 <span data-ttu-id="1ecc9-110">`S_OK` 如果這個方法順利完成否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="1ecc9-110">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ecc9-111">備註</span><span class="sxs-lookup"><span data-stu-id="1ecc9-111">Remarks</span></span>  
 <span data-ttu-id="1ecc9-112">強式名稱語彙基元是公開金鑰的縮短格式。</span><span class="sxs-lookup"><span data-stu-id="1ecc9-112">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="1ecc9-113">64 位元雜湊建立用來簽署組件的公開金鑰權杖。</span><span class="sxs-lookup"><span data-stu-id="1ecc9-113">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="1ecc9-114">此權杖是組件的強式名稱的一部分，而且可以讀取組件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="1ecc9-114">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="1ecc9-115">建立權杖之後，您應該呼叫[iclrstrongname:: Strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法來釋放配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="1ecc9-115">After the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ecc9-116">需求</span><span class="sxs-lookup"><span data-stu-id="1ecc9-116">Requirements</span></span>  
 <span data-ttu-id="1ecc9-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1ecc9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ecc9-118">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1ecc9-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1ecc9-119">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1ecc9-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1ecc9-120">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ecc9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ecc9-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ecc9-121">See also</span></span>

- [<span data-ttu-id="1ecc9-122">StrongNameTokenFromAssemblyEx 方法</span><span class="sxs-lookup"><span data-stu-id="1ecc9-122">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="1ecc9-123">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="1ecc9-123">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

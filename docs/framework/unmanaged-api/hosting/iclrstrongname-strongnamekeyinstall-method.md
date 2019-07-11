---
title: ICLRStrongName::StrongNameKeyInstall 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyInstall
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyInstall method [.NET Framework hosting]
- StrongNameKeyInstall method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5c15cf3b-164c-49d1-8e57-e42949d55acf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a2badf8f164abd1bbb8892ec5db28f7cf39f5c5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775662"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="63fd3-102">ICLRStrongName::StrongNameKeyInstall 方法</span><span class="sxs-lookup"><span data-stu-id="63fd3-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="63fd3-103">將公開/私密金鑰組匯入到容器中。</span><span class="sxs-lookup"><span data-stu-id="63fd3-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63fd3-104">語法</span><span class="sxs-lookup"><span data-stu-id="63fd3-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63fd3-105">參數</span><span class="sxs-lookup"><span data-stu-id="63fd3-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="63fd3-106">[in]金鑰容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="63fd3-106">[in] The name of the key container.</span></span> <span data-ttu-id="63fd3-107">`wszKeyContainer` 必須是非空白字串。</span><span class="sxs-lookup"><span data-stu-id="63fd3-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="63fd3-108">[in]二進位金鑰組。</span><span class="sxs-lookup"><span data-stu-id="63fd3-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="63fd3-109">[in]大小，以位元組為單位的`pbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="63fd3-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63fd3-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="63fd3-110">Return Value</span></span>  
 <span data-ttu-id="63fd3-111">`S_OK` 如果這個方法順利完成否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="63fd3-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63fd3-112">備註</span><span class="sxs-lookup"><span data-stu-id="63fd3-112">Remarks</span></span>  
 <span data-ttu-id="63fd3-113">使用[iclrstrongname:: Strongnamekeydelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)方法來刪除金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="63fd3-113">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63fd3-114">需求</span><span class="sxs-lookup"><span data-stu-id="63fd3-114">Requirements</span></span>  
 <span data-ttu-id="63fd3-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="63fd3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63fd3-116">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="63fd3-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="63fd3-117">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="63fd3-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63fd3-118">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63fd3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63fd3-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63fd3-119">See also</span></span>

- [<span data-ttu-id="63fd3-120">StrongNameKeyDelete 方法</span><span class="sxs-lookup"><span data-stu-id="63fd3-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="63fd3-121">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="63fd3-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

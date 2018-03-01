---
title: "ICLRStrongName::StrongNameKeyInstall 方法"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: df1bdb5d6d6018855cb76b48d58e557a61288a51
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="66b0d-102">ICLRStrongName::StrongNameKeyInstall 方法</span><span class="sxs-lookup"><span data-stu-id="66b0d-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="66b0d-103">匯入容器的公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="66b0d-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66b0d-104">語法</span><span class="sxs-lookup"><span data-stu-id="66b0d-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66b0d-105">參數</span><span class="sxs-lookup"><span data-stu-id="66b0d-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="66b0d-106">[in]金鑰容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="66b0d-106">[in] The name of the key container.</span></span> <span data-ttu-id="66b0d-107">`wszKeyContainer`必須是非空白字串。</span><span class="sxs-lookup"><span data-stu-id="66b0d-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="66b0d-108">[in]二進位的金鑰組。</span><span class="sxs-lookup"><span data-stu-id="66b0d-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="66b0d-109">[in]大小，以位元組為單位的`pbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="66b0d-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66b0d-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="66b0d-110">Return Value</span></span>  
 <span data-ttu-id="66b0d-111">`S_OK`如果方法成功。否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](http://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="66b0d-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66b0d-112">備註</span><span class="sxs-lookup"><span data-stu-id="66b0d-112">Remarks</span></span>  
 <span data-ttu-id="66b0d-113">使用[iclrstrongname:: Strongnamekeydelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)方法，以刪除金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="66b0d-113">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66b0d-114">需求</span><span class="sxs-lookup"><span data-stu-id="66b0d-114">Requirements</span></span>  
 <span data-ttu-id="66b0d-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="66b0d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66b0d-116">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="66b0d-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="66b0d-117">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="66b0d-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="66b0d-118">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66b0d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66b0d-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="66b0d-119">See Also</span></span>  
 [<span data-ttu-id="66b0d-120">StrongNameKeyDelete 方法</span><span class="sxs-lookup"><span data-stu-id="66b0d-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="66b0d-121">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="66b0d-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

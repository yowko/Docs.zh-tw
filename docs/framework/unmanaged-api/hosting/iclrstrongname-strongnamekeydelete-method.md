---
title: ICLRStrongName::StrongNameKeyDelete 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyDelete method [.NET Framework hosting]
ms.assetid: 0163412f-f617-4428-89e0-03992fec31e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e9cd423bd351d9e4b12f21fe3a4a52c9909b7ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432056"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="b6df3-102">ICLRStrongName::StrongNameKeyDelete 方法</span><span class="sxs-lookup"><span data-stu-id="b6df3-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="b6df3-103">刪除指定的金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="b6df3-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6df3-104">語法</span><span class="sxs-lookup"><span data-stu-id="b6df3-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6df3-105">參數</span><span class="sxs-lookup"><span data-stu-id="b6df3-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="b6df3-106">[in]若要刪除的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="b6df3-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6df3-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="b6df3-107">Return Value</span></span>  
 <span data-ttu-id="b6df3-108">`S_OK` 如果方法成功。否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](http://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="b6df3-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6df3-109">備註</span><span class="sxs-lookup"><span data-stu-id="b6df3-109">Remarks</span></span>  
 <span data-ttu-id="b6df3-110">使用[iclrstrongname:: Strongnamekeyinstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)方法來匯入到容器的公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="b6df3-110">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6df3-111">需求</span><span class="sxs-lookup"><span data-stu-id="b6df3-111">Requirements</span></span>  
 <span data-ttu-id="b6df3-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6df3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6df3-113">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="b6df3-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b6df3-114">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b6df3-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6df3-115">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6df3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6df3-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6df3-116">See Also</span></span>  
 [<span data-ttu-id="b6df3-117">StrongNameKeyInstall 方法</span><span class="sxs-lookup"><span data-stu-id="b6df3-117">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="b6df3-118">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="b6df3-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

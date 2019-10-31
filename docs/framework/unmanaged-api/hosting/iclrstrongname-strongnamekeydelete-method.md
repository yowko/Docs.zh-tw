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
ms.openlocfilehash: 4e72818be6808c519677192d3744bbc5ec414d0d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135087"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="44aff-102">ICLRStrongName::StrongNameKeyDelete 方法</span><span class="sxs-lookup"><span data-stu-id="44aff-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="44aff-103">刪除指定的金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="44aff-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44aff-104">語法</span><span class="sxs-lookup"><span data-stu-id="44aff-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44aff-105">參數</span><span class="sxs-lookup"><span data-stu-id="44aff-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="44aff-106">在要刪除的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="44aff-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44aff-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="44aff-107">Return Value</span></span>  
 <span data-ttu-id="44aff-108">如果方法順利完成，`S_OK`;否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)）。</span><span class="sxs-lookup"><span data-stu-id="44aff-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44aff-109">備註</span><span class="sxs-lookup"><span data-stu-id="44aff-109">Remarks</span></span>  
 <span data-ttu-id="44aff-110">使用[ICLRStrongName：： StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)方法，將公開/私密金鑰組匯入容器。</span><span class="sxs-lookup"><span data-stu-id="44aff-110">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44aff-111">需求</span><span class="sxs-lookup"><span data-stu-id="44aff-111">Requirements</span></span>  
 <span data-ttu-id="44aff-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="44aff-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44aff-113">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="44aff-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="44aff-114">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="44aff-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44aff-115">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44aff-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44aff-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="44aff-116">See also</span></span>

- [<span data-ttu-id="44aff-117">StrongNameKeyInstall 方法</span><span class="sxs-lookup"><span data-stu-id="44aff-117">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="44aff-118">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="44aff-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

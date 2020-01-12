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
ms.openlocfilehash: 95098cbb060c06d2d5a5a4c04b6fa9017bca66a1
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899586"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="7f270-102">ICLRStrongName::StrongNameKeyDelete 方法</span><span class="sxs-lookup"><span data-stu-id="7f270-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="7f270-103">刪除指定的金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="7f270-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f270-104">語法</span><span class="sxs-lookup"><span data-stu-id="7f270-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f270-105">參數</span><span class="sxs-lookup"><span data-stu-id="7f270-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="7f270-106">在要刪除的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="7f270-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f270-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="7f270-107">Return Value</span></span>  
 <span data-ttu-id="7f270-108">如果方法順利完成，`S_OK`;否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="7f270-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f270-109">備註</span><span class="sxs-lookup"><span data-stu-id="7f270-109">Remarks</span></span>  
 <span data-ttu-id="7f270-110">使用[ICLRStrongName：： StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)方法，將公開/私密金鑰組匯入容器。</span><span class="sxs-lookup"><span data-stu-id="7f270-110">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f270-111">需求</span><span class="sxs-lookup"><span data-stu-id="7f270-111">Requirements</span></span>  
 <span data-ttu-id="7f270-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7f270-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f270-113">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="7f270-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7f270-114">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7f270-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f270-115">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f270-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f270-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="7f270-116">See also</span></span>

- [<span data-ttu-id="7f270-117">StrongNameKeyInstall 方法</span><span class="sxs-lookup"><span data-stu-id="7f270-117">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="7f270-118">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="7f270-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

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
ms.openlocfilehash: 2a76377857c3cf1e40a328b9a13fb4834321707e
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899560"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="4ba5a-102">ICLRStrongName::StrongNameKeyInstall 方法</span><span class="sxs-lookup"><span data-stu-id="4ba5a-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="4ba5a-103">將公開/私密金鑰組匯入到容器中。</span><span class="sxs-lookup"><span data-stu-id="4ba5a-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ba5a-104">語法</span><span class="sxs-lookup"><span data-stu-id="4ba5a-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ba5a-105">參數</span><span class="sxs-lookup"><span data-stu-id="4ba5a-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="4ba5a-106">在金鑰容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="4ba5a-106">[in] The name of the key container.</span></span> <span data-ttu-id="4ba5a-107">`wszKeyContainer` 必須是非空白字串。</span><span class="sxs-lookup"><span data-stu-id="4ba5a-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="4ba5a-108">在二進位金鑰組。</span><span class="sxs-lookup"><span data-stu-id="4ba5a-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="4ba5a-109">在`pbKeyBlob`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="4ba5a-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ba5a-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="4ba5a-110">Return Value</span></span>  
 <span data-ttu-id="4ba5a-111">如果方法順利完成，`S_OK`;否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="4ba5a-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ba5a-112">備註</span><span class="sxs-lookup"><span data-stu-id="4ba5a-112">Remarks</span></span>  
 <span data-ttu-id="4ba5a-113">請使用[ICLRStrongName：： StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)方法來刪除金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="4ba5a-113">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ba5a-114">需求</span><span class="sxs-lookup"><span data-stu-id="4ba5a-114">Requirements</span></span>  
 <span data-ttu-id="4ba5a-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4ba5a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ba5a-116">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="4ba5a-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4ba5a-117">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4ba5a-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4ba5a-118">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ba5a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ba5a-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="4ba5a-119">See also</span></span>

- [<span data-ttu-id="4ba5a-120">StrongNameKeyDelete 方法</span><span class="sxs-lookup"><span data-stu-id="4ba5a-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="4ba5a-121">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="4ba5a-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

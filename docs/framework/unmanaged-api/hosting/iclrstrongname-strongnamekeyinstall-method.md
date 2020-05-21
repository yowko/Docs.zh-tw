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
ms.openlocfilehash: e0c60d6e74c48531a223f6dbb35125b5a2017cbb
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763033"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="8711c-102">ICLRStrongName::StrongNameKeyInstall 方法</span><span class="sxs-lookup"><span data-stu-id="8711c-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="8711c-103">將公開/私密金鑰組匯入到容器中。</span><span class="sxs-lookup"><span data-stu-id="8711c-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8711c-104">語法</span><span class="sxs-lookup"><span data-stu-id="8711c-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8711c-105">參數</span><span class="sxs-lookup"><span data-stu-id="8711c-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="8711c-106">在金鑰容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="8711c-106">[in] The name of the key container.</span></span> <span data-ttu-id="8711c-107">`wszKeyContainer`必須是非空白字串。</span><span class="sxs-lookup"><span data-stu-id="8711c-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="8711c-108">在二進位金鑰組。</span><span class="sxs-lookup"><span data-stu-id="8711c-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="8711c-109">在的大小（以位元組為單位） `pbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="8711c-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8711c-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="8711c-110">Return Value</span></span>  
 <span data-ttu-id="8711c-111">`S_OK`如果方法已成功完成，則為，否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="8711c-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8711c-112">備註</span><span class="sxs-lookup"><span data-stu-id="8711c-112">Remarks</span></span>  
 <span data-ttu-id="8711c-113">請使用[ICLRStrongName：： StrongNameKeyDelete](iclrstrongname-strongnamekeydelete-method.md)方法來刪除金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="8711c-113">Use the [ICLRStrongName::StrongNameKeyDelete](iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8711c-114">規格需求</span><span class="sxs-lookup"><span data-stu-id="8711c-114">Requirements</span></span>  
 <span data-ttu-id="8711c-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8711c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8711c-116">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="8711c-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8711c-117">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8711c-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8711c-118">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8711c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8711c-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8711c-119">See also</span></span>

- [<span data-ttu-id="8711c-120">StrongNameKeyDelete 方法</span><span class="sxs-lookup"><span data-stu-id="8711c-120">StrongNameKeyDelete Method</span></span>](iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="8711c-121">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="8711c-121">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)

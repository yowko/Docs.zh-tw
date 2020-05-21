---
title: ICLRStrongName::StrongNameKeyGen 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyGen method [.NET Framework hosting]
ms.assetid: ac5c1245-9acf-4271-9c08-3d9b7c670df3
topic_type:
- apiref
ms.openlocfilehash: db5c0dbe57607c7a3bf8b97cee734415aa934336
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763081"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a><span data-ttu-id="22c15-102">ICLRStrongName::StrongNameKeyGen 方法</span><span class="sxs-lookup"><span data-stu-id="22c15-102">ICLRStrongName::StrongNameKeyGen Method</span></span>
<span data-ttu-id="22c15-103">建立將供強式名稱使用的新公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="22c15-103">Creates a new public/private key pair for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22c15-104">語法</span><span class="sxs-lookup"><span data-stu-id="22c15-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22c15-105">參數</span><span class="sxs-lookup"><span data-stu-id="22c15-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="22c15-106">在要求的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="22c15-106">[in] The requested key container name.</span></span> <span data-ttu-id="22c15-107">`wszKeyContainer`必須是非空白字串或 null，才能產生暫存名稱。</span><span class="sxs-lookup"><span data-stu-id="22c15-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="22c15-108">在值，指定是否要保留註冊的金鑰。</span><span class="sxs-lookup"><span data-stu-id="22c15-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="22c15-109">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="22c15-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="22c15-110">0x00000000-在為 null 時使用， `wszKeyContainer` 以產生暫存金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="22c15-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="22c15-111">0x00000001 （ `SN_LEAVE_KEY` ）-指定應將金鑰保留為已註冊。</span><span class="sxs-lookup"><span data-stu-id="22c15-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="22c15-112">脫銷傳回的公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="22c15-112">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="22c15-113">脫銷的大小（以位元組為單位） `ppbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="22c15-113">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22c15-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="22c15-114">Return Value</span></span>  
 <span data-ttu-id="22c15-115">`S_OK`如果方法已成功完成，則為，否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="22c15-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22c15-116">備註</span><span class="sxs-lookup"><span data-stu-id="22c15-116">Remarks</span></span>  
 <span data-ttu-id="22c15-117">[ICLRStrongName：： StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)方法會建立1024位金鑰。</span><span class="sxs-lookup"><span data-stu-id="22c15-117">The [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method creates a 1024-bit key.</span></span> <span data-ttu-id="22c15-118">在取得金鑰之後，您應該呼叫[ICLRStrongName：： StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md)方法來釋放已配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="22c15-118">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22c15-119">規格需求</span><span class="sxs-lookup"><span data-stu-id="22c15-119">Requirements</span></span>  
 <span data-ttu-id="22c15-120">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="22c15-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22c15-121">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="22c15-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="22c15-122">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="22c15-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="22c15-123">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22c15-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22c15-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22c15-124">See also</span></span>

- [<span data-ttu-id="22c15-125">StrongNameKeyGenEx 方法</span><span class="sxs-lookup"><span data-stu-id="22c15-125">StrongNameKeyGenEx Method</span></span>](iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="22c15-126">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="22c15-126">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)

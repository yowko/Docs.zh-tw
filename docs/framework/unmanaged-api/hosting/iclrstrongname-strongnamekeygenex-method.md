---
title: ICLRStrongName::StrongNameKeyGenEx 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGenEx
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyGenEx method [.NET Framework hosting]
- StrongNameKeyGenEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 1f8b59d0-5b72-45b8-ab74-c2b43ffc806e
topic_type:
- apiref
ms.openlocfilehash: b09677a45c5d515aacb2cac709599140039a9dd8
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899547"
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a><span data-ttu-id="c450b-102">ICLRStrongName::StrongNameKeyGenEx 方法</span><span class="sxs-lookup"><span data-stu-id="c450b-102">ICLRStrongName::StrongNameKeyGenEx Method</span></span>
<span data-ttu-id="c450b-103">產生具有指定金鑰大小的新公開/私密金鑰組，以供強式名稱使用。</span><span class="sxs-lookup"><span data-stu-id="c450b-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c450b-104">語法</span><span class="sxs-lookup"><span data-stu-id="c450b-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c450b-105">參數</span><span class="sxs-lookup"><span data-stu-id="c450b-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="c450b-106">在要求的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="c450b-106">[in] The requested key container name.</span></span> <span data-ttu-id="c450b-107">`wszKeyContainer` 必須是非空白字串或 null，才能產生暫存名稱。</span><span class="sxs-lookup"><span data-stu-id="c450b-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c450b-108">在值，指定是否要保留註冊的金鑰。</span><span class="sxs-lookup"><span data-stu-id="c450b-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="c450b-109">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="c450b-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="c450b-110">0x00000000-在 `wszKeyContainer` 為 null 時用來產生暫存金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="c450b-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="c450b-111">0x00000001 （`SN_LEAVE_KEY`）-指定應將金鑰保留為已註冊。</span><span class="sxs-lookup"><span data-stu-id="c450b-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="c450b-112">在要求的金鑰大小（以位為單位）。</span><span class="sxs-lookup"><span data-stu-id="c450b-112">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="c450b-113">脫銷傳回的公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="c450b-113">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="c450b-114">脫銷`ppbKeyBlob`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="c450b-114">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c450b-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="c450b-115">Return Value</span></span>  
 <span data-ttu-id="c450b-116">如果方法順利完成，`S_OK`;否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="c450b-116">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c450b-117">備註</span><span class="sxs-lookup"><span data-stu-id="c450b-117">Remarks</span></span>  
 <span data-ttu-id="c450b-118">.NET Framework 版本1.0 和1.1 需要1024位的 `dwKeySize`，才能以強式名稱簽署元件;2.0 版新增了2048位金鑰的支援。</span><span class="sxs-lookup"><span data-stu-id="c450b-118">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="c450b-119">在取得金鑰之後，您應該呼叫[ICLRStrongName：： StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法來釋放已配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="c450b-119">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c450b-120">需求</span><span class="sxs-lookup"><span data-stu-id="c450b-120">Requirements</span></span>  
 <span data-ttu-id="c450b-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c450b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c450b-122">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="c450b-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c450b-123">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c450b-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c450b-124">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c450b-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c450b-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="c450b-125">See also</span></span>

- [<span data-ttu-id="c450b-126">StrongNameKeyGen 方法</span><span class="sxs-lookup"><span data-stu-id="c450b-126">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="c450b-127">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="c450b-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

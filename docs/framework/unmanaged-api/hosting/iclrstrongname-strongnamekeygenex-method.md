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
ms.openlocfilehash: fb18b7b5ac73a1f270af6fae95a23e04b17ca5f1
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763068"
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a><span data-ttu-id="d9b3c-102">ICLRStrongName::StrongNameKeyGenEx 方法</span><span class="sxs-lookup"><span data-stu-id="d9b3c-102">ICLRStrongName::StrongNameKeyGenEx Method</span></span>
<span data-ttu-id="d9b3c-103">產生具有指定金鑰大小的新公開/私密金鑰組，以供強式名稱使用。</span><span class="sxs-lookup"><span data-stu-id="d9b3c-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9b3c-104">語法</span><span class="sxs-lookup"><span data-stu-id="d9b3c-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9b3c-105">參數</span><span class="sxs-lookup"><span data-stu-id="d9b3c-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="d9b3c-106">在要求的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="d9b3c-106">[in] The requested key container name.</span></span> <span data-ttu-id="d9b3c-107">`wszKeyContainer`必須是非空白字串或 null，才能產生暫存名稱。</span><span class="sxs-lookup"><span data-stu-id="d9b3c-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d9b3c-108">在值，指定是否要保留註冊的金鑰。</span><span class="sxs-lookup"><span data-stu-id="d9b3c-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="d9b3c-109">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="d9b3c-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="d9b3c-110">0x00000000-在為 null 時使用， `wszKeyContainer` 以產生暫存金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="d9b3c-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="d9b3c-111">0x00000001 （ `SN_LEAVE_KEY` ）-指定應將金鑰保留為已註冊。</span><span class="sxs-lookup"><span data-stu-id="d9b3c-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="d9b3c-112">在要求的金鑰大小（以位為單位）。</span><span class="sxs-lookup"><span data-stu-id="d9b3c-112">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="d9b3c-113">脫銷傳回的公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="d9b3c-113">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="d9b3c-114">脫銷的大小（以位元組為單位） `ppbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="d9b3c-114">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9b3c-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="d9b3c-115">Return Value</span></span>  
 <span data-ttu-id="d9b3c-116">`S_OK`如果方法已成功完成，則為，否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="d9b3c-116">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9b3c-117">備註</span><span class="sxs-lookup"><span data-stu-id="d9b3c-117">Remarks</span></span>  
 <span data-ttu-id="d9b3c-118">.NET Framework 版本1.0 和1.1 需要 `dwKeySize` 1024 位以強式名稱簽署元件; 版本2.0 新增了支援的2048位金鑰。</span><span class="sxs-lookup"><span data-stu-id="d9b3c-118">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="d9b3c-119">在取得金鑰之後，您應該呼叫[ICLRStrongName：： StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md)方法來釋放已配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="d9b3c-119">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9b3c-120">規格需求</span><span class="sxs-lookup"><span data-stu-id="d9b3c-120">Requirements</span></span>  
 <span data-ttu-id="d9b3c-121">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d9b3c-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9b3c-122">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="d9b3c-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d9b3c-123">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d9b3c-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9b3c-124">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9b3c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9b3c-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9b3c-125">See also</span></span>

- [<span data-ttu-id="d9b3c-126">StrongNameKeyGen 方法</span><span class="sxs-lookup"><span data-stu-id="d9b3c-126">StrongNameKeyGen Method</span></span>](iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="d9b3c-127">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="d9b3c-127">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)

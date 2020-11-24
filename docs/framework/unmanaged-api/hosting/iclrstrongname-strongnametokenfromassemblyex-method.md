---
title: ICLRStrongName::StrongNameTokenFromAssemblyEx 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameTokenFromAssemblyEx method [.NET Framework hosting]
ms.assetid: 648ea90e-5e60-40a0-a56a-3e61bf2fba7c
topic_type:
- apiref
ms.openlocfilehash: 35fe86f856360814cfbb5453bfb6e5efaaef02fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677722"
---
# <a name="iclrstrongnamestrongnametokenfromassemblyex-method"></a><span data-ttu-id="ab1b6-102">ICLRStrongName::StrongNameTokenFromAssemblyEx 方法</span><span class="sxs-lookup"><span data-stu-id="ab1b6-102">ICLRStrongName::StrongNameTokenFromAssemblyEx Method</span></span>

<span data-ttu-id="ab1b6-103">從指定的元件檔案建立強式名稱權杖，並傳回權杖所代表的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="ab1b6-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab1b6-104">語法</span><span class="sxs-lookup"><span data-stu-id="ab1b6-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab1b6-105">參數</span><span class="sxs-lookup"><span data-stu-id="ab1b6-105">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="ab1b6-106">在元件的可攜式可執行檔 (PE) 檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="ab1b6-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="ab1b6-107">擴展傳回的強式名稱 token。</span><span class="sxs-lookup"><span data-stu-id="ab1b6-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="ab1b6-108">擴展強式名稱權杖的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="ab1b6-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="ab1b6-109">擴展傳回的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="ab1b6-109">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="ab1b6-110">擴展公開金鑰的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="ab1b6-110">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab1b6-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="ab1b6-111">Return Value</span></span>  

 <span data-ttu-id="ab1b6-112">`S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。</span><span class="sxs-lookup"><span data-stu-id="ab1b6-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab1b6-113">備註</span><span class="sxs-lookup"><span data-stu-id="ab1b6-113">Remarks</span></span>  

 <span data-ttu-id="ab1b6-114">強式名稱權杖是公開金鑰的縮寫形式。</span><span class="sxs-lookup"><span data-stu-id="ab1b6-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="ab1b6-115">權杖是從用來簽署元件的公開金鑰建立的64位雜湊。</span><span class="sxs-lookup"><span data-stu-id="ab1b6-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="ab1b6-116">權杖是元件強式名稱的一部分，而且可以從元件中繼資料讀取。</span><span class="sxs-lookup"><span data-stu-id="ab1b6-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="ab1b6-117">在抓取金鑰並建立權杖之後，您應該呼叫 [ICLRStrongName：： StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) 方法來釋放已配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="ab1b6-117">After the key is retrieved and the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab1b6-118">需求</span><span class="sxs-lookup"><span data-stu-id="ab1b6-118">Requirements</span></span>  

 <span data-ttu-id="ab1b6-119">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ab1b6-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab1b6-120">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="ab1b6-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ab1b6-121">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="ab1b6-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab1b6-122">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab1b6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab1b6-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab1b6-123">See also</span></span>

- [<span data-ttu-id="ab1b6-124">StrongNameTokenFromAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="ab1b6-124">StrongNameTokenFromAssembly Method</span></span>](iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="ab1b6-125">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="ab1b6-125">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)

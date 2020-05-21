---
title: ICLRStrongName::StrongNameTokenFromAssembly 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly method [.NET Framework hosting]
- StrongNameTokenFromAssembly method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: fc725afb-b66b-4015-aa44-1c0d1304197f
topic_type:
- apiref
ms.openlocfilehash: e71fcf80b51edc318bbc7d81bb277c614184ee55
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762509"
---
# <a name="iclrstrongnamestrongnametokenfromassembly-method"></a><span data-ttu-id="5df24-102">ICLRStrongName::StrongNameTokenFromAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="5df24-102">ICLRStrongName::StrongNameTokenFromAssembly Method</span></span>
<span data-ttu-id="5df24-103">從指定的組件檔案建立強式名稱權杖。</span><span class="sxs-lookup"><span data-stu-id="5df24-103">Creates a strong name token from the specified assembly file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5df24-104">語法</span><span class="sxs-lookup"><span data-stu-id="5df24-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5df24-105">參數</span><span class="sxs-lookup"><span data-stu-id="5df24-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="5df24-106">在元件的可移植執行檔（PE）路徑。</span><span class="sxs-lookup"><span data-stu-id="5df24-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="5df24-107">脫銷傳回的強式名稱 token。</span><span class="sxs-lookup"><span data-stu-id="5df24-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="5df24-108">脫銷強式名稱 token 的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="5df24-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5df24-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="5df24-109">Return Value</span></span>  
 <span data-ttu-id="5df24-110">`S_OK`如果方法已成功完成，則為，否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="5df24-110">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5df24-111">備註</span><span class="sxs-lookup"><span data-stu-id="5df24-111">Remarks</span></span>  
 <span data-ttu-id="5df24-112">強式名稱 token 是公用金鑰的縮寫格式。</span><span class="sxs-lookup"><span data-stu-id="5df24-112">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="5df24-113">Token 是從用來簽署元件的公開金鑰所建立的64位雜湊。</span><span class="sxs-lookup"><span data-stu-id="5df24-113">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="5df24-114">Token 是元件強式名稱的一部分，而且可以從元件中繼資料讀取。</span><span class="sxs-lookup"><span data-stu-id="5df24-114">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="5df24-115">建立權杖之後，您應該呼叫[ICLRStrongName：： StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md)方法來釋放已配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="5df24-115">After the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5df24-116">規格需求</span><span class="sxs-lookup"><span data-stu-id="5df24-116">Requirements</span></span>  
 <span data-ttu-id="5df24-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5df24-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5df24-118">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="5df24-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5df24-119">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5df24-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5df24-120">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5df24-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5df24-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5df24-121">See also</span></span>

- [<span data-ttu-id="5df24-122">StrongNameTokenFromAssemblyEx 方法</span><span class="sxs-lookup"><span data-stu-id="5df24-122">StrongNameTokenFromAssemblyEx Method</span></span>](iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="5df24-123">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="5df24-123">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)

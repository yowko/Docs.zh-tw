---
title: StrongNameTokenFromAssembly 函式
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssembly
helpviewer_keywords:
- StrongNameTokenFromAssembly function [.NET Framework strong naming]
ms.assetid: 0a4b47ee-02f6-4a98-864e-a6f11ca3f2d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f88c0feea48ee96745effc36798bb26b4ccbf3cc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168671"
---
# <a name="strongnametokenfromassembly-function"></a><span data-ttu-id="5fec4-102">StrongNameTokenFromAssembly 函式</span><span class="sxs-lookup"><span data-stu-id="5fec4-102">StrongNameTokenFromAssembly Function</span></span>
<span data-ttu-id="5fec4-103">從指定的組件檔案建立強式名稱權杖。</span><span class="sxs-lookup"><span data-stu-id="5fec4-103">Creates a strong name token from the specified assembly file.</span></span>  
  
 <span data-ttu-id="5fec4-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="5fec4-104">This function has been deprecated.</span></span> <span data-ttu-id="5fec4-105">使用[iclrstrongname:: Strongnametokenfromassembly](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="5fec4-105">Use the [ICLRStrongName::StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fec4-106">語法</span><span class="sxs-lookup"><span data-stu-id="5fec4-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fec4-107">參數</span><span class="sxs-lookup"><span data-stu-id="5fec4-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="5fec4-108">[in]組件的可攜式執行檔 (PE) 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="5fec4-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="5fec4-109">[out]傳回的強式名稱語彙基元。</span><span class="sxs-lookup"><span data-stu-id="5fec4-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="5fec4-110">[out]大小，以位元組為單位的強式名稱語彙基元。</span><span class="sxs-lookup"><span data-stu-id="5fec4-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5fec4-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="5fec4-111">Return Value</span></span>  
 `true` <span data-ttu-id="5fec4-112">如果成功地完成;否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="5fec4-112">on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fec4-113">備註</span><span class="sxs-lookup"><span data-stu-id="5fec4-113">Remarks</span></span>  
 <span data-ttu-id="5fec4-114">強式名稱語彙基元是公開金鑰的縮短格式。</span><span class="sxs-lookup"><span data-stu-id="5fec4-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="5fec4-115">64 位元雜湊建立用來簽署組件的公開金鑰權杖。</span><span class="sxs-lookup"><span data-stu-id="5fec4-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="5fec4-116">此權杖是組件的強式名稱的一部分，而且可以讀取組件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="5fec4-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="5fec4-117">建立權杖之後，您應該呼叫[StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)函式來釋放配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="5fec4-117">After the token is created, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="5fec4-118">如果`StrongNameTokenFromAssembly`函式未順利完成，請呼叫[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函式來擷取最後一個產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="5fec4-118">If the `StrongNameTokenFromAssembly` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fec4-119">需求</span><span class="sxs-lookup"><span data-stu-id="5fec4-119">Requirements</span></span>  
 <span data-ttu-id="5fec4-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5fec4-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fec4-121">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="5fec4-121">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="5fec4-122">**LIBRARY:** 包含做為 mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5fec4-122">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 **<span data-ttu-id="5fec4-123">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="5fec4-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5fec4-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5fec4-124">See also</span></span>

- [<span data-ttu-id="5fec4-125">StrongNameTokenFromAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="5fec4-125">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="5fec4-126">StrongNameTokenFromAssemblyEx 方法</span><span class="sxs-lookup"><span data-stu-id="5fec4-126">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="5fec4-127">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="5fec4-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

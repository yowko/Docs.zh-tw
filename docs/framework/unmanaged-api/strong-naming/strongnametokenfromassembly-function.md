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
ms.openlocfilehash: 71058a1ff82335b2a341904805d06738e662c296
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798868"
---
# <a name="strongnametokenfromassembly-function"></a><span data-ttu-id="d35e0-102">StrongNameTokenFromAssembly 函式</span><span class="sxs-lookup"><span data-stu-id="d35e0-102">StrongNameTokenFromAssembly Function</span></span>
<span data-ttu-id="d35e0-103">從指定的組件檔案建立強式名稱權杖。</span><span class="sxs-lookup"><span data-stu-id="d35e0-103">Creates a strong name token from the specified assembly file.</span></span>  
  
 <span data-ttu-id="d35e0-104">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="d35e0-104">This function has been deprecated.</span></span> <span data-ttu-id="d35e0-105">請改用[ICLRStrongName：： StrongNameTokenFromAssembly](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="d35e0-105">Use the [ICLRStrongName::StrongNameTokenFromAssembly](../hosting/iclrstrongname-strongnametokenfromassembly-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d35e0-106">語法</span><span class="sxs-lookup"><span data-stu-id="d35e0-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d35e0-107">參數</span><span class="sxs-lookup"><span data-stu-id="d35e0-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="d35e0-108">在元件的可移植執行檔（PE）路徑。</span><span class="sxs-lookup"><span data-stu-id="d35e0-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="d35e0-109">脫銷傳回的強式名稱 token。</span><span class="sxs-lookup"><span data-stu-id="d35e0-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="d35e0-110">脫銷強式名稱 token 的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="d35e0-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d35e0-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="d35e0-111">Return Value</span></span>  
 <span data-ttu-id="d35e0-112">`true`成功完成時;否則為`false`。</span><span class="sxs-lookup"><span data-stu-id="d35e0-112">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d35e0-113">備註</span><span class="sxs-lookup"><span data-stu-id="d35e0-113">Remarks</span></span>  
 <span data-ttu-id="d35e0-114">強式名稱 token 是公用金鑰的縮寫格式。</span><span class="sxs-lookup"><span data-stu-id="d35e0-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="d35e0-115">Token 是從用來簽署元件的公開金鑰所建立的64位雜湊。</span><span class="sxs-lookup"><span data-stu-id="d35e0-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="d35e0-116">Token 是元件強式名稱的一部分，而且可以從元件中繼資料讀取。</span><span class="sxs-lookup"><span data-stu-id="d35e0-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="d35e0-117">建立權杖之後，您應該呼叫[StrongNameFreeBuffer](strongnamefreebuffer-function.md)函式以釋放已配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="d35e0-117">After the token is created, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="d35e0-118">如果 `StrongNameTokenFromAssembly` 函式未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式，以取出最後產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d35e0-118">If the `StrongNameTokenFromAssembly` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d35e0-119">需求</span><span class="sxs-lookup"><span data-stu-id="d35e0-119">Requirements</span></span>  
 <span data-ttu-id="d35e0-120">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d35e0-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d35e0-121">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="d35e0-121">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="d35e0-122">**LIBRARY:** 包含為 mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d35e0-122">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="d35e0-123">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d35e0-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d35e0-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d35e0-124">See also</span></span>

- [<span data-ttu-id="d35e0-125">StrongNameTokenFromAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="d35e0-125">StrongNameTokenFromAssembly Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="d35e0-126">StrongNameTokenFromAssemblyEx 方法</span><span class="sxs-lookup"><span data-stu-id="d35e0-126">StrongNameTokenFromAssemblyEx Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="d35e0-127">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="d35e0-127">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)

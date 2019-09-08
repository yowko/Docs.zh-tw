---
title: StrongNameSignatureVerificationEx 函式
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx function [.NET Framework strong naming]
ms.assetid: cfe4b634-18bf-44b8-9773-d94fb7e8a480
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08247c1ec5b868055e4836b3c0fb520a536374e8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798924"
---
# <a name="strongnamesignatureverificationex-function"></a><span data-ttu-id="d4871-102">StrongNameSignatureVerificationEx 函式</span><span class="sxs-lookup"><span data-stu-id="d4871-102">StrongNameSignatureVerificationEx Function</span></span>
<span data-ttu-id="d4871-103">取得指出位於指定路徑的組件資訊清單是否包含強式名稱簽章的值。</span><span class="sxs-lookup"><span data-stu-id="d4871-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
 <span data-ttu-id="d4871-104">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="d4871-104">This function has been deprecated.</span></span> <span data-ttu-id="d4871-105">請改用[ICLRStrongName：： StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="d4871-105">Use the [ICLRStrongName::StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4871-106">語法</span><span class="sxs-lookup"><span data-stu-id="d4871-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4871-107">參數</span><span class="sxs-lookup"><span data-stu-id="d4871-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="d4871-108">在要驗證之元件的可攜式可執行檔（.exe 或 .dll）的路徑。</span><span class="sxs-lookup"><span data-stu-id="d4871-108">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="d4871-109">在表示執行驗證，即使需要覆寫登錄設定也一樣; `false`否則為。 `true`</span><span class="sxs-lookup"><span data-stu-id="d4871-109">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="d4871-110">脫銷如果已驗證強式名稱簽章，則為`false`，否則為。 `true`</span><span class="sxs-lookup"><span data-stu-id="d4871-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="d4871-111">`pfWasVerified`如果驗證因為登錄`false`設定而成功，也會設定為。</span><span class="sxs-lookup"><span data-stu-id="d4871-111">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4871-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="d4871-112">Return Value</span></span>  
 <span data-ttu-id="d4871-113">`true`如果驗證成功，則為，否則為`false`。</span><span class="sxs-lookup"><span data-stu-id="d4871-113">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4871-114">備註</span><span class="sxs-lookup"><span data-stu-id="d4871-114">Remarks</span></span>  
 <span data-ttu-id="d4871-115">`StrongNameSignatureVerificationEx`提供的功能類似于[StrongNameSignatureVerification](strongnamesignatureverification-function.md)函數。</span><span class="sxs-lookup"><span data-stu-id="d4871-115">`StrongNameSignatureVerificationEx` provides a capability similar to the [StrongNameSignatureVerification](strongnamesignatureverification-function.md) function.</span></span> <span data-ttu-id="d4871-116">不過，的第二個輸入參數和輸出參數`StrongNameSignatureVerificationEx`的類型`BOOLEAN`是，而`DWORD`不是。</span><span class="sxs-lookup"><span data-stu-id="d4871-116">However, the second input parameter and the output parameter for `StrongNameSignatureVerificationEx` are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4871-117">需求</span><span class="sxs-lookup"><span data-stu-id="d4871-117">Requirements</span></span>  
 <span data-ttu-id="d4871-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d4871-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4871-119">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="d4871-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="d4871-120">**LIBRARY:** 包含為 mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d4871-120">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="d4871-121">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4871-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4871-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4871-122">See also</span></span>

- [<span data-ttu-id="d4871-123">StrongNameSignatureVerificationEx 方法</span><span class="sxs-lookup"><span data-stu-id="d4871-123">StrongNameSignatureVerificationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="d4871-124">StrongNameSignatureVerification 方法</span><span class="sxs-lookup"><span data-stu-id="d4871-124">StrongNameSignatureVerification Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="d4871-125">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="d4871-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)

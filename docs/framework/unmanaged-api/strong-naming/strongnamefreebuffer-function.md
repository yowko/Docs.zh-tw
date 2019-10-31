---
title: StrongNameFreeBuffer 函式
ms.date: 03/30/2017
api_name:
- StrongNameFreeBuffer
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer function [.NET Framework strong naming]
ms.assetid: eda21ecf-4734-4f92-aaba-9f34884385db
topic_type:
- apiref
ms.openlocfilehash: 11821acbeeb04ae09464eb0e032b9bf387914168
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095055"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="9e540-102">StrongNameFreeBuffer 函式</span><span class="sxs-lookup"><span data-stu-id="9e540-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="9e540-103">釋放使用對強式名稱函式 (例如 [StrongNameGetPublicKey](strongnamegetpublickey-function.md)、[StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md) 或 [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)) 的上一個呼叫所配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="9e540-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="9e540-104">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="9e540-104">This function has been deprecated.</span></span> <span data-ttu-id="9e540-105">請改用[ICLRStrongName：： StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="9e540-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e540-106">語法</span><span class="sxs-lookup"><span data-stu-id="9e540-106">Syntax</span></span>  
  
```cpp  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e540-107">參數</span><span class="sxs-lookup"><span data-stu-id="9e540-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="9e540-108">在要釋放之記憶體的指標。</span><span class="sxs-lookup"><span data-stu-id="9e540-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e540-109">需求</span><span class="sxs-lookup"><span data-stu-id="9e540-109">Requirements</span></span>  
 <span data-ttu-id="9e540-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9e540-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e540-111">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="9e540-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="9e540-112">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9e540-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9e540-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e540-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e540-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="9e540-114">See also</span></span>

- [<span data-ttu-id="9e540-115">StrongNameFreeBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="9e540-115">StrongNameFreeBuffer Method</span></span>](../hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="9e540-116">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="9e540-116">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)

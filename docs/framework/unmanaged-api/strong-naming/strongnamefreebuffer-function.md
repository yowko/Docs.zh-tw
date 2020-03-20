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
ms.openlocfilehash: 50e3cc6e677de45be9256a2a818ebd6ed7d8b843
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176912"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="cbdb3-102">StrongNameFreeBuffer 函式</span><span class="sxs-lookup"><span data-stu-id="cbdb3-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="cbdb3-103">釋放使用對強式名稱函式 (例如 [StrongNameGetPublicKey](strongnamegetpublickey-function.md)、[StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md) 或 [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)) 的上一個呼叫所配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="cbdb3-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="cbdb3-104">此函數已被棄用。</span><span class="sxs-lookup"><span data-stu-id="cbdb3-104">This function has been deprecated.</span></span> <span data-ttu-id="cbdb3-105">改用[ICLR 強式名稱：：強式名稱自由緩衝區](../hosting/iclrstrongname-strongnamefreebuffer-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="cbdb3-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbdb3-106">語法</span><span class="sxs-lookup"><span data-stu-id="cbdb3-106">Syntax</span></span>  
  
```cpp  
VOID StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbdb3-107">參數</span><span class="sxs-lookup"><span data-stu-id="cbdb3-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="cbdb3-108">[在]指向要釋放的記憶體的指標。</span><span class="sxs-lookup"><span data-stu-id="cbdb3-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbdb3-109">需求</span><span class="sxs-lookup"><span data-stu-id="cbdb3-109">Requirements</span></span>  
 <span data-ttu-id="cbdb3-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cbdb3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbdb3-111">**標題：** 強式名稱.h</span><span class="sxs-lookup"><span data-stu-id="cbdb3-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="cbdb3-112">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="cbdb3-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cbdb3-113">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbdb3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbdb3-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbdb3-114">See also</span></span>

- [<span data-ttu-id="cbdb3-115">StrongNameFreeBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="cbdb3-115">StrongNameFreeBuffer Method</span></span>](../hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="cbdb3-116">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="cbdb3-116">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)

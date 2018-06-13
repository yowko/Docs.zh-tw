---
title: FExecuteInAppDomainCallback 函式指標
ms.date: 03/30/2017
api_name:
- FExecuteInAppDomainCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FExecuteInAppDomainCallback
helpviewer_keywords:
- FExecuteInAppDomainCallback function pointer [.NET Framework hosting]
ms.assetid: 2709f18f-3eee-497f-bc33-3ab7a485599b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c3cafe3a8912702a093f9df7234112c0057b440
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431296"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="9e9e2-102">FExecuteInAppDomainCallback 函式指標</span><span class="sxs-lookup"><span data-stu-id="9e9e2-102">FExecuteInAppDomainCallback Function Pointer</span></span>
<span data-ttu-id="9e9e2-103">指向由通用語言執行平台 (CLR) 執行 managed 程式碼呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="9e9e2-103">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="9e9e2-104">此函式指標中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9e9e2-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e9e2-105">語法</span><span class="sxs-lookup"><span data-stu-id="9e9e2-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e9e2-106">參數</span><span class="sxs-lookup"><span data-stu-id="9e9e2-106">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="9e9e2-107">[in]其中包含要執行的 managed 程式碼不透明呼叫端配置的記憶體指標。</span><span class="sxs-lookup"><span data-stu-id="9e9e2-107">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="9e9e2-108">配置和存留期這個記憶體是由呼叫端 (也就是 CLR) 控制。</span><span class="sxs-lookup"><span data-stu-id="9e9e2-108">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="9e9e2-109">這不是 CLR managed 堆積的記憶體。</span><span class="sxs-lookup"><span data-stu-id="9e9e2-109">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e9e2-110">需求</span><span class="sxs-lookup"><span data-stu-id="9e9e2-110">Requirements</span></span>  
 <span data-ttu-id="9e9e2-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9e9e2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e9e2-112">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9e9e2-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e9e2-113">**程式庫：** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="9e9e2-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="9e9e2-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e9e2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e9e2-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e9e2-115">See Also</span></span>  
 [<span data-ttu-id="9e9e2-116">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="9e9e2-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

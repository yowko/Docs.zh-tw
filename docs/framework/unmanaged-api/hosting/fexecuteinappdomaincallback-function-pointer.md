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
ms.openlocfilehash: 970468bc2f50144c62c6e3cbcf9c00c2027f7663
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138173"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="f3bb5-102">FExecuteInAppDomainCallback 函式指標</span><span class="sxs-lookup"><span data-stu-id="f3bb5-102">FExecuteInAppDomainCallback Function Pointer</span></span>
<span data-ttu-id="f3bb5-103">指向 common language runtime （CLR）所呼叫的函式，以執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="f3bb5-103">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="f3bb5-104">這個函式指標在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="f3bb5-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3bb5-105">語法</span><span class="sxs-lookup"><span data-stu-id="f3bb5-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3bb5-106">參數</span><span class="sxs-lookup"><span data-stu-id="f3bb5-106">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="f3bb5-107">在不透明呼叫端配置的記憶體指標，其中包含要執行的 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="f3bb5-107">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="f3bb5-108">這個記憶體的配置和存留期是由呼叫端（也就是 CLR）所控制。</span><span class="sxs-lookup"><span data-stu-id="f3bb5-108">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="f3bb5-109">這不是 CLR managed 堆積記憶體。</span><span class="sxs-lookup"><span data-stu-id="f3bb5-109">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3bb5-110">需求</span><span class="sxs-lookup"><span data-stu-id="f3bb5-110">Requirements</span></span>  
 <span data-ttu-id="f3bb5-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f3bb5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3bb5-112">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="f3bb5-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f3bb5-113">連結**庫：** Mscorwks.dll .dll</span><span class="sxs-lookup"><span data-stu-id="f3bb5-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="f3bb5-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3bb5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3bb5-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="f3bb5-115">See also</span></span>

- [<span data-ttu-id="f3bb5-116">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="f3bb5-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

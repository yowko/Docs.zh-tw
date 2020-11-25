---
title: FLockClrVersionCallback 函式指標
ms.date: 03/30/2017
api_name:
- FLockClrVersionCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FLockClrVersionCallback
helpviewer_keywords:
- FLockClrVersionCallback function pointer [.NET Framework hosting]
ms.assetid: 98a4762d-9ad2-45bd-9d03-39064a028b44
topic_type:
- apiref
ms.openlocfilehash: d18702a1bb15d2cc6c7b8577b91ed011e9bd0c05
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733668"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="4c348-102">FLockClrVersionCallback 函式指標</span><span class="sxs-lookup"><span data-stu-id="4c348-102">FLockClrVersionCallback Function Pointer</span></span>

<span data-ttu-id="4c348-103">指向 common language runtime (CLR) 呼叫的函式，以指出初始化已啟動或已完成。</span><span class="sxs-lookup"><span data-stu-id="4c348-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="4c348-104">在 .NET Framework 4 中，此函式指標已被取代。</span><span class="sxs-lookup"><span data-stu-id="4c348-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c348-105">語法</span><span class="sxs-lookup"><span data-stu-id="4c348-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="4c348-106">備註</span><span class="sxs-lookup"><span data-stu-id="4c348-106">Remarks</span></span>  

 <span data-ttu-id="4c348-107">這個函式是由主機所執行。</span><span class="sxs-lookup"><span data-stu-id="4c348-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c348-108">需求</span><span class="sxs-lookup"><span data-stu-id="4c348-108">Requirements</span></span>  

 <span data-ttu-id="4c348-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4c348-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c348-110">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="4c348-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4c348-111">連結 **庫：** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="4c348-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="4c348-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c348-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c348-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c348-113">See also</span></span>

- [<span data-ttu-id="4c348-114">LockClrVersion 函式</span><span class="sxs-lookup"><span data-stu-id="4c348-114">LockClrVersion Function</span></span>](lockclrversion-function.md)
- [<span data-ttu-id="4c348-115">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="4c348-115">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)

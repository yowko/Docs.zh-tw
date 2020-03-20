---
title: CorExitProcess 函式
ms.date: 03/30/2017
api_name:
- CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CorExitProcess
helpviewer_keywords:
- CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type:
- apiref
ms.openlocfilehash: 44578595b3cb790570c5359e714bd39c109cf1f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176457"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="31af7-102">CorExitProcess 函式</span><span class="sxs-lookup"><span data-stu-id="31af7-102">CorExitProcess Function</span></span>
<span data-ttu-id="31af7-103">關閉當前非託管進程。</span><span class="sxs-lookup"><span data-stu-id="31af7-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="31af7-104">此功能已在 .NET 框架 4 中棄用。</span><span class="sxs-lookup"><span data-stu-id="31af7-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="31af7-105">改用[ICLRMetaHost：：退出進程](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="31af7-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31af7-106">語法</span><span class="sxs-lookup"><span data-stu-id="31af7-106">Syntax</span></span>  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31af7-107">參數</span><span class="sxs-lookup"><span data-stu-id="31af7-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="31af7-108">指定進程結束代碼的整數。</span><span class="sxs-lookup"><span data-stu-id="31af7-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31af7-109">備註</span><span class="sxs-lookup"><span data-stu-id="31af7-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31af7-110">從 .NET 框架 4`CorExitProcess`開始，退出進程中的每個啟動運行時，而不僅僅是將舊 API 綁定到的運行時。</span><span class="sxs-lookup"><span data-stu-id="31af7-110">Beginning with the .NET Framework 4, `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31af7-111">需求</span><span class="sxs-lookup"><span data-stu-id="31af7-111">Requirements</span></span>  
 <span data-ttu-id="31af7-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="31af7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31af7-113">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="31af7-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="31af7-114">**庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="31af7-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31af7-115">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31af7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31af7-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31af7-116">See also</span></span>

- [<span data-ttu-id="31af7-117">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="31af7-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

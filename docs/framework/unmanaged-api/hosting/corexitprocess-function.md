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
ms.openlocfilehash: a60805e1fd78cb14835957a7afc14fe279cb20fb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616563"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="ff14e-102">CorExitProcess 函式</span><span class="sxs-lookup"><span data-stu-id="ff14e-102">CorExitProcess Function</span></span>
<span data-ttu-id="ff14e-103">關閉目前的非受控進程。</span><span class="sxs-lookup"><span data-stu-id="ff14e-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="ff14e-104">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="ff14e-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="ff14e-105">請改用[ICLRMetaHost：： ExitProcess](iclrmetahost-exitprocess-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="ff14e-105">Use the [ICLRMetaHost::ExitProcess](iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff14e-106">語法</span><span class="sxs-lookup"><span data-stu-id="ff14e-106">Syntax</span></span>  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff14e-107">參數</span><span class="sxs-lookup"><span data-stu-id="ff14e-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="ff14e-108">指定進程結束代碼的整數。</span><span class="sxs-lookup"><span data-stu-id="ff14e-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff14e-109">備註</span><span class="sxs-lookup"><span data-stu-id="ff14e-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff14e-110">從 .NET Framework 4 開始， `CorExitProcess` 會在進程中結束每個已啟動的執行時間，而不只是舊版 api 已系結的執行時間。</span><span class="sxs-lookup"><span data-stu-id="ff14e-110">Beginning with the .NET Framework 4, `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff14e-111">需求</span><span class="sxs-lookup"><span data-stu-id="ff14e-111">Requirements</span></span>  
 <span data-ttu-id="ff14e-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ff14e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff14e-113">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="ff14e-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ff14e-114">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="ff14e-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff14e-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff14e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff14e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff14e-116">See also</span></span>

- [<span data-ttu-id="ff14e-117">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="ff14e-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)

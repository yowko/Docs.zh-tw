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
api_type:
- DLLExport
f1_keywords:
- CorExitProcess
helpviewer_keywords:
- CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3e7f3208d7ac84645fa4c7ad7e0b71f6a0d3d3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429325"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="d1446-102">CorExitProcess 函式</span><span class="sxs-lookup"><span data-stu-id="d1446-102">CorExitProcess Function</span></span>
<span data-ttu-id="d1446-103">關閉目前未受管理的程序。</span><span class="sxs-lookup"><span data-stu-id="d1446-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="d1446-104">此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d1446-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="d1446-105">使用[iclrmetahost:: Exitprocess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="d1446-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1446-106">語法</span><span class="sxs-lookup"><span data-stu-id="d1446-106">Syntax</span></span>  
  
```  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1446-107">參數</span><span class="sxs-lookup"><span data-stu-id="d1446-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="d1446-108">指定處理序結束碼的整數。</span><span class="sxs-lookup"><span data-stu-id="d1446-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1446-109">備註</span><span class="sxs-lookup"><span data-stu-id="d1446-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1446-110">開頭為[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]，`CorExitProcess`結束的處理程序中，而不只是執行階段的舊版應用程式開發介面已繫結中每個已啟動執行階段。</span><span class="sxs-lookup"><span data-stu-id="d1446-110">Beginning with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1446-111">需求</span><span class="sxs-lookup"><span data-stu-id="d1446-111">Requirements</span></span>  
 <span data-ttu-id="d1446-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d1446-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1446-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d1446-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d1446-114">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d1446-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1446-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1446-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1446-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1446-116">See Also</span></span>  
 [<span data-ttu-id="d1446-117">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="d1446-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

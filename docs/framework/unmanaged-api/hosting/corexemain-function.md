---
title: "_CorExeMain 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _CorExeMain
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: _CorExeMain
helpviewer_keywords: _CorExeMain function [.NET Framework hosting]
ms.assetid: 898f76e2-16f4-4a63-b7d9-dad2d3824d8a
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f5c0909db10c7bf8e15a7af998b78e0a193a908
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corexemain-function"></a><span data-ttu-id="fcbe2-102">_CorExeMain 函式</span><span class="sxs-lookup"><span data-stu-id="fcbe2-102">_CorExeMain Function</span></span>
<span data-ttu-id="fcbe2-103">初始化 common language runtime (CLR)、 找出 managed 的進入點中可執行組件的 CLR 標頭，並開始執行。</span><span class="sxs-lookup"><span data-stu-id="fcbe2-103">Initializes the common language runtime (CLR), locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcbe2-104">語法</span><span class="sxs-lookup"><span data-stu-id="fcbe2-104">Syntax</span></span>  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="fcbe2-105">備註</span><span class="sxs-lookup"><span data-stu-id="fcbe2-105">Remarks</span></span>  
 <span data-ttu-id="fcbe2-106">在處理序所建立的 managed 可執行組件載入器會呼叫此函式。</span><span class="sxs-lookup"><span data-stu-id="fcbe2-106">This function is called by the loader in processes created from managed executable assemblies.</span></span> <span data-ttu-id="fcbe2-107">DLL 的組件載入器會呼叫[_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="fcbe2-107">For DLL assemblies, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="fcbe2-108">作業系統載入器會呼叫這個方法，不論映像檔中指定的進入點。</span><span class="sxs-lookup"><span data-stu-id="fcbe2-108">The operating system loader calls this method regardless of the entry point specified in the image file.</span></span>  
  
 <span data-ttu-id="fcbe2-109">在 Windows 98、 Windows ME、 Windows NT 和 Windows 2000`_CorExeMain`間接透過一個修復作業系統載入器在呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="fcbe2-109">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorExeMain` function is called indirectly through a fixup in the operating system loader.</span></span> <span data-ttu-id="fcbe2-110">在所有其他 Windows 版本，它會呼叫直接由作業系統載入器。</span><span class="sxs-lookup"><span data-stu-id="fcbe2-110">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="fcbe2-111">如需詳細資訊，請參閱中的 < 備註 > 一節[_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)主題。</span><span class="sxs-lookup"><span data-stu-id="fcbe2-111">For additional information, see the Remarks section in the [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcbe2-112">需求</span><span class="sxs-lookup"><span data-stu-id="fcbe2-112">Requirements</span></span>  
 <span data-ttu-id="fcbe2-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fcbe2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcbe2-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fcbe2-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fcbe2-115">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fcbe2-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fcbe2-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcbe2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcbe2-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="fcbe2-117">See Also</span></span>  
 [<span data-ttu-id="fcbe2-118">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="fcbe2-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

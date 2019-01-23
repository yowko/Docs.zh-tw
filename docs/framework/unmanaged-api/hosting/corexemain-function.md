---
title: _CorExeMain 函式
ms.date: 03/30/2017
api_name:
- _CorExeMain
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain
helpviewer_keywords:
- _CorExeMain function [.NET Framework hosting]
ms.assetid: 898f76e2-16f4-4a63-b7d9-dad2d3824d8a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c6887d390ded1846e201711c9278663b9ff2888
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520257"
---
# <a name="corexemain-function"></a><span data-ttu-id="949d2-102">_CorExeMain 函式</span><span class="sxs-lookup"><span data-stu-id="949d2-102">_CorExeMain Function</span></span>
<span data-ttu-id="949d2-103">初始化 common language runtime (CLR)，在可執行組件的 CLR 標頭，尋找 managed 的進入點，並開始執行。</span><span class="sxs-lookup"><span data-stu-id="949d2-103">Initializes the common language runtime (CLR), locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="949d2-104">語法</span><span class="sxs-lookup"><span data-stu-id="949d2-104">Syntax</span></span>  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="949d2-105">備註</span><span class="sxs-lookup"><span data-stu-id="949d2-105">Remarks</span></span>  
 <span data-ttu-id="949d2-106">從受管理的可執行組件建立的處理序中載入器會呼叫此函式。</span><span class="sxs-lookup"><span data-stu-id="949d2-106">This function is called by the loader in processes created from managed executable assemblies.</span></span> <span data-ttu-id="949d2-107">DLL 的組件，載入器會呼叫[_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="949d2-107">For DLL assemblies, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="949d2-108">作業系統載入器會呼叫這個方法，不論映像檔中指定的進入點。</span><span class="sxs-lookup"><span data-stu-id="949d2-108">The operating system loader calls this method regardless of the entry point specified in the image file.</span></span>  
  
 <span data-ttu-id="949d2-109">在 Windows 98、 Windows ME、 Windows NT 和 Windows 2000`_CorExeMain`修復作業系統載入器中透過間接呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="949d2-109">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorExeMain` function is called indirectly through a fixup in the operating system loader.</span></span> <span data-ttu-id="949d2-110">在所有其他 Windows 版本，它會呼叫直接由作業系統載入器。</span><span class="sxs-lookup"><span data-stu-id="949d2-110">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="949d2-111">如需詳細資訊，請參閱 < 備註 > 一節[_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)主題。</span><span class="sxs-lookup"><span data-stu-id="949d2-111">For additional information, see the Remarks section in the [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="949d2-112">需求</span><span class="sxs-lookup"><span data-stu-id="949d2-112">Requirements</span></span>  
 <span data-ttu-id="949d2-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="949d2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="949d2-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="949d2-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="949d2-115">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="949d2-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="949d2-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="949d2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="949d2-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="949d2-117">See also</span></span>
- [<span data-ttu-id="949d2-118">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="949d2-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

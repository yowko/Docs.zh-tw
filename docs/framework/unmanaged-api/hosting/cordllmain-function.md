---
title: _CorDllMain 函式
ms.date: 03/30/2017
api_name:
- _CorDllMain
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorDllMain
helpviewer_keywords:
- _CorDllMain function [.NET Framework hosting]
ms.assetid: bc7b51cf-39d3-48ec-a5cb-2f179fbefff8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5d541f834e829305fa2b091c45d0dc8f387bb55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431665"
---
# <a name="cordllmain-function"></a><span data-ttu-id="a7153-102">_CorDllMain 函式</span><span class="sxs-lookup"><span data-stu-id="a7153-102">_CorDllMain Function</span></span>
<span data-ttu-id="a7153-103">初始化 common language runtime (CLR)、 找出 managed 的進入點 DLL 組件的 CLR 標頭，並開始執行。</span><span class="sxs-lookup"><span data-stu-id="a7153-103">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7153-104">語法</span><span class="sxs-lookup"><span data-stu-id="a7153-104">Syntax</span></span>  
  
```  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7153-105">參數</span><span class="sxs-lookup"><span data-stu-id="a7153-105">Parameters</span></span>  
 `hInst`  
 <span data-ttu-id="a7153-106">[in]載入模組的執行個體控制代碼。</span><span class="sxs-lookup"><span data-stu-id="a7153-106">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="a7153-107">[in]指出為什麼稱為 DLL 進入點函式。</span><span class="sxs-lookup"><span data-stu-id="a7153-107">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="a7153-108">這個參數可以是下列值之一： DLL_PROCESS_ATTACH、 DLL_THREAD_ATTACH、 DLL_THREAD_ATTACH 或 DLL_PROCESS_DETACH。</span><span class="sxs-lookup"><span data-stu-id="a7153-108">This parameter can be one of the following values: DLL_PROCESS_ATTACH, DLL_THREAD_ATTACH, DLL_THREAD_ATTACH, or DLL_PROCESS_DETACH.</span></span> <span data-ttu-id="a7153-109">如需這些值的描述，請參閱`DllMain`Platform SDK 中的文件。</span><span class="sxs-lookup"><span data-stu-id="a7153-109">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="a7153-110">[in]未使用。</span><span class="sxs-lookup"><span data-stu-id="a7153-110">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7153-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="a7153-111">Return Value</span></span>  
 <span data-ttu-id="a7153-112">這個方法會傳回`true`成功和`false`如果發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="a7153-112">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7153-113">備註</span><span class="sxs-lookup"><span data-stu-id="a7153-113">Remarks</span></span>  
 <span data-ttu-id="a7153-114">作業系統載入器會呼叫此函數的 DLL 的組件。</span><span class="sxs-lookup"><span data-stu-id="a7153-114">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="a7153-115">可執行的組件，載入器會呼叫[_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="a7153-115">For executable assemblies, the loader calls the [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="a7153-116">作業系統載入器會呼叫這個方法，不論 DLL 檔案中指定的進入點。</span><span class="sxs-lookup"><span data-stu-id="a7153-116">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
 <span data-ttu-id="a7153-117">在 Windows 98、 Windows ME、 Windows NT 和 Windows 2000`_CorDllMain`函式間接透過呼叫 fixupin 作業系統載入器。</span><span class="sxs-lookup"><span data-stu-id="a7153-117">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorDllMain` function is called indirectly through a fixupin the operating system loader.</span></span> <span data-ttu-id="a7153-118">在所有其他 Windows 版本，它會呼叫直接由作業系統載入器。</span><span class="sxs-lookup"><span data-stu-id="a7153-118">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="a7153-119">如需詳細資訊，請參閱中的 < 備註 > 一節[_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)主題。</span><span class="sxs-lookup"><span data-stu-id="a7153-119">For additional information, see the Remarks section in the [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7153-120">需求</span><span class="sxs-lookup"><span data-stu-id="a7153-120">Requirements</span></span>  
 <span data-ttu-id="a7153-121">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a7153-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7153-122">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a7153-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a7153-123">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a7153-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a7153-124">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7153-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7153-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7153-125">See Also</span></span>  
 [<span data-ttu-id="a7153-126">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="a7153-126">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

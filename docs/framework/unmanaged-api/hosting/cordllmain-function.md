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
ms.openlocfilehash: c509f475d5bf0105ece9791ee3e51d21c298a31f
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679303"
---
# <a name="cordllmain-function"></a><span data-ttu-id="35fd3-102">\_CorDllMain 函式</span><span class="sxs-lookup"><span data-stu-id="35fd3-102">\_CorDllMain Function</span></span>

<span data-ttu-id="35fd3-103">初始化 common language runtime (CLR)、 在 DLL 組件的 CLR 標頭，尋找 managed 的進入點，並開始執行。</span><span class="sxs-lookup"><span data-stu-id="35fd3-103">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35fd3-104">語法</span><span class="sxs-lookup"><span data-stu-id="35fd3-104">Syntax</span></span>  
  
```  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35fd3-105">參數</span><span class="sxs-lookup"><span data-stu-id="35fd3-105">Parameters</span></span>  
 `hInst`  
 <span data-ttu-id="35fd3-106">[in]載入模組的執行個體控制代碼。</span><span class="sxs-lookup"><span data-stu-id="35fd3-106">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="35fd3-107">[in]指出為什麼稱為 DLL 進入點函式。</span><span class="sxs-lookup"><span data-stu-id="35fd3-107">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="35fd3-108">這個參數可以是下列值之一：DLL\_PROCESS_ATTACH、 DLL\_執行緒\_附加、 DLL\_執行緒\_ATTACH 或 DLL\_程序\_卸離。</span><span class="sxs-lookup"><span data-stu-id="35fd3-108">This parameter can be one of the following values: DLL\_PROCESS_ATTACH, DLL\_THREAD\_ATTACH, DLL\_THREAD\_ATTACH, or DLL\_PROCESS\_DETACH.</span></span> <span data-ttu-id="35fd3-109">如需這些值的描述，請參閱`DllMain`平台 SDK 中的文件。</span><span class="sxs-lookup"><span data-stu-id="35fd3-109">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="35fd3-110">[in]未使用。</span><span class="sxs-lookup"><span data-stu-id="35fd3-110">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="35fd3-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="35fd3-111">Return Value</span></span>  
 <span data-ttu-id="35fd3-112">這個方法會傳回`true`成功和`false`發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="35fd3-112">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35fd3-113">備註</span><span class="sxs-lookup"><span data-stu-id="35fd3-113">Remarks</span></span>  
 <span data-ttu-id="35fd3-114">作業系統載入器會呼叫此函數的 DLL 組件。</span><span class="sxs-lookup"><span data-stu-id="35fd3-114">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="35fd3-115">針對可執行檔的組件，載入器會呼叫[ \_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="35fd3-115">For executable assemblies, the loader calls the [\_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="35fd3-116">作業系統載入器會呼叫這個方法，不論在 DLL 檔案中指定的進入點。</span><span class="sxs-lookup"><span data-stu-id="35fd3-116">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
<span data-ttu-id="35fd3-117">`_CorDllMain`直接由作業系統載入器呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="35fd3-117">The `_CorDllMain` function is called directly by the operating system loader.</span></span>
  
 <span data-ttu-id="35fd3-118">如需詳細資訊，請參閱 < 備註 > 一節[ \_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)主題。</span><span class="sxs-lookup"><span data-stu-id="35fd3-118">For additional information, see the Remarks section in the [\_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35fd3-119">需求</span><span class="sxs-lookup"><span data-stu-id="35fd3-119">Requirements</span></span>  

 <span data-ttu-id="35fd3-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="35fd3-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35fd3-121">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="35fd3-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="35fd3-122">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="35fd3-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="35fd3-123">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35fd3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35fd3-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35fd3-124">See also</span></span>

- [<span data-ttu-id="35fd3-125">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="35fd3-125">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

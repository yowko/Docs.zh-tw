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
ms.openlocfilehash: f60f159ab4770023cee7123b39109040243e1ccd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136970"
---
# <a name="_cordllmain-function"></a><span data-ttu-id="38947-102">\_CorDllMain 函式</span><span class="sxs-lookup"><span data-stu-id="38947-102">\_CorDllMain Function</span></span>

<span data-ttu-id="38947-103">初始化 common language runtime （CLR），尋找 DLL 元件的 CLR 標頭中的 managed 進入點，然後開始執行。</span><span class="sxs-lookup"><span data-stu-id="38947-103">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38947-104">語法</span><span class="sxs-lookup"><span data-stu-id="38947-104">Syntax</span></span>  
  
```cpp  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38947-105">參數</span><span class="sxs-lookup"><span data-stu-id="38947-105">Parameters</span></span>  
 `hInst`  
 <span data-ttu-id="38947-106">在已載入模組的實例控制碼。</span><span class="sxs-lookup"><span data-stu-id="38947-106">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="38947-107">在指出呼叫 DLL 進入點函式的原因。</span><span class="sxs-lookup"><span data-stu-id="38947-107">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="38947-108">這個參數可以是下列其中一個值： DLL\_PROCESS_ATTACH、DLL\_執行緒\_附加、DLL\_執行緒\_附加，或 DLL\_進程\_卸離。</span><span class="sxs-lookup"><span data-stu-id="38947-108">This parameter can be one of the following values: DLL\_PROCESS_ATTACH, DLL\_THREAD\_ATTACH, DLL\_THREAD\_ATTACH, or DLL\_PROCESS\_DETACH.</span></span> <span data-ttu-id="38947-109">如需這些值的說明，請參閱 Platform SDK 中的 `DllMain` 檔。</span><span class="sxs-lookup"><span data-stu-id="38947-109">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="38947-110">在未使用.</span><span class="sxs-lookup"><span data-stu-id="38947-110">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38947-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="38947-111">Return Value</span></span>  
 <span data-ttu-id="38947-112">這個方法會傳回成功的 `true`，並在發生錯誤時 `false`。</span><span class="sxs-lookup"><span data-stu-id="38947-112">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38947-113">備註</span><span class="sxs-lookup"><span data-stu-id="38947-113">Remarks</span></span>  
 <span data-ttu-id="38947-114">DLL 元件的作業系統載入器會呼叫這個函式。</span><span class="sxs-lookup"><span data-stu-id="38947-114">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="38947-115">對於可執行檔元件，載入器會改為呼叫[\_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)函數。</span><span class="sxs-lookup"><span data-stu-id="38947-115">For executable assemblies, the loader calls the [\_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="38947-116">無論 DLL 檔案中指定的進入點為何，作業系統載入器都會呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="38947-116">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
<span data-ttu-id="38947-117">`_CorDllMain` 函式是由作業系統載入器直接呼叫。</span><span class="sxs-lookup"><span data-stu-id="38947-117">The `_CorDllMain` function is called directly by the operating system loader.</span></span>
  
 <span data-ttu-id="38947-118">如需詳細資訊，請參閱[\_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)主題中的「備註」一節。</span><span class="sxs-lookup"><span data-stu-id="38947-118">For additional information, see the Remarks section in the [\_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38947-119">需求</span><span class="sxs-lookup"><span data-stu-id="38947-119">Requirements</span></span>  

 <span data-ttu-id="38947-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="38947-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38947-121">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="38947-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="38947-122">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="38947-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="38947-123">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38947-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38947-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="38947-124">See also</span></span>

- [<span data-ttu-id="38947-125">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="38947-125">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

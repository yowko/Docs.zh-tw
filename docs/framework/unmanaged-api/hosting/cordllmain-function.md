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
ms.openlocfilehash: 1b3ebcabc66ee7ca29245bb02d958be311bc65fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673692"
---
# <a name="_cordllmain-function"></a><span data-ttu-id="d2456-102">\_CorDllMain 函式</span><span class="sxs-lookup"><span data-stu-id="d2456-102">\_CorDllMain Function</span></span>

<span data-ttu-id="d2456-103">初始化 common language runtime (CLR) 、找出 DLL 元件的 CLR 標頭中的 managed 進入點，然後開始執行。</span><span class="sxs-lookup"><span data-stu-id="d2456-103">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2456-104">語法</span><span class="sxs-lookup"><span data-stu-id="d2456-104">Syntax</span></span>  
  
```cpp  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2456-105">參數</span><span class="sxs-lookup"><span data-stu-id="d2456-105">Parameters</span></span>  

 `hInst`  
 <span data-ttu-id="d2456-106">在已載入模組的實例控制碼。</span><span class="sxs-lookup"><span data-stu-id="d2456-106">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="d2456-107">在指出呼叫 DLL 進入點函數的原因。</span><span class="sxs-lookup"><span data-stu-id="d2456-107">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="d2456-108">這個參數可以是下列其中一個值： DLL \_ PROCESS_ATTACH、dll \_ 執行緒 \_ 附加、dll \_ 執行緒 \_ 附加或 dll 進程卸 \_ \_ 離。</span><span class="sxs-lookup"><span data-stu-id="d2456-108">This parameter can be one of the following values: DLL\_PROCESS_ATTACH, DLL\_THREAD\_ATTACH, DLL\_THREAD\_ATTACH, or DLL\_PROCESS\_DETACH.</span></span> <span data-ttu-id="d2456-109">如需這些值的說明，請參閱 `DllMain` PLATFORM SDK 中的檔。</span><span class="sxs-lookup"><span data-stu-id="d2456-109">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="d2456-110">在閒置。</span><span class="sxs-lookup"><span data-stu-id="d2456-110">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2456-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="d2456-111">Return Value</span></span>  

 <span data-ttu-id="d2456-112">`true`如果發生錯誤，這個方法 `false` 會傳回成功。</span><span class="sxs-lookup"><span data-stu-id="d2456-112">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2456-113">備註</span><span class="sxs-lookup"><span data-stu-id="d2456-113">Remarks</span></span>  

 <span data-ttu-id="d2456-114">DLL 元件的作業系統載入器會呼叫這個函數。</span><span class="sxs-lookup"><span data-stu-id="d2456-114">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="d2456-115">針對可執行檔元件，載入器會改為呼叫[ \_ CorExeMain](corexemain-function.md)函數。</span><span class="sxs-lookup"><span data-stu-id="d2456-115">For executable assemblies, the loader calls the [\_CorExeMain](corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="d2456-116">作業系統載入器會呼叫這個方法，不論 DLL 檔中指定的進入點為何。</span><span class="sxs-lookup"><span data-stu-id="d2456-116">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
<span data-ttu-id="d2456-117">`_CorDllMain`作業系統載入器會直接呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="d2456-117">The `_CorDllMain` function is called directly by the operating system loader.</span></span>
  
 <span data-ttu-id="d2456-118">如需詳細資訊，請參閱[ \_ CorValidateImage](corvalidateimage-function.md)主題中的「備註」一節。</span><span class="sxs-lookup"><span data-stu-id="d2456-118">For additional information, see the Remarks section in the [\_CorValidateImage](corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2456-119">需求</span><span class="sxs-lookup"><span data-stu-id="d2456-119">Requirements</span></span>  

 <span data-ttu-id="d2456-120">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d2456-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2456-121">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="d2456-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d2456-122">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="d2456-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d2456-123">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2456-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2456-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2456-124">See also</span></span>

- [<span data-ttu-id="d2456-125">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="d2456-125">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)

---
title: _CorExeMain2 函式
ms.date: 03/30/2017
api_name:
- _CorExeMain2
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain2
helpviewer_keywords:
- _CorExeMain2 function [.NET Framework hosting]
ms.assetid: 72ea68b4-689f-4733-9416-9664b75e8892
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 573336b32040f44ff1b59fcbb75b59aa00976b5c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430175"
---
# <a name="corexemain2-function"></a><span data-ttu-id="e009f-102">_CorExeMain2 函式</span><span class="sxs-lookup"><span data-stu-id="e009f-102">_CorExeMain2 Function</span></span>
<span data-ttu-id="e009f-103">指定記憶體對應程式碼中執行的進入點。</span><span class="sxs-lookup"><span data-stu-id="e009f-103">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="e009f-104">作業系統載入器會呼叫此函式。</span><span class="sxs-lookup"><span data-stu-id="e009f-104">This function is called by the operating system loader.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e009f-105">語法</span><span class="sxs-lookup"><span data-stu-id="e009f-105">Syntax</span></span>  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e009f-106">參數</span><span class="sxs-lookup"><span data-stu-id="e009f-106">Parameters</span></span>  
 `pUnmappedPE`  
 <span data-ttu-id="e009f-107">[in]記憶體對應的程式碼之指標。</span><span class="sxs-lookup"><span data-stu-id="e009f-107">[in] A pointer to the memory-mapped code.</span></span>  
  
 `cUnmappedPE`  
 <span data-ttu-id="e009f-108">[in]項目數`pUnmappedPE`可以保存。</span><span class="sxs-lookup"><span data-stu-id="e009f-108">[in] The number of elements `pUnmappedPE` can hold.</span></span>  
  
 `pImageNameIn`  
 <span data-ttu-id="e009f-109">[in]可執行檔映像的名稱指標。</span><span class="sxs-lookup"><span data-stu-id="e009f-109">[in] A pointer to the name of the executable image.</span></span>  
  
 `pLoadersFileName`  
 <span data-ttu-id="e009f-110">[in]載入器檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="e009f-110">[in] The name of the loader file.</span></span>  
  
 `pCmdLine`  
 <span data-ttu-id="e009f-111">[in]命令列參數，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="e009f-111">[in] Command-line parameters, if any.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e009f-112">需求</span><span class="sxs-lookup"><span data-stu-id="e009f-112">Requirements</span></span>  
 <span data-ttu-id="e009f-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e009f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e009f-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e009f-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e009f-115">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e009f-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e009f-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e009f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e009f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e009f-117">See Also</span></span>  
 [<span data-ttu-id="e009f-118">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="e009f-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

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
ms.openlocfilehash: a3fb9d87b6433d46dad081619e0692a42219408d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673615"
---
# <a name="_corexemain2-function"></a><span data-ttu-id="1b8d6-102">_CorExeMain2 函式</span><span class="sxs-lookup"><span data-stu-id="1b8d6-102">_CorExeMain2 Function</span></span>

<span data-ttu-id="1b8d6-103">執行指定之記憶體對應程式碼中的進入點。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-103">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="1b8d6-104">作業系統載入器會呼叫這個函式。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-104">This function is called by the operating system loader.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b8d6-105">語法</span><span class="sxs-lookup"><span data-stu-id="1b8d6-105">Syntax</span></span>  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b8d6-106">參數</span><span class="sxs-lookup"><span data-stu-id="1b8d6-106">Parameters</span></span>  

 `pUnmappedPE`  
 <span data-ttu-id="1b8d6-107">在記憶體對應程式碼的指標。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-107">[in] A pointer to the memory-mapped code.</span></span>  
  
 `cUnmappedPE`  
 <span data-ttu-id="1b8d6-108">在元素數目 `pUnmappedPE` 可以保留。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-108">[in] The number of elements `pUnmappedPE` can hold.</span></span>  
  
 `pImageNameIn`  
 <span data-ttu-id="1b8d6-109">在可執行檔映射名稱的指標。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-109">[in] A pointer to the name of the executable image.</span></span>  
  
 `pLoadersFileName`  
 <span data-ttu-id="1b8d6-110">在載入器檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-110">[in] The name of the loader file.</span></span>  
  
 `pCmdLine`  
 <span data-ttu-id="1b8d6-111">在命令列參數（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-111">[in] Command-line parameters, if any.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b8d6-112">需求</span><span class="sxs-lookup"><span data-stu-id="1b8d6-112">Requirements</span></span>  

 <span data-ttu-id="1b8d6-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1b8d6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b8d6-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="1b8d6-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1b8d6-115">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="1b8d6-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1b8d6-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b8d6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b8d6-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b8d6-117">See also</span></span>

- [<span data-ttu-id="1b8d6-118">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="1b8d6-118">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)

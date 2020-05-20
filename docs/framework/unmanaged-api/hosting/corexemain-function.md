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
ms.openlocfilehash: 935ac478fb966315e81fdcc004761038b28e3178
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616586"
---
# <a name="_corexemain-function"></a><span data-ttu-id="70e15-102">_CorExeMain 函式</span><span class="sxs-lookup"><span data-stu-id="70e15-102">_CorExeMain Function</span></span>
<span data-ttu-id="70e15-103">初始化 common language runtime （CLR），尋找可執行元件的 CLR 標頭中的 managed 進入點，然後開始執行。</span><span class="sxs-lookup"><span data-stu-id="70e15-103">Initializes the common language runtime (CLR), locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70e15-104">語法</span><span class="sxs-lookup"><span data-stu-id="70e15-104">Syntax</span></span>  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="70e15-105">備註</span><span class="sxs-lookup"><span data-stu-id="70e15-105">Remarks</span></span>  
 <span data-ttu-id="70e15-106">此函式是由 managed 可執行元件所建立之進程中的載入器所呼叫。</span><span class="sxs-lookup"><span data-stu-id="70e15-106">This function is called by the loader in processes created from managed executable assemblies.</span></span> <span data-ttu-id="70e15-107">對於 DLL 元件，載入器會改為呼叫[_CorDllMain](cordllmain-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="70e15-107">For DLL assemblies, the loader calls the [_CorDllMain](cordllmain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="70e15-108">無論影像檔案中指定的進入點為何，作業系統載入器都會呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="70e15-108">The operating system loader calls this method regardless of the entry point specified in the image file.</span></span>  
  
 <span data-ttu-id="70e15-109">在 Windows 98、Windows ME、Windows NT 和 Windows 2000 中，函式 `_CorExeMain` 會透過作業系統載入器中的修復間接呼叫。</span><span class="sxs-lookup"><span data-stu-id="70e15-109">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorExeMain` function is called indirectly through a fixup in the operating system loader.</span></span> <span data-ttu-id="70e15-110">在所有其他版本的 Windows 中，作業系統載入器會直接呼叫它。</span><span class="sxs-lookup"><span data-stu-id="70e15-110">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="70e15-111">如需詳細資訊，請參閱[_CorValidateImage](corvalidateimage-function.md)主題中的「備註」一節。</span><span class="sxs-lookup"><span data-stu-id="70e15-111">For additional information, see the Remarks section in the [_CorValidateImage](corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70e15-112">需求</span><span class="sxs-lookup"><span data-stu-id="70e15-112">Requirements</span></span>  
 <span data-ttu-id="70e15-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="70e15-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70e15-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="70e15-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="70e15-115">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="70e15-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="70e15-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70e15-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70e15-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70e15-117">See also</span></span>

- [<span data-ttu-id="70e15-118">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="70e15-118">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)

---
title: CreateHistoryReader 函式
ms.date: 03/30/2017
api_name:
- CreateHistoryReader
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateHistoryReader
helpviewer_keywords:
- CreateHistoryReader function [.NET Framework fusion]
ms.assetid: 66a89acf-8c32-44c0-8787-960c99c7b3ec
topic_type:
- apiref
ms.openlocfilehash: 80979f0424469bb1d4771ad6507bb8c9d5364ab4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108601"
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="91275-102">CreateHistoryReader 函式</span><span class="sxs-lookup"><span data-stu-id="91275-102">CreateHistoryReader Function</span></span>
<span data-ttu-id="91275-103">為指定的檔案建立記錄讀取器。</span><span class="sxs-lookup"><span data-stu-id="91275-103">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91275-104">語法</span><span class="sxs-lookup"><span data-stu-id="91275-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="91275-105">參數</span><span class="sxs-lookup"><span data-stu-id="91275-105">Parameters</span></span>  
 `wzFilePath`  
 <span data-ttu-id="91275-106">在檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="91275-106">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="91275-107">脫銷成功完成時，會包含記錄讀取器的指標。</span><span class="sxs-lookup"><span data-stu-id="91275-107">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91275-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="91275-108">Return Value</span></span>  
 <span data-ttu-id="91275-109">除了下表所述的值之外，這個方法會傳回 Winerror.h 中定義的標準 COM 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="91275-109">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="91275-110">傳回碼</span><span class="sxs-lookup"><span data-stu-id="91275-110">Return code</span></span>|<span data-ttu-id="91275-111">描述</span><span class="sxs-lookup"><span data-stu-id="91275-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="91275-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="91275-112">S_OK</span></span>|<span data-ttu-id="91275-113">表示方法已順利完成。</span><span class="sxs-lookup"><span data-stu-id="91275-113">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="91275-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="91275-114">E_INVALIDARG</span></span>|<span data-ttu-id="91275-115">表示 `wzFilePath` 或 `ppHistoryReader` 設定為 null 參考。</span><span class="sxs-lookup"><span data-stu-id="91275-115">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="91275-116">需求</span><span class="sxs-lookup"><span data-stu-id="91275-116">Requirements</span></span>  
 <span data-ttu-id="91275-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="91275-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91275-118">連結**庫：** 融合 .dll</span><span class="sxs-lookup"><span data-stu-id="91275-118">**Library:** Fusion.dll</span></span>  
  
 <span data-ttu-id="91275-119">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91275-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91275-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="91275-120">See also</span></span>

- [<span data-ttu-id="91275-121">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="91275-121">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)

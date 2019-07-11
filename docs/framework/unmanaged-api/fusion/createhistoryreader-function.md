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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee30d4f32e05fab27ae70052b28d3d152594cf90
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778423"
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="eea53-102">CreateHistoryReader 函式</span><span class="sxs-lookup"><span data-stu-id="eea53-102">CreateHistoryReader Function</span></span>
<span data-ttu-id="eea53-103">建立記錄讀取器指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="eea53-103">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eea53-104">語法</span><span class="sxs-lookup"><span data-stu-id="eea53-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="eea53-105">參數</span><span class="sxs-lookup"><span data-stu-id="eea53-105">Parameters</span></span>  
 `wzFilePath`  
 <span data-ttu-id="eea53-106">[in]檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="eea53-106">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="eea53-107">[out]成功完成時，包含歷程記錄讀取器的指標。</span><span class="sxs-lookup"><span data-stu-id="eea53-107">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eea53-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="eea53-108">Return Value</span></span>  
 <span data-ttu-id="eea53-109">中所定義 WinError.h，除了下表中所述的值，這個方法會傳回標準 COM 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="eea53-109">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="eea53-110">傳回碼</span><span class="sxs-lookup"><span data-stu-id="eea53-110">Return code</span></span>|<span data-ttu-id="eea53-111">說明</span><span class="sxs-lookup"><span data-stu-id="eea53-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="eea53-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="eea53-112">S_OK</span></span>|<span data-ttu-id="eea53-113">表示已成功完成的方法。</span><span class="sxs-lookup"><span data-stu-id="eea53-113">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="eea53-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="eea53-114">E_INVALIDARG</span></span>|<span data-ttu-id="eea53-115">指出`wzFilePath`或`ppHistoryReader`設為 null 參考。</span><span class="sxs-lookup"><span data-stu-id="eea53-115">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eea53-116">需求</span><span class="sxs-lookup"><span data-stu-id="eea53-116">Requirements</span></span>  
 <span data-ttu-id="eea53-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eea53-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eea53-118">**LIBRARY:** Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="eea53-118">**Library:** Fusion.dll</span></span>  
  
 <span data-ttu-id="eea53-119">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eea53-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eea53-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eea53-120">See also</span></span>

- [<span data-ttu-id="eea53-121">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="eea53-121">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

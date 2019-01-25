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
ms.openlocfilehash: 8beb5e64b05f50ba61ced72fcdb7700d4b9f30e2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505038"
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="ee70c-102">CreateHistoryReader 函式</span><span class="sxs-lookup"><span data-stu-id="ee70c-102">CreateHistoryReader Function</span></span>
<span data-ttu-id="ee70c-103">建立記錄讀取器指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="ee70c-103">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee70c-104">語法</span><span class="sxs-lookup"><span data-stu-id="ee70c-104">Syntax</span></span>  
  
```  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ee70c-105">參數</span><span class="sxs-lookup"><span data-stu-id="ee70c-105">Parameters</span></span>  
 `wzFilePath`  
 <span data-ttu-id="ee70c-106">[in]檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="ee70c-106">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="ee70c-107">[out]成功完成時，包含歷程記錄讀取器的指標。</span><span class="sxs-lookup"><span data-stu-id="ee70c-107">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ee70c-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="ee70c-108">Return Value</span></span>  
 <span data-ttu-id="ee70c-109">中所定義 WinError.h，除了下表中所述的值，這個方法會傳回標準 COM 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="ee70c-109">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="ee70c-110">傳回碼</span><span class="sxs-lookup"><span data-stu-id="ee70c-110">Return code</span></span>|<span data-ttu-id="ee70c-111">描述</span><span class="sxs-lookup"><span data-stu-id="ee70c-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="ee70c-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ee70c-112">S_OK</span></span>|<span data-ttu-id="ee70c-113">表示已成功完成的方法。</span><span class="sxs-lookup"><span data-stu-id="ee70c-113">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="ee70c-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ee70c-114">E_INVALIDARG</span></span>|<span data-ttu-id="ee70c-115">指出`wzFilePath`或`ppHistoryReader`設為 null 參考。</span><span class="sxs-lookup"><span data-stu-id="ee70c-115">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ee70c-116">需求</span><span class="sxs-lookup"><span data-stu-id="ee70c-116">Requirements</span></span>  
 <span data-ttu-id="ee70c-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ee70c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee70c-118">**程式庫：** Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="ee70c-118">**Library:** Fusion.dll</span></span>  
  
 <span data-ttu-id="ee70c-119">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee70c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee70c-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee70c-120">See also</span></span>
- [<span data-ttu-id="ee70c-121">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="ee70c-121">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

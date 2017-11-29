---
title: "CreateHistoryReader 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateHistoryReader
api_location: fusion.dll
api_type: DLLExport
f1_keywords: CreateHistoryReader
helpviewer_keywords: CreateHistoryReader function [.NET Framework fusion]
ms.assetid: 66a89acf-8c32-44c0-8787-960c99c7b3ec
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4f4b09f592a27b7d3d25b2dbe13be7e261023bf5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="82e55-102">CreateHistoryReader 函式</span><span class="sxs-lookup"><span data-stu-id="82e55-102">CreateHistoryReader Function</span></span>
<span data-ttu-id="82e55-103">建立指定的檔案歷程記錄讀取器。</span><span class="sxs-lookup"><span data-stu-id="82e55-103">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82e55-104">語法</span><span class="sxs-lookup"><span data-stu-id="82e55-104">Syntax</span></span>  
  
```  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82e55-105">參數</span><span class="sxs-lookup"><span data-stu-id="82e55-105">Parameters</span></span>  
 `wzFilePath`  
 <span data-ttu-id="82e55-106">[in]檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="82e55-106">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="82e55-107">[out]在成功完成時，包含歷程記錄讀取器的指標。</span><span class="sxs-lookup"><span data-stu-id="82e55-107">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82e55-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="82e55-108">Return Value</span></span>  
 <span data-ttu-id="82e55-109">這個方法會傳回除了下表中描述的值定義了 WinError.h，在標準的 COM 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="82e55-109">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="82e55-110">傳回碼</span><span class="sxs-lookup"><span data-stu-id="82e55-110">Return code</span></span>|<span data-ttu-id="82e55-111">描述</span><span class="sxs-lookup"><span data-stu-id="82e55-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="82e55-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="82e55-112">S_OK</span></span>|<span data-ttu-id="82e55-113">表示已成功完成的方法。</span><span class="sxs-lookup"><span data-stu-id="82e55-113">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="82e55-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="82e55-114">E_INVALIDARG</span></span>|<span data-ttu-id="82e55-115">表示`wzFilePath`或`ppHistoryReader`會設為 null 參考。</span><span class="sxs-lookup"><span data-stu-id="82e55-115">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="82e55-116">需求</span><span class="sxs-lookup"><span data-stu-id="82e55-116">Requirements</span></span>  
 <span data-ttu-id="82e55-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="82e55-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82e55-118">**程式庫：** Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="82e55-118">**Library:** Fusion.dll</span></span>  
  
 <span data-ttu-id="82e55-119">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82e55-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82e55-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82e55-120">See Also</span></span>  
 [<span data-ttu-id="82e55-121">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="82e55-121">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

---
title: "ICLRMetadataLocator::GetMetadata 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetadataLocator.GetMetadata
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRMetadataLocator::GetMetadata
helpviewer_keywords:
- GetMetadata method, ICLRMetadataLocator interface [.NET Framework debugging]
- ICLRMetadataLocator::GetMetadata method [.NET Framework debugging]
ms.assetid: 704a8893-ac56-43b4-90ea-715f38ccb40e
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8758a96464d1465d92fb17314f1e36ab8d9169c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a><span data-ttu-id="dce74-102">ICLRMetadataLocator::GetMetadata 方法</span><span class="sxs-lookup"><span data-stu-id="dce74-102">ICLRMetadataLocator::GetMetadata Method</span></span>
<span data-ttu-id="dce74-103">呼叫由 common language runtime (CLR) 資料存取服務擷取映像的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="dce74-103">Called by the common language runtime (CLR) data access services to retrieve the metadata of an image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dce74-104">語法</span><span class="sxs-lookup"><span data-stu-id="dce74-104">Syntax</span></span>  
  
```  
HRESULT GetMetadata(  
    [in]  LPCWSTR         imagePath,  
    [in]  ULONG32         imageTimestamp,  
    [in]  ULONG32         imageSize,  
    [in]  GUID*           mvid,  
    [in]  ULONG32         mdRva,  
    [in]  ULONG32         flags,  
    [in]  ULONG32         bufferSize,  
    [out, size_is(bufferSize), length_is(*dataSize)]  
          BYTE*           buffer,  
    [out] ULONG32*        dataSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dce74-105">參數</span><span class="sxs-lookup"><span data-stu-id="dce74-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="dce74-106">[in]字串，指定影像檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="dce74-106">[in] A string that specifies the path of the image file.</span></span>  
  
 `imageTimestamp`  
 <span data-ttu-id="dce74-107">[in]映像檔的時間戳記。</span><span class="sxs-lookup"><span data-stu-id="dce74-107">[in] The time stamp of the image file.</span></span>  
  
 `imageSize`  
 <span data-ttu-id="dce74-108">[in]映像檔的大小。</span><span class="sxs-lookup"><span data-stu-id="dce74-108">[in] The size of the image file.</span></span>  
  
 `mvid`  
 <span data-ttu-id="dce74-109">[in]影像的全域唯一識別項。</span><span class="sxs-lookup"><span data-stu-id="dce74-109">[in] The globally unique identifier of the image.</span></span>  
  
 `mdRva`  
 <span data-ttu-id="dce74-110">[in]相對虛擬位址 (RVA) 的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="dce74-110">[in] The relative virtual address (RVA) of the metadata.</span></span> <span data-ttu-id="dce74-111">位址是相對於映像的基底位址。</span><span class="sxs-lookup"><span data-stu-id="dce74-111">The address is relative to the image base address.</span></span>  
  
 `flags`  
 <span data-ttu-id="dce74-112">[in]保留供未來使用。</span><span class="sxs-lookup"><span data-stu-id="dce74-112">[in] Reserved for future use.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="dce74-113">[in]要放置中繼資料的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="dce74-113">[in] The size of the buffer in which to place the metadata.</span></span>  
  
 `buffer`  
 <span data-ttu-id="dce74-114">[out]要放置中繼資料緩衝區。</span><span class="sxs-lookup"><span data-stu-id="dce74-114">[out] The buffer in which to place the metadata.</span></span>  
  
 `dataSize`  
 <span data-ttu-id="dce74-115">[out]傳回中繼資料的大小。</span><span class="sxs-lookup"><span data-stu-id="dce74-115">[out] The size of the metadata that is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dce74-116">備註</span><span class="sxs-lookup"><span data-stu-id="dce74-116">Remarks</span></span>  
 <span data-ttu-id="dce74-117">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="dce74-117">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dce74-118">需求</span><span class="sxs-lookup"><span data-stu-id="dce74-118">Requirements</span></span>  
 <span data-ttu-id="dce74-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dce74-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dce74-120">**標頭：** ClrData.idl、 ClrData.h</span><span class="sxs-lookup"><span data-stu-id="dce74-120">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="dce74-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dce74-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dce74-122">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dce74-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dce74-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="dce74-123">See Also</span></span>  
 [<span data-ttu-id="dce74-124">ICLRMetadataLocator 介面</span><span class="sxs-lookup"><span data-stu-id="dce74-124">ICLRMetadataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)

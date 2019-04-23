---
title: ICLRMetadataLocator::GetMetadata 方法
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator.GetMetadata
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator::GetMetadata
helpviewer_keywords:
- GetMetadata method, ICLRMetadataLocator interface [.NET Framework debugging]
- ICLRMetadataLocator::GetMetadata method [.NET Framework debugging]
ms.assetid: 704a8893-ac56-43b4-90ea-715f38ccb40e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e677aefd5420f71867c1f11a2c9408c77d305c45
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59161370"
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a><span data-ttu-id="edb18-102">ICLRMetadataLocator::GetMetadata 方法</span><span class="sxs-lookup"><span data-stu-id="edb18-102">ICLRMetadataLocator::GetMetadata Method</span></span>
<span data-ttu-id="edb18-103">由通用語言執行平台 (CLR) 資料存取服務擷取的映像的中繼資料的呼叫。</span><span class="sxs-lookup"><span data-stu-id="edb18-103">Called by the common language runtime (CLR) data access services to retrieve the metadata of an image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edb18-104">語法</span><span class="sxs-lookup"><span data-stu-id="edb18-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="edb18-105">參數</span><span class="sxs-lookup"><span data-stu-id="edb18-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="edb18-106">[in]字串，指定影像檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="edb18-106">[in] A string that specifies the path of the image file.</span></span>  
  
 `imageTimestamp`  
 <span data-ttu-id="edb18-107">[in]影像檔的時間戳記。</span><span class="sxs-lookup"><span data-stu-id="edb18-107">[in] The time stamp of the image file.</span></span>  
  
 `imageSize`  
 <span data-ttu-id="edb18-108">[in]影像檔的大小。</span><span class="sxs-lookup"><span data-stu-id="edb18-108">[in] The size of the image file.</span></span>  
  
 `mvid`  
 <span data-ttu-id="edb18-109">[in]映像的全域唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="edb18-109">[in] The globally unique identifier of the image.</span></span>  
  
 `mdRva`  
 <span data-ttu-id="edb18-110">[in]相對虛擬位址 (RVA) 的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="edb18-110">[in] The relative virtual address (RVA) of the metadata.</span></span> <span data-ttu-id="edb18-111">此位址是相對於映像的基底位址。</span><span class="sxs-lookup"><span data-stu-id="edb18-111">The address is relative to the image base address.</span></span>  
  
 `flags`  
 <span data-ttu-id="edb18-112">[in]保留供日後使用。</span><span class="sxs-lookup"><span data-stu-id="edb18-112">[in] Reserved for future use.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="edb18-113">[in]在其中放置中繼資料的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="edb18-113">[in] The size of the buffer in which to place the metadata.</span></span>  
  
 `buffer`  
 <span data-ttu-id="edb18-114">[out]中要放置的中繼資料的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="edb18-114">[out] The buffer in which to place the metadata.</span></span>  
  
 `dataSize`  
 <span data-ttu-id="edb18-115">[out]傳回中繼資料的大小。</span><span class="sxs-lookup"><span data-stu-id="edb18-115">[out] The size of the metadata that is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edb18-116">備註</span><span class="sxs-lookup"><span data-stu-id="edb18-116">Remarks</span></span>  
 <span data-ttu-id="edb18-117">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="edb18-117">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edb18-118">需求</span><span class="sxs-lookup"><span data-stu-id="edb18-118">Requirements</span></span>  
 <span data-ttu-id="edb18-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="edb18-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edb18-120">**標頭：** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="edb18-120">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="edb18-121">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="edb18-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="edb18-122">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edb18-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edb18-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="edb18-123">See also</span></span>

- [<span data-ttu-id="edb18-124">ICLRMetadataLocator 介面</span><span class="sxs-lookup"><span data-stu-id="edb18-124">ICLRMetadataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)

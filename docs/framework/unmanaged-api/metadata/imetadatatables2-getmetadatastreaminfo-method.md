---
title: IMetaDataTables2::GetMetaDataStreamInfo 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStreamInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStreamInfo
helpviewer_keywords:
- GetMetaDataStreamInfo method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStreamInfo method [.NET Framework metadata]
ms.assetid: 8b280627-cc74-4789-95da-1fefc966de05
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57fa18df1baece984a745725dba614e8c4bb1450
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471447"
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a><span data-ttu-id="18ced-102">IMetaDataTables2::GetMetaDataStreamInfo 方法</span><span class="sxs-lookup"><span data-stu-id="18ced-102">IMetaDataTables2::GetMetaDataStreamInfo Method</span></span>
<span data-ttu-id="18ced-103">取得名稱、 大小和指定的索引處的中繼資料資料流內容。</span><span class="sxs-lookup"><span data-stu-id="18ced-103">Gets the name, size, and contents of the metadata stream at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18ced-104">語法</span><span class="sxs-lookup"><span data-stu-id="18ced-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18ced-105">參數</span><span class="sxs-lookup"><span data-stu-id="18ced-105">Parameters</span></span>  
 `ix`  
 <span data-ttu-id="18ced-106">[in]要求的中繼資料資料流的索引。</span><span class="sxs-lookup"><span data-stu-id="18ced-106">[in] The index of the requested metadata stream.</span></span>  
  
 `ppchName`  
 <span data-ttu-id="18ced-107">[out]資料流的名稱指標。</span><span class="sxs-lookup"><span data-stu-id="18ced-107">[out] A pointer to the name of the stream.</span></span>  
  
 `ppv`  
 <span data-ttu-id="18ced-108">[out]中繼資料資料流的指標。</span><span class="sxs-lookup"><span data-stu-id="18ced-108">[out] A pointer to the metadata stream.</span></span>  
  
 `pcb`  
 <span data-ttu-id="18ced-109">[out]大小，以位元組為單位的`ppv`。</span><span class="sxs-lookup"><span data-stu-id="18ced-109">[out] The size, in bytes, of `ppv`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18ced-110">需求</span><span class="sxs-lookup"><span data-stu-id="18ced-110">Requirements</span></span>  
 <span data-ttu-id="18ced-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="18ced-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18ced-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="18ced-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="18ced-113">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="18ced-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="18ced-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18ced-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18ced-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18ced-115">See also</span></span>
- [<span data-ttu-id="18ced-116">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="18ced-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
- [<span data-ttu-id="18ced-117">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="18ced-117">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)

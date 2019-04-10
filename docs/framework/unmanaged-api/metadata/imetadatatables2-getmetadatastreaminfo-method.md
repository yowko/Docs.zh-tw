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
ms.openlocfilehash: 0f70187ba9bd71225162e6e10184e4992b5600f5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228844"
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a><span data-ttu-id="fe791-102">IMetaDataTables2::GetMetaDataStreamInfo 方法</span><span class="sxs-lookup"><span data-stu-id="fe791-102">IMetaDataTables2::GetMetaDataStreamInfo Method</span></span>
<span data-ttu-id="fe791-103">取得名稱、 大小和指定的索引處的中繼資料資料流內容。</span><span class="sxs-lookup"><span data-stu-id="fe791-103">Gets the name, size, and contents of the metadata stream at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe791-104">語法</span><span class="sxs-lookup"><span data-stu-id="fe791-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe791-105">參數</span><span class="sxs-lookup"><span data-stu-id="fe791-105">Parameters</span></span>  
 `ix`  
 <span data-ttu-id="fe791-106">[in]要求的中繼資料資料流的索引。</span><span class="sxs-lookup"><span data-stu-id="fe791-106">[in] The index of the requested metadata stream.</span></span>  
  
 `ppchName`  
 <span data-ttu-id="fe791-107">[out]資料流的名稱指標。</span><span class="sxs-lookup"><span data-stu-id="fe791-107">[out] A pointer to the name of the stream.</span></span>  
  
 `ppv`  
 <span data-ttu-id="fe791-108">[out]中繼資料資料流的指標。</span><span class="sxs-lookup"><span data-stu-id="fe791-108">[out] A pointer to the metadata stream.</span></span>  
  
 `pcb`  
 <span data-ttu-id="fe791-109">[out]大小，以位元組為單位的`ppv`。</span><span class="sxs-lookup"><span data-stu-id="fe791-109">[out] The size, in bytes, of `ppv`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe791-110">需求</span><span class="sxs-lookup"><span data-stu-id="fe791-110">Requirements</span></span>  
 <span data-ttu-id="fe791-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fe791-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe791-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fe791-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fe791-113">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fe791-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="fe791-114">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="fe791-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fe791-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe791-115">See also</span></span>

- [<span data-ttu-id="fe791-116">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="fe791-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
- [<span data-ttu-id="fe791-117">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="fe791-117">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)

---
title: IMetaDataTables2::GetMetaDataStorage 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStorage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStorage
helpviewer_keywords:
- GetMetaDataStorage method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStorage method [.NET Framework metadata]
ms.assetid: 667a6d1e-753d-4ea2-8fd8-a8337d1bb9cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e832bbb58a08c50d8c2bb37fa0c310ef3133d02c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583626"
---
# <a name="imetadatatables2getmetadatastorage-method"></a><span data-ttu-id="5340c-102">IMetaDataTables2::GetMetaDataStorage 方法</span><span class="sxs-lookup"><span data-stu-id="5340c-102">IMetaDataTables2::GetMetaDataStorage Method</span></span>
<span data-ttu-id="5340c-103">取得大小和指定的區段中所儲存的中繼資料的內容。</span><span class="sxs-lookup"><span data-stu-id="5340c-103">Gets the size and contents of the metadata stored in the specified section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5340c-104">語法</span><span class="sxs-lookup"><span data-stu-id="5340c-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataStorage (  
   [in, out] const void   **ppvMd,  
   [out] ULONG   *pcbMd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5340c-105">參數</span><span class="sxs-lookup"><span data-stu-id="5340c-105">Parameters</span></span>  
 `ppvMd`  
 <span data-ttu-id="5340c-106">[in、 out]中繼資料區段指標。</span><span class="sxs-lookup"><span data-stu-id="5340c-106">[in, out] A pointer to a metadata section.</span></span>  
  
 `pcbMd`  
 <span data-ttu-id="5340c-107">[out]中繼資料資料流的大小。</span><span class="sxs-lookup"><span data-stu-id="5340c-107">[out] The size of the metadata stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5340c-108">需求</span><span class="sxs-lookup"><span data-stu-id="5340c-108">Requirements</span></span>  
 <span data-ttu-id="5340c-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5340c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5340c-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5340c-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5340c-111">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5340c-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5340c-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5340c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5340c-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5340c-113">See also</span></span>
- [<span data-ttu-id="5340c-114">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="5340c-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
- [<span data-ttu-id="5340c-115">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="5340c-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)

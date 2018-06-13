---
title: IMetaDataTables::GetBlob 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlob
helpviewer_keywords:
- GetBlob method [.NET Framework metadata]
- IMetaDataTables::GetBlob method [.NET Framework metadata]
ms.assetid: 94667c1c-6d58-4aa7-b74e-530b11e2a276
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 743fb1c77e2dd74487a7498be25ea23b4919032a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447294"
---
# <a name="imetadatatablesgetblob-method"></a><span data-ttu-id="320ce-102">IMetaDataTables::GetBlob 方法</span><span class="sxs-lookup"><span data-stu-id="320ce-102">IMetaDataTables::GetBlob Method</span></span>
<span data-ttu-id="320ce-103">取得二進位大型物件 (BLOB) 的指標，在指定的資料行索引。</span><span class="sxs-lookup"><span data-stu-id="320ce-103">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="320ce-104">語法</span><span class="sxs-lookup"><span data-stu-id="320ce-104">Syntax</span></span>  
  
```  
HRESULT GetBlob (  
    [in]  ULONG          ixBlob,  
    [out] ULONG          *pcbData,  
    [out] const void     **ppData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="320ce-105">參數</span><span class="sxs-lookup"><span data-stu-id="320ce-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="320ce-106">[in]要取得的記憶體位址`ppData`。</span><span class="sxs-lookup"><span data-stu-id="320ce-106">[in] The memory address from which to get `ppData`.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="320ce-107">[out]指標的大小，以位元組為單位的`ppData`。</span><span class="sxs-lookup"><span data-stu-id="320ce-107">[out] A pointer to the size, in bytes, of `ppData`.</span></span>  
  
 `ppData`  
 <span data-ttu-id="320ce-108">[out]擷取二進位資料指標的指標。</span><span class="sxs-lookup"><span data-stu-id="320ce-108">[out] A pointer to a pointer to the binary data retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="320ce-109">需求</span><span class="sxs-lookup"><span data-stu-id="320ce-109">Requirements</span></span>  
 <span data-ttu-id="320ce-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="320ce-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="320ce-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="320ce-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="320ce-112">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="320ce-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="320ce-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="320ce-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="320ce-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="320ce-114">See Also</span></span>  
 [<span data-ttu-id="320ce-115">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="320ce-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="320ce-116">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="320ce-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

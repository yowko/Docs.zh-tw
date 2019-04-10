---
title: IMetaDataTables::GetColumnInfo 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetColumnInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumnInfo
helpviewer_keywords:
- IMetaDataTables::GetColumnInfo method [.NET Framework metadata]
- GetColumnInfo method [.NET Framework metadata]
ms.assetid: 68c160ea-ae7d-4750-985d-a038b2c8e7d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6156499368fb743b69c03f38b40ad3c5bcabce6e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174898"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="fa29c-102">IMetaDataTables::GetColumnInfo 方法</span><span class="sxs-lookup"><span data-stu-id="fa29c-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="fa29c-103">取得指定的資料表中指定的資料行的相關的資料。</span><span class="sxs-lookup"><span data-stu-id="fa29c-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa29c-104">語法</span><span class="sxs-lookup"><span data-stu-id="fa29c-104">Syntax</span></span>  
  
```  
HRESULT GetColumnInfo (   
    [in]  ULONG        ixTbl,  
    [in]  ULONG        ixCol,  
    [out] ULONG        *poCol,  
    [out] ULONG        *pcbCol,  
    [out] ULONG        *pType,  
    [out] const char   **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa29c-105">參數</span><span class="sxs-lookup"><span data-stu-id="fa29c-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="fa29c-106">[in]所需的資料表索引。</span><span class="sxs-lookup"><span data-stu-id="fa29c-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="fa29c-107">[in]所需的資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="fa29c-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="fa29c-108">[out]資料列中的資料行位移的指標。</span><span class="sxs-lookup"><span data-stu-id="fa29c-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="fa29c-109">[out]大小 （位元組），資料行的指標。</span><span class="sxs-lookup"><span data-stu-id="fa29c-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="fa29c-110">[out]資料行中值的類型指標。</span><span class="sxs-lookup"><span data-stu-id="fa29c-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="fa29c-111">[out]指標的資料行名稱的指標。</span><span class="sxs-lookup"><span data-stu-id="fa29c-111">[out] A pointer to a pointer to the column name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa29c-112">需求</span><span class="sxs-lookup"><span data-stu-id="fa29c-112">Requirements</span></span>  
 <span data-ttu-id="fa29c-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fa29c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa29c-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fa29c-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fa29c-115">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fa29c-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="fa29c-116">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="fa29c-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fa29c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa29c-117">See also</span></span>

- [<span data-ttu-id="fa29c-118">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="fa29c-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="fa29c-119">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="fa29c-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

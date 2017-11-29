---
title: "IMetaDataTables::GetColumnInfo 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetColumnInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetColumnInfo
helpviewer_keywords:
- IMetaDataTables::GetColumnInfo method [.NET Framework metadata]
- GetColumnInfo method [.NET Framework metadata]
ms.assetid: 68c160ea-ae7d-4750-985d-a038b2c8e7d9
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 939085294666a233341f65a8f5736d9dce201470
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="b771c-102">IMetaDataTables::GetColumnInfo 方法</span><span class="sxs-lookup"><span data-stu-id="b771c-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="b771c-103">指定資料表中取得指定之資料行的相關資料。</span><span class="sxs-lookup"><span data-stu-id="b771c-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b771c-104">語法</span><span class="sxs-lookup"><span data-stu-id="b771c-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="b771c-105">參數</span><span class="sxs-lookup"><span data-stu-id="b771c-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="b771c-106">[in]所需的資料表索引。</span><span class="sxs-lookup"><span data-stu-id="b771c-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="b771c-107">[in]所需的資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="b771c-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="b771c-108">[out]指向的資料列中的資料行的位移。</span><span class="sxs-lookup"><span data-stu-id="b771c-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="b771c-109">[out]大小 （位元組），資料行的指標。</span><span class="sxs-lookup"><span data-stu-id="b771c-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="b771c-110">[out]資料行中值的類型的指標。</span><span class="sxs-lookup"><span data-stu-id="b771c-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="b771c-111">[out]指標的資料行名稱的指標。</span><span class="sxs-lookup"><span data-stu-id="b771c-111">[out] A pointer to a pointer to the column name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b771c-112">需求</span><span class="sxs-lookup"><span data-stu-id="b771c-112">Requirements</span></span>  
 <span data-ttu-id="b771c-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b771c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b771c-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b771c-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b771c-115">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b771c-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b771c-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b771c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b771c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b771c-117">See Also</span></span>  
 [<span data-ttu-id="b771c-118">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="b771c-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="b771c-119">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="b771c-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

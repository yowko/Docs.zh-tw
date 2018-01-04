---
title: "IMetaDataTables 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables
helpviewer_keywords: IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 31272cce-506a-4f18-bcbf-01ee45e36356
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ff70e99a963c929792a73cefd6e8feaefa8b252e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatables-interface"></a><span data-ttu-id="7d5f7-102">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="7d5f7-102">IMetaDataTables Interface</span></span>
<span data-ttu-id="7d5f7-103">提供儲存和擷取資料表中的中繼資料資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="7d5f7-103">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7d5f7-104">方法</span><span class="sxs-lookup"><span data-stu-id="7d5f7-104">Methods</span></span>  
  
|<span data-ttu-id="7d5f7-105">方法</span><span class="sxs-lookup"><span data-stu-id="7d5f7-105">Method</span></span>|<span data-ttu-id="7d5f7-106">描述</span><span class="sxs-lookup"><span data-stu-id="7d5f7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7d5f7-107">GetBlob 方法</span><span class="sxs-lookup"><span data-stu-id="7d5f7-107">GetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|<span data-ttu-id="7d5f7-108">取得二進位大型物件 (BLOB) 的指標，在指定的資料行索引。</span><span class="sxs-lookup"><span data-stu-id="7d5f7-108">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>|  
|[<span data-ttu-id="7d5f7-109">GetBlobHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="7d5f7-109">GetBlobHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|<span data-ttu-id="7d5f7-110">取得以位元組為單位，對 BLOB 堆積的大小。</span><span class="sxs-lookup"><span data-stu-id="7d5f7-110">Gets the size, in bytes, of the BLOB heap.</span></span>|  
|[<span data-ttu-id="7d5f7-111">GetCodedTokenInfo 方法</span><span class="sxs-lookup"><span data-stu-id="7d5f7-111">GetCodedTokenInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|<span data-ttu-id="7d5f7-112">取得與指定的資料列索引相關聯的語彙基元的陣列指標。</span><span class="sxs-lookup"><span data-stu-id="7d5f7-112">Gets a pointer to an array of tokens associated with the specified row index.</span></span>|  
|[<span data-ttu-id="7d5f7-113">GetColumn 方法</span><span class="sxs-lookup"><span data-stu-id="7d5f7-113">GetColumn Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|<span data-ttu-id="7d5f7-114">取得指定之資料行索引，在指定的資料表索引的資料表中的資料行中所包含之值的指標。</span><span class="sxs-lookup"><span data-stu-id="7d5f7-114">Gets a pointer to the values contained in the column at the specified column index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="7d5f7-115">GetColumnInfo 方法</span><span class="sxs-lookup"><span data-stu-id="7d5f7-115">GetColumnInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|<span data-ttu-id="7d5f7-116">指定資料表中取得指定之資料行的相關資料。</span><span class="sxs-lookup"><span data-stu-id="7d5f7-116">Gets data about the specified column in the specified table.</span></span>|  
|[<span data-ttu-id="7d5f7-117">GetGuid 方法</span><span class="sxs-lookup"><span data-stu-id="7d5f7-117">GetGuid Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|<span data-ttu-id="7d5f7-118">從指定索引處的資料列取得的 GUID。</span><span class="sxs-lookup"><span data-stu-id="7d5f7-118">Gets a GUID from the row at the specified index.</span></span>|  
|[<span data-ttu-id="7d5f7-119">GetGuidHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="7d5f7-119">GetGuidHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|<span data-ttu-id="7d5f7-120">取得以位元組為單位 GUID 堆積的大小。</span><span class="sxs-lookup"><span data-stu-id="7d5f7-120">Gets the size, in bytes, of the GUID heap.</span></span>|  
|[<span data-ttu-id="7d5f7-121">GetNextBlob 方法</span><span class="sxs-lookup"><span data-stu-id="7d5f7-121">GetNextBlob Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|<span data-ttu-id="7d5f7-122">取得資料表中的下一個 BLOB 的索引。</span><span class="sxs-lookup"><span data-stu-id="7d5f7-122">Gets the index of the next BLOB in the table.</span></span>|  
|[<span data-ttu-id="7d5f7-123">GetNextGuid 方法</span><span class="sxs-lookup"><span data-stu-id="7d5f7-123">GetNextGuid Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|<span data-ttu-id="7d5f7-124">取得目前的資料表資料行中的下一個 GUID 值的索引。</span><span class="sxs-lookup"><span data-stu-id="7d5f7-124">Gets the index of the next GUID value in the current table column.</span></span>|  
|[<span data-ttu-id="7d5f7-125">GetNextString 方法</span><span class="sxs-lookup"><span data-stu-id="7d5f7-125">GetNextString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|<span data-ttu-id="7d5f7-126">取得目前的資料表資料行中的下一個字串的索引。</span><span class="sxs-lookup"><span data-stu-id="7d5f7-126">Gets the index of the next string in the current table column.</span></span>|  
|[<span data-ttu-id="7d5f7-127">GetNextUserString 方法</span><span class="sxs-lookup"><span data-stu-id="7d5f7-127">GetNextUserString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|<span data-ttu-id="7d5f7-128">取得包含目前的資料表資料行中的下一個硬式編碼字串的資料列索引。</span><span class="sxs-lookup"><span data-stu-id="7d5f7-128">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>|  
|[<span data-ttu-id="7d5f7-129">GetNumTables 方法</span><span class="sxs-lookup"><span data-stu-id="7d5f7-129">GetNumTables Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|<span data-ttu-id="7d5f7-130">取得目前範圍中的資料表數目`IMetaDataTables`執行個體。</span><span class="sxs-lookup"><span data-stu-id="7d5f7-130">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>|  
|[<span data-ttu-id="7d5f7-131">GetRow 方法</span><span class="sxs-lookup"><span data-stu-id="7d5f7-131">GetRow Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|<span data-ttu-id="7d5f7-132">取得指定資料列索引，在指定的資料表索引的資料表中的資料列。</span><span class="sxs-lookup"><span data-stu-id="7d5f7-132">Gets the row at the specified row index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="7d5f7-133">GetString 方法</span><span class="sxs-lookup"><span data-stu-id="7d5f7-133">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|<span data-ttu-id="7d5f7-134">取得字串中指定索引處與資料表資料行目前參考的範圍內。</span><span class="sxs-lookup"><span data-stu-id="7d5f7-134">Gets the string at the specified index from the table column in the current reference scope.</span></span>|  
|[<span data-ttu-id="7d5f7-135">GetStringHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="7d5f7-135">GetStringHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|<span data-ttu-id="7d5f7-136">取得大小，單位為位元組字串堆積。</span><span class="sxs-lookup"><span data-stu-id="7d5f7-136">Gets the size, in bytes, of the string heap.</span></span>|  
|[<span data-ttu-id="7d5f7-137">GetTableIndex 方法</span><span class="sxs-lookup"><span data-stu-id="7d5f7-137">GetTableIndex Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|<span data-ttu-id="7d5f7-138">取得指定語彙基元所參考之資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="7d5f7-138">Gets the index for the table referenced by the specified token.</span></span>|  
|[<span data-ttu-id="7d5f7-139">GetTableInfo 方法</span><span class="sxs-lookup"><span data-stu-id="7d5f7-139">GetTableInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|<span data-ttu-id="7d5f7-140">取得指定的資料表索引名稱、 資料列大小、 資料列數目、 資料行數和資料表的索引鍵資料行索引。</span><span class="sxs-lookup"><span data-stu-id="7d5f7-140">Gets the name, row size, number of rows, number of columns, and key column index of the table at the specified table index.</span></span>|  
|[<span data-ttu-id="7d5f7-141">GetUserString 方法</span><span class="sxs-lookup"><span data-stu-id="7d5f7-141">GetUserString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|<span data-ttu-id="7d5f7-142">取得目前範圍中的字串資料行中指定索引處的硬式編碼的字串。</span><span class="sxs-lookup"><span data-stu-id="7d5f7-142">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>|  
|[<span data-ttu-id="7d5f7-143">GetUserStringHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="7d5f7-143">GetUserStringHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|<span data-ttu-id="7d5f7-144">取得以位元組為單位的使用者字串堆積的大小。</span><span class="sxs-lookup"><span data-stu-id="7d5f7-144">Gets the size, in bytes, of the user string heap.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7d5f7-145">需求</span><span class="sxs-lookup"><span data-stu-id="7d5f7-145">Requirements</span></span>  
 <span data-ttu-id="7d5f7-146">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7d5f7-146">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d5f7-147">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7d5f7-147">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7d5f7-148">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7d5f7-148">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7d5f7-149">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d5f7-149">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d5f7-150">請參閱</span><span class="sxs-lookup"><span data-stu-id="7d5f7-150">See Also</span></span>  
 [<span data-ttu-id="7d5f7-151">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="7d5f7-151">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="7d5f7-152">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="7d5f7-152">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

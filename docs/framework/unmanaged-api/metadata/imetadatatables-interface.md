---
title: IMetaDataTables 介面
ms.date: 03/30/2017
api_name:
- IMetaDataTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables
helpviewer_keywords:
- IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 31272cce-506a-4f18-bcbf-01ee45e36356
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ea250cd413836796e8e6a3438ac7d6933035091e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714278"
---
# <a name="imetadatatables-interface"></a><span data-ttu-id="8e618-102">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="8e618-102">IMetaDataTables Interface</span></span>
<span data-ttu-id="8e618-103">提供儲存和擷取資料表中的中繼資料資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="8e618-103">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8e618-104">方法</span><span class="sxs-lookup"><span data-stu-id="8e618-104">Methods</span></span>  
  
|<span data-ttu-id="8e618-105">方法</span><span class="sxs-lookup"><span data-stu-id="8e618-105">Method</span></span>|<span data-ttu-id="8e618-106">描述</span><span class="sxs-lookup"><span data-stu-id="8e618-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8e618-107">GetBlob 方法</span><span class="sxs-lookup"><span data-stu-id="8e618-107">GetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|<span data-ttu-id="8e618-108">取得二進位大型物件 (BLOB) 的指標，在指定的資料行索引。</span><span class="sxs-lookup"><span data-stu-id="8e618-108">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>|  
|[<span data-ttu-id="8e618-109">GetBlobHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="8e618-109">GetBlobHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|<span data-ttu-id="8e618-110">取得大小，以位元組為單位，對 BLOB 堆積。</span><span class="sxs-lookup"><span data-stu-id="8e618-110">Gets the size, in bytes, of the BLOB heap.</span></span>|  
|[<span data-ttu-id="8e618-111">GetCodedTokenInfo 方法</span><span class="sxs-lookup"><span data-stu-id="8e618-111">GetCodedTokenInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|<span data-ttu-id="8e618-112">取得與指定的資料列索引相關聯的語彙基元的陣列指標。</span><span class="sxs-lookup"><span data-stu-id="8e618-112">Gets a pointer to an array of tokens associated with the specified row index.</span></span>|  
|[<span data-ttu-id="8e618-113">GetColumn 方法</span><span class="sxs-lookup"><span data-stu-id="8e618-113">GetColumn Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|<span data-ttu-id="8e618-114">取得指定的資料行索引，在指定的資料表索引的資料表中的資料行中包含的值的指標。</span><span class="sxs-lookup"><span data-stu-id="8e618-114">Gets a pointer to the values contained in the column at the specified column index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="8e618-115">GetColumnInfo 方法</span><span class="sxs-lookup"><span data-stu-id="8e618-115">GetColumnInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|<span data-ttu-id="8e618-116">取得指定的資料表中指定的資料行的相關的資料。</span><span class="sxs-lookup"><span data-stu-id="8e618-116">Gets data about the specified column in the specified table.</span></span>|  
|[<span data-ttu-id="8e618-117">GetGuid 方法</span><span class="sxs-lookup"><span data-stu-id="8e618-117">GetGuid Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|<span data-ttu-id="8e618-118">從指定索引處的資料列中取得的 GUID。</span><span class="sxs-lookup"><span data-stu-id="8e618-118">Gets a GUID from the row at the specified index.</span></span>|  
|[<span data-ttu-id="8e618-119">GetGuidHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="8e618-119">GetGuidHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|<span data-ttu-id="8e618-120">取得大小，以位元組為單位，GUID 堆積。</span><span class="sxs-lookup"><span data-stu-id="8e618-120">Gets the size, in bytes, of the GUID heap.</span></span>|  
|[<span data-ttu-id="8e618-121">GetNextBlob 方法</span><span class="sxs-lookup"><span data-stu-id="8e618-121">GetNextBlob Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|<span data-ttu-id="8e618-122">取得資料表中的下一個 BLOB 的索引。</span><span class="sxs-lookup"><span data-stu-id="8e618-122">Gets the index of the next BLOB in the table.</span></span>|  
|[<span data-ttu-id="8e618-123">GetNextGuid 方法</span><span class="sxs-lookup"><span data-stu-id="8e618-123">GetNextGuid Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|<span data-ttu-id="8e618-124">取得目前的資料表資料行中的下一個 GUID 值的索引。</span><span class="sxs-lookup"><span data-stu-id="8e618-124">Gets the index of the next GUID value in the current table column.</span></span>|  
|[<span data-ttu-id="8e618-125">GetNextString 方法</span><span class="sxs-lookup"><span data-stu-id="8e618-125">GetNextString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|<span data-ttu-id="8e618-126">取得目前的資料表資料行中的下一個字串的索引。</span><span class="sxs-lookup"><span data-stu-id="8e618-126">Gets the index of the next string in the current table column.</span></span>|  
|[<span data-ttu-id="8e618-127">GetNextUserString 方法</span><span class="sxs-lookup"><span data-stu-id="8e618-127">GetNextUserString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|<span data-ttu-id="8e618-128">取得包含目前的資料表資料行中的下一步 硬式編碼字串的資料列索引。</span><span class="sxs-lookup"><span data-stu-id="8e618-128">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>|  
|[<span data-ttu-id="8e618-129">GetNumTables 方法</span><span class="sxs-lookup"><span data-stu-id="8e618-129">GetNumTables Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|<span data-ttu-id="8e618-130">取得目前的範圍中的資料表數目`IMetaDataTables`執行個體。</span><span class="sxs-lookup"><span data-stu-id="8e618-130">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>|  
|[<span data-ttu-id="8e618-131">GetRow 方法</span><span class="sxs-lookup"><span data-stu-id="8e618-131">GetRow Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|<span data-ttu-id="8e618-132">取得指定的資料列索引，在指定的資料表索引的資料表中的資料列。</span><span class="sxs-lookup"><span data-stu-id="8e618-132">Gets the row at the specified row index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="8e618-133">GetString 方法</span><span class="sxs-lookup"><span data-stu-id="8e618-133">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|<span data-ttu-id="8e618-134">取得字串的指定索引處與資料表資料行中目前參考的範圍。</span><span class="sxs-lookup"><span data-stu-id="8e618-134">Gets the string at the specified index from the table column in the current reference scope.</span></span>|  
|[<span data-ttu-id="8e618-135">GetStringHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="8e618-135">GetStringHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|<span data-ttu-id="8e618-136">取得大小，以位元組為單位對字串堆積。</span><span class="sxs-lookup"><span data-stu-id="8e618-136">Gets the size, in bytes, of the string heap.</span></span>|  
|[<span data-ttu-id="8e618-137">GetTableIndex 方法</span><span class="sxs-lookup"><span data-stu-id="8e618-137">GetTableIndex Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|<span data-ttu-id="8e618-138">取得指定語彙基元所參考之資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="8e618-138">Gets the index for the table referenced by the specified token.</span></span>|  
|[<span data-ttu-id="8e618-139">GetTableInfo 方法</span><span class="sxs-lookup"><span data-stu-id="8e618-139">GetTableInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|<span data-ttu-id="8e618-140">取得在指定的資料表索引的名稱、 資料列大小、 資料列數目、 資料行和資料表的索引鍵資料行索引。</span><span class="sxs-lookup"><span data-stu-id="8e618-140">Gets the name, row size, number of rows, number of columns, and key column index of the table at the specified table index.</span></span>|  
|[<span data-ttu-id="8e618-141">GetUserString 方法</span><span class="sxs-lookup"><span data-stu-id="8e618-141">GetUserString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|<span data-ttu-id="8e618-142">取得在目前範圍中的字串資料行中的指定索引處的硬式編碼的字串。</span><span class="sxs-lookup"><span data-stu-id="8e618-142">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>|  
|[<span data-ttu-id="8e618-143">GetUserStringHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="8e618-143">GetUserStringHeapSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|<span data-ttu-id="8e618-144">取得大小，以位元組為單位的使用者字串堆積。</span><span class="sxs-lookup"><span data-stu-id="8e618-144">Gets the size, in bytes, of the user string heap.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8e618-145">需求</span><span class="sxs-lookup"><span data-stu-id="8e618-145">Requirements</span></span>  
 <span data-ttu-id="8e618-146">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8e618-146">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e618-147">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8e618-147">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8e618-148">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8e618-148">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8e618-149">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e618-149">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e618-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e618-150">See also</span></span>
- [<span data-ttu-id="8e618-151">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="8e618-151">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="8e618-152">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="8e618-152">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

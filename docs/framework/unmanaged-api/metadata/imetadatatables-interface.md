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
ms.openlocfilehash: 2105033e684ec172e24adfb14bcab7668b388af3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501117"
---
# <a name="imetadatatables-interface"></a><span data-ttu-id="a993c-102">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="a993c-102">IMetaDataTables Interface</span></span>
<span data-ttu-id="a993c-103">提供儲存和擷取資料表中的中繼資料資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="a993c-103">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a993c-104">方法</span><span class="sxs-lookup"><span data-stu-id="a993c-104">Methods</span></span>  
  
|<span data-ttu-id="a993c-105">方法</span><span class="sxs-lookup"><span data-stu-id="a993c-105">Method</span></span>|<span data-ttu-id="a993c-106">描述</span><span class="sxs-lookup"><span data-stu-id="a993c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a993c-107">GetBlob 方法</span><span class="sxs-lookup"><span data-stu-id="a993c-107">GetBlob Method</span></span>](imetadatatables-getblob-method.md)|<span data-ttu-id="a993c-108">取得位於指定之資料行索引處之二進位大型物件（BLOB）的指標。</span><span class="sxs-lookup"><span data-stu-id="a993c-108">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>|  
|[<span data-ttu-id="a993c-109">GetBlobHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="a993c-109">GetBlobHeapSize Method</span></span>](imetadatatables-getblobheapsize-method.md)|<span data-ttu-id="a993c-110">取得 BLOB 堆積的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="a993c-110">Gets the size, in bytes, of the BLOB heap.</span></span>|  
|[<span data-ttu-id="a993c-111">GetCodedTokenInfo 方法</span><span class="sxs-lookup"><span data-stu-id="a993c-111">GetCodedTokenInfo Method</span></span>](imetadatatables-getcodedtokeninfo-method.md)|<span data-ttu-id="a993c-112">取得與指定之資料列索引相關聯之標記陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="a993c-112">Gets a pointer to an array of tokens associated with the specified row index.</span></span>|  
|[<span data-ttu-id="a993c-113">GetColumn 方法</span><span class="sxs-lookup"><span data-stu-id="a993c-113">GetColumn Method</span></span>](imetadatatables-getcolumn-method.md)|<span data-ttu-id="a993c-114">取得指定之資料表索引的資料表中，位於指定之資料行索引之資料行中的值指標。</span><span class="sxs-lookup"><span data-stu-id="a993c-114">Gets a pointer to the values contained in the column at the specified column index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="a993c-115">GetColumnInfo 方法</span><span class="sxs-lookup"><span data-stu-id="a993c-115">GetColumnInfo Method</span></span>](imetadatatables-getcolumninfo-method.md)|<span data-ttu-id="a993c-116">取得指定資料表中指定之資料行的相關資料。</span><span class="sxs-lookup"><span data-stu-id="a993c-116">Gets data about the specified column in the specified table.</span></span>|  
|[<span data-ttu-id="a993c-117">GetGuid 方法</span><span class="sxs-lookup"><span data-stu-id="a993c-117">GetGuid Method</span></span>](imetadatatables-getguid-method.md)|<span data-ttu-id="a993c-118">從指定索引處的資料列取得 GUID。</span><span class="sxs-lookup"><span data-stu-id="a993c-118">Gets a GUID from the row at the specified index.</span></span>|  
|[<span data-ttu-id="a993c-119">GetGuidHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="a993c-119">GetGuidHeapSize Method</span></span>](imetadatatables-getguidheapsize-method.md)|<span data-ttu-id="a993c-120">取得 GUID 堆積的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="a993c-120">Gets the size, in bytes, of the GUID heap.</span></span>|  
|[<span data-ttu-id="a993c-121">GetNextBlob 方法</span><span class="sxs-lookup"><span data-stu-id="a993c-121">GetNextBlob Method</span></span>](imetadatatables-getnextblob-method.md)|<span data-ttu-id="a993c-122">取得資料表中下一個 BLOB 的索引。</span><span class="sxs-lookup"><span data-stu-id="a993c-122">Gets the index of the next BLOB in the table.</span></span>|  
|[<span data-ttu-id="a993c-123">GetNextGuid 方法</span><span class="sxs-lookup"><span data-stu-id="a993c-123">GetNextGuid Method</span></span>](imetadatatables-getnextguid-method.md)|<span data-ttu-id="a993c-124">取得目前資料表資料行中下一個 GUID 值的索引。</span><span class="sxs-lookup"><span data-stu-id="a993c-124">Gets the index of the next GUID value in the current table column.</span></span>|  
|[<span data-ttu-id="a993c-125">GetNextString 方法</span><span class="sxs-lookup"><span data-stu-id="a993c-125">GetNextString Method</span></span>](imetadatatables-getnextstring-method.md)|<span data-ttu-id="a993c-126">取得目前資料表資料行中下一個字串的索引。</span><span class="sxs-lookup"><span data-stu-id="a993c-126">Gets the index of the next string in the current table column.</span></span>|  
|[<span data-ttu-id="a993c-127">GetNextUserString 方法</span><span class="sxs-lookup"><span data-stu-id="a993c-127">GetNextUserString Method</span></span>](imetadatatables-getnextuserstring-method.md)|<span data-ttu-id="a993c-128">取得包含目前資料表資料行中下一個硬式編碼字串的資料列索引。</span><span class="sxs-lookup"><span data-stu-id="a993c-128">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>|  
|[<span data-ttu-id="a993c-129">GetNumTables 方法</span><span class="sxs-lookup"><span data-stu-id="a993c-129">GetNumTables Method</span></span>](imetadatatables-getnumtables-method.md)|<span data-ttu-id="a993c-130">取得目前實例範圍中的資料表數目 `IMetaDataTables` 。</span><span class="sxs-lookup"><span data-stu-id="a993c-130">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>|  
|[<span data-ttu-id="a993c-131">GetRow 方法</span><span class="sxs-lookup"><span data-stu-id="a993c-131">GetRow Method</span></span>](imetadatatables-getrow-method.md)|<span data-ttu-id="a993c-132">在指定之資料表索引的資料表中，取得位於指定資料列索引處的資料列。</span><span class="sxs-lookup"><span data-stu-id="a993c-132">Gets the row at the specified row index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="a993c-133">GetString 方法</span><span class="sxs-lookup"><span data-stu-id="a993c-133">GetString Method</span></span>](imetadatatables-getstring-method.md)|<span data-ttu-id="a993c-134">從目前參考範圍的資料表資料行中，取得位於指定索引位置的字串。</span><span class="sxs-lookup"><span data-stu-id="a993c-134">Gets the string at the specified index from the table column in the current reference scope.</span></span>|  
|[<span data-ttu-id="a993c-135">GetStringHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="a993c-135">GetStringHeapSize Method</span></span>](imetadatatables-getstringheapsize-method.md)|<span data-ttu-id="a993c-136">取得字串堆積的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="a993c-136">Gets the size, in bytes, of the string heap.</span></span>|  
|[<span data-ttu-id="a993c-137">GetTableIndex 方法</span><span class="sxs-lookup"><span data-stu-id="a993c-137">GetTableIndex Method</span></span>](imetadatatables-gettableindex-method.md)|<span data-ttu-id="a993c-138">取得指定之標記所參考之資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="a993c-138">Gets the index for the table referenced by the specified token.</span></span>|  
|[<span data-ttu-id="a993c-139">GetTableInfo 方法</span><span class="sxs-lookup"><span data-stu-id="a993c-139">GetTableInfo Method</span></span>](imetadatatables-gettableinfo-method.md)|<span data-ttu-id="a993c-140">取得指定資料表索引處之資料表的名稱、資料列大小、資料列數目、資料行數目和索引鍵資料行索引。</span><span class="sxs-lookup"><span data-stu-id="a993c-140">Gets the name, row size, number of rows, number of columns, and key column index of the table at the specified table index.</span></span>|  
|[<span data-ttu-id="a993c-141">GetUserString 方法</span><span class="sxs-lookup"><span data-stu-id="a993c-141">GetUserString Method</span></span>](imetadatatables-getuserstring-method.md)|<span data-ttu-id="a993c-142">取得在目前範圍的字串資料行中指定索引處的硬式編碼字串。</span><span class="sxs-lookup"><span data-stu-id="a993c-142">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>|  
|[<span data-ttu-id="a993c-143">GetUserStringHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="a993c-143">GetUserStringHeapSize Method</span></span>](imetadatatables-getuserstringheapsize-method.md)|<span data-ttu-id="a993c-144">取得使用者字串堆積的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="a993c-144">Gets the size, in bytes, of the user string heap.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a993c-145">規格需求</span><span class="sxs-lookup"><span data-stu-id="a993c-145">Requirements</span></span>  
 <span data-ttu-id="a993c-146">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a993c-146">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a993c-147">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="a993c-147">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a993c-148">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="a993c-148">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a993c-149">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a993c-149">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a993c-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a993c-150">See also</span></span>

- [<span data-ttu-id="a993c-151">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="a993c-151">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="a993c-152">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="a993c-152">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)

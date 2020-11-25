---
title: IMetaDataTables::GetColumn 方法
ms.date: 02/25/2019
api_name:
- IMetaDataTables.GetColumn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type:
- apiref
ms.openlocfilehash: 270546f0270521e38cfdcae5e4d2137202c13cb1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711064"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="c4a83-102">IMetaDataTables::GetColumn 方法</span><span class="sxs-lookup"><span data-stu-id="c4a83-102">IMetaDataTables::GetColumn Method</span></span>

<span data-ttu-id="c4a83-103">取得包含在指定資料表中指定之資料行和資料列之資料格中的值指標。</span><span class="sxs-lookup"><span data-stu-id="c4a83-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4a83-104">語法</span><span class="sxs-lookup"><span data-stu-id="c4a83-104">Syntax</span></span>  
  
```cpp  
HRESULT GetColumn (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4a83-105">參數</span><span class="sxs-lookup"><span data-stu-id="c4a83-105">Parameters</span></span>

 `ixTbl`  
 <span data-ttu-id="c4a83-106">在資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="c4a83-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="c4a83-107">在資料表中資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="c4a83-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="c4a83-108">在資料表中資料列的索引。</span><span class="sxs-lookup"><span data-stu-id="c4a83-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="c4a83-109">擴展資料格中值的指標。</span><span class="sxs-lookup"><span data-stu-id="c4a83-109">[out] A pointer to the value in the cell.</span></span>  

## <a name="remarks"></a><span data-ttu-id="c4a83-110">備註</span><span class="sxs-lookup"><span data-stu-id="c4a83-110">Remarks</span></span>

<span data-ttu-id="c4a83-111">透過傳回的值 interpretion `pVal` 取決於資料行的類型。</span><span class="sxs-lookup"><span data-stu-id="c4a83-111">The interpretion of the value returned through `pVal` depends on the column's type.</span></span> <span data-ttu-id="c4a83-112">您可以藉由呼叫 [IMetaDataTables GetColumnInfo](imetadatatables-getcolumninfo-method.md)來判斷資料行類型。</span><span class="sxs-lookup"><span data-stu-id="c4a83-112">The column type can be determined by calling [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span></span>

- <span data-ttu-id="c4a83-113">**GetColumn** 方法會自動將 **Rid** 或 **CodedToken** 類型的資料行轉換為完整32位 `mdToken` 值。</span><span class="sxs-lookup"><span data-stu-id="c4a83-113">The **GetColumn** method automatically converts columns of type **Rid** or **CodedToken** to full 32-bit `mdToken` values.</span></span>
- <span data-ttu-id="c4a83-114">它也會自動將8位或16位值轉換成完整的32位值。</span><span class="sxs-lookup"><span data-stu-id="c4a83-114">It also automatically converts 8-bit or 16-bit values to full 32-bit values.</span></span>
- <span data-ttu-id="c4a83-115">針對 *堆積* 類型資料行，傳回的 *pVal* 會是對應堆積的索引。</span><span class="sxs-lookup"><span data-stu-id="c4a83-115">For *heap* type columns, the returned *pVal* will be an index into the corresponding heap.</span></span>

| <span data-ttu-id="c4a83-116">資料行類型</span><span class="sxs-lookup"><span data-stu-id="c4a83-116">Column type</span></span>              | <span data-ttu-id="c4a83-117">pVal contains</span><span class="sxs-lookup"><span data-stu-id="c4a83-117">pVal contains</span></span> | <span data-ttu-id="c4a83-118">註解</span><span class="sxs-lookup"><span data-stu-id="c4a83-118">Comment</span></span>                          |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="c4a83-119">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="c4a83-119">`0`..`iRidMax`</span></span><br><span data-ttu-id="c4a83-120"> (0. 63) </span><span class="sxs-lookup"><span data-stu-id="c4a83-120">(0..63)</span></span>  | <span data-ttu-id="c4a83-121">mdToken</span><span class="sxs-lookup"><span data-stu-id="c4a83-121">mdToken</span></span>     | <span data-ttu-id="c4a83-122">*pVal* 將包含完整的權杖。</span><span class="sxs-lookup"><span data-stu-id="c4a83-122">*pVal* will contain a full Token.</span></span> <span data-ttu-id="c4a83-123">函數會自動將 Rid 轉換成完整的權杖。</span><span class="sxs-lookup"><span data-stu-id="c4a83-123">The function automatically converts the Rid into a full token.</span></span> |
| <span data-ttu-id="c4a83-124">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="c4a83-124">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="c4a83-125"> (64. 95) </span><span class="sxs-lookup"><span data-stu-id="c4a83-125">(64..95)</span></span> | <span data-ttu-id="c4a83-126">mdToken</span><span class="sxs-lookup"><span data-stu-id="c4a83-126">mdToken</span></span> | <span data-ttu-id="c4a83-127">傳回時， *pVal* 會包含完整的權杖。</span><span class="sxs-lookup"><span data-stu-id="c4a83-127">Upon return, *pVal* will contain a full Token.</span></span> <span data-ttu-id="c4a83-128">此函式會自動將 CodedToken 解壓縮至完整權杖中。</span><span class="sxs-lookup"><span data-stu-id="c4a83-128">The function automatically decompresses the CodedToken into a full token.</span></span> |
| <span data-ttu-id="c4a83-129">`iSHORT` (96) </span><span class="sxs-lookup"><span data-stu-id="c4a83-129">`iSHORT` (96)</span></span>            | <span data-ttu-id="c4a83-130">Int16</span><span class="sxs-lookup"><span data-stu-id="c4a83-130">Int16</span></span>         | <span data-ttu-id="c4a83-131">自動將簽章延伸至32位。</span><span class="sxs-lookup"><span data-stu-id="c4a83-131">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="c4a83-132">`iUSHORT` (97) </span><span class="sxs-lookup"><span data-stu-id="c4a83-132">`iUSHORT` (97)</span></span>           | <span data-ttu-id="c4a83-133">UInt16</span><span class="sxs-lookup"><span data-stu-id="c4a83-133">UInt16</span></span>        | <span data-ttu-id="c4a83-134">自動將簽章延伸至32位。</span><span class="sxs-lookup"><span data-stu-id="c4a83-134">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="c4a83-135">`iLONG` (98) </span><span class="sxs-lookup"><span data-stu-id="c4a83-135">`iLONG` (98)</span></span>             | <span data-ttu-id="c4a83-136">Int32</span><span class="sxs-lookup"><span data-stu-id="c4a83-136">Int32</span></span>         |                                        |
| <span data-ttu-id="c4a83-137">`iULONG` (99) </span><span class="sxs-lookup"><span data-stu-id="c4a83-137">`iULONG` (99)</span></span>            | <span data-ttu-id="c4a83-138">UInt32</span><span class="sxs-lookup"><span data-stu-id="c4a83-138">UInt32</span></span>        |                                        |
| <span data-ttu-id="c4a83-139">`iBYTE` (100) </span><span class="sxs-lookup"><span data-stu-id="c4a83-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="c4a83-140">Byte</span><span class="sxs-lookup"><span data-stu-id="c4a83-140">Byte</span></span>          | <span data-ttu-id="c4a83-141">自動將簽章延伸至32位。</span><span class="sxs-lookup"><span data-stu-id="c4a83-141">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="c4a83-142">`iSTRING` (101) </span><span class="sxs-lookup"><span data-stu-id="c4a83-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="c4a83-143">字串堆積索引</span><span class="sxs-lookup"><span data-stu-id="c4a83-143">String heap index</span></span> | <span data-ttu-id="c4a83-144">*pVal* 是字串堆積的索引。</span><span class="sxs-lookup"><span data-stu-id="c4a83-144">*pVal* is an index into the String heap.</span></span> <span data-ttu-id="c4a83-145">使用 [IMetadataTables：： GetString](imetadatatables-getstring-method.md) 來取得實際的資料行字串值。</span><span class="sxs-lookup"><span data-stu-id="c4a83-145">Use [IMetadataTables::GetString](imetadatatables-getstring-method.md) to get the actual column String value.</span></span> |
| <span data-ttu-id="c4a83-146">`iGUID` (102) </span><span class="sxs-lookup"><span data-stu-id="c4a83-146">`iGUID` (102)</span></span>            | <span data-ttu-id="c4a83-147">Guid 堆積索引</span><span class="sxs-lookup"><span data-stu-id="c4a83-147">Guid heap index</span></span> | <span data-ttu-id="c4a83-148">*pVal* 是 Guid 堆積的索引。</span><span class="sxs-lookup"><span data-stu-id="c4a83-148">*pVal* is an index into the Guid heap.</span></span> <span data-ttu-id="c4a83-149">使用 [IMetadataTables：： GetGuid](imetadatatables-getguid-method.md) 取得實際的資料行 Guid 值。</span><span class="sxs-lookup"><span data-stu-id="c4a83-149">Use [IMetadataTables::GetGuid](imetadatatables-getguid-method.md) to get the actual column Guid value.</span></span> |
| <span data-ttu-id="c4a83-150">`iBLOB` (103) </span><span class="sxs-lookup"><span data-stu-id="c4a83-150">`iBLOB` (103)</span></span>            | <span data-ttu-id="c4a83-151">Blob 堆積索引</span><span class="sxs-lookup"><span data-stu-id="c4a83-151">Blob heap index</span></span> | <span data-ttu-id="c4a83-152">*pVal* 是 Blob 堆積中的索引。</span><span class="sxs-lookup"><span data-stu-id="c4a83-152">*pVal* is an index into the Blob heap.</span></span> <span data-ttu-id="c4a83-153">使用 [IMetadataTables：： GetBlob](imetadatatables-getblob-method.md) 取得實際的資料行 Blob 值。</span><span class="sxs-lookup"><span data-stu-id="c4a83-153">Use [IMetadataTables::GetBlob](imetadatatables-getblob-method.md) to get the actual column Blob value.</span></span> |
  
## <a name="requirements"></a><span data-ttu-id="c4a83-154">需求</span><span class="sxs-lookup"><span data-stu-id="c4a83-154">Requirements</span></span>  

 <span data-ttu-id="c4a83-155">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c4a83-155">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4a83-156">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="c4a83-156">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c4a83-157">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="c4a83-157">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c4a83-158">**.NET Framework 版本**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4a83-158">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4a83-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4a83-159">See also</span></span>

- [<span data-ttu-id="c4a83-160">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="c4a83-160">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="c4a83-161">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="c4a83-161">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)

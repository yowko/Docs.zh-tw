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
ms.openlocfilehash: 76d23fe9221ae5a07d79b8c5c1a7ad297922b003
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501244"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="ed7a3-102">IMetaDataTables::GetColumn 方法</span><span class="sxs-lookup"><span data-stu-id="ed7a3-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="ed7a3-103">取得給定資料表中指定之資料行和資料列的儲存格所包含之值的指標。</span><span class="sxs-lookup"><span data-stu-id="ed7a3-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed7a3-104">語法</span><span class="sxs-lookup"><span data-stu-id="ed7a3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetColumn (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed7a3-105">參數</span><span class="sxs-lookup"><span data-stu-id="ed7a3-105">Parameters</span></span>

 `ixTbl`  
 <span data-ttu-id="ed7a3-106">在資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="ed7a3-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="ed7a3-107">在資料表中資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="ed7a3-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="ed7a3-108">在資料表中的資料列索引。</span><span class="sxs-lookup"><span data-stu-id="ed7a3-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="ed7a3-109">脫銷儲存格中值的指標。</span><span class="sxs-lookup"><span data-stu-id="ed7a3-109">[out] A pointer to the value in the cell.</span></span>  

## <a name="remarks"></a><span data-ttu-id="ed7a3-110">備註</span><span class="sxs-lookup"><span data-stu-id="ed7a3-110">Remarks</span></span>

<span data-ttu-id="ed7a3-111">透過傳回之值的 interpretion `pVal` 取決於資料行的類型。</span><span class="sxs-lookup"><span data-stu-id="ed7a3-111">The interpretion of the value returned through `pVal` depends on the column's type.</span></span> <span data-ttu-id="ed7a3-112">您可以藉由呼叫 IMetaDataTables 來判斷資料行類型。 [GetColumnInfo](imetadatatables-getcolumninfo-method.md)。</span><span class="sxs-lookup"><span data-stu-id="ed7a3-112">The column type can be determined by calling [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span></span>

- <span data-ttu-id="ed7a3-113">**GetColumn**方法會自動將**Rid**或**CodedToken**類型的資料行轉換成完整32位的 `mdToken` 值。</span><span class="sxs-lookup"><span data-stu-id="ed7a3-113">The **GetColumn** method automatically converts columns of type **Rid** or **CodedToken** to full 32-bit `mdToken` values.</span></span>
- <span data-ttu-id="ed7a3-114">它也會自動將8位或16位的值轉換成完整的32位值。</span><span class="sxs-lookup"><span data-stu-id="ed7a3-114">It also automatically converts 8-bit or 16-bit values to full 32-bit values.</span></span>
- <span data-ttu-id="ed7a3-115">若是*堆積*類型的資料行，傳回的*pVal*將會是對應堆積的索引。</span><span class="sxs-lookup"><span data-stu-id="ed7a3-115">For *heap* type columns, the returned *pVal* will be an index into the corresponding heap.</span></span>

| <span data-ttu-id="ed7a3-116">資料行類型</span><span class="sxs-lookup"><span data-stu-id="ed7a3-116">Column type</span></span>              | <span data-ttu-id="ed7a3-117">pVal 包含</span><span class="sxs-lookup"><span data-stu-id="ed7a3-117">pVal contains</span></span> | <span data-ttu-id="ed7a3-118">註解</span><span class="sxs-lookup"><span data-stu-id="ed7a3-118">Comment</span></span>                          |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="ed7a3-119">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="ed7a3-119">`0`..`iRidMax`</span></span><br><span data-ttu-id="ed7a3-120">（0到63）</span><span class="sxs-lookup"><span data-stu-id="ed7a3-120">(0..63)</span></span>  | <span data-ttu-id="ed7a3-121">mdToken</span><span class="sxs-lookup"><span data-stu-id="ed7a3-121">mdToken</span></span>     | <span data-ttu-id="ed7a3-122">*pVal*會包含完整的 Token。</span><span class="sxs-lookup"><span data-stu-id="ed7a3-122">*pVal* will contain a full Token.</span></span> <span data-ttu-id="ed7a3-123">函式會自動將 Rid 轉換成完整 token。</span><span class="sxs-lookup"><span data-stu-id="ed7a3-123">The function automatically converts the Rid into a full token.</span></span> |
| <span data-ttu-id="ed7a3-124">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="ed7a3-124">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="ed7a3-125">（64. 95）</span><span class="sxs-lookup"><span data-stu-id="ed7a3-125">(64..95)</span></span> | <span data-ttu-id="ed7a3-126">mdToken</span><span class="sxs-lookup"><span data-stu-id="ed7a3-126">mdToken</span></span> | <span data-ttu-id="ed7a3-127">傳回時， *pVal*會包含完整的 Token。</span><span class="sxs-lookup"><span data-stu-id="ed7a3-127">Upon return, *pVal* will contain a full Token.</span></span> <span data-ttu-id="ed7a3-128">函式會自動將 CodedToken 解壓縮至完整 token。</span><span class="sxs-lookup"><span data-stu-id="ed7a3-128">The function automatically decompresses the CodedToken into a full token.</span></span> |
| <span data-ttu-id="ed7a3-129">`iSHORT`（96）</span><span class="sxs-lookup"><span data-stu-id="ed7a3-129">`iSHORT` (96)</span></span>            | <span data-ttu-id="ed7a3-130">Int16</span><span class="sxs-lookup"><span data-stu-id="ed7a3-130">Int16</span></span>         | <span data-ttu-id="ed7a3-131">自動將簽章延伸至32位。</span><span class="sxs-lookup"><span data-stu-id="ed7a3-131">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="ed7a3-132">`iUSHORT`（97）</span><span class="sxs-lookup"><span data-stu-id="ed7a3-132">`iUSHORT` (97)</span></span>           | <span data-ttu-id="ed7a3-133">UInt16</span><span class="sxs-lookup"><span data-stu-id="ed7a3-133">UInt16</span></span>        | <span data-ttu-id="ed7a3-134">自動將簽章延伸至32位。</span><span class="sxs-lookup"><span data-stu-id="ed7a3-134">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="ed7a3-135">`iLONG`（98）</span><span class="sxs-lookup"><span data-stu-id="ed7a3-135">`iLONG` (98)</span></span>             | <span data-ttu-id="ed7a3-136">Int32</span><span class="sxs-lookup"><span data-stu-id="ed7a3-136">Int32</span></span>         |                                        |
| <span data-ttu-id="ed7a3-137">`iULONG`（99）</span><span class="sxs-lookup"><span data-stu-id="ed7a3-137">`iULONG` (99)</span></span>            | <span data-ttu-id="ed7a3-138">UInt32</span><span class="sxs-lookup"><span data-stu-id="ed7a3-138">UInt32</span></span>        |                                        |
| <span data-ttu-id="ed7a3-139">`iBYTE`（100）</span><span class="sxs-lookup"><span data-stu-id="ed7a3-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="ed7a3-140">Byte</span><span class="sxs-lookup"><span data-stu-id="ed7a3-140">Byte</span></span>          | <span data-ttu-id="ed7a3-141">自動將簽章延伸至32位。</span><span class="sxs-lookup"><span data-stu-id="ed7a3-141">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="ed7a3-142">`iSTRING`（101）</span><span class="sxs-lookup"><span data-stu-id="ed7a3-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="ed7a3-143">字串堆積索引</span><span class="sxs-lookup"><span data-stu-id="ed7a3-143">String heap index</span></span> | <span data-ttu-id="ed7a3-144">*pVal*是字串堆積中的索引。</span><span class="sxs-lookup"><span data-stu-id="ed7a3-144">*pVal* is an index into the String heap.</span></span> <span data-ttu-id="ed7a3-145">請使用[IMetadataTables：： GetString](imetadatatables-getstring-method.md)來取得實際的資料行字串值。</span><span class="sxs-lookup"><span data-stu-id="ed7a3-145">Use [IMetadataTables::GetString](imetadatatables-getstring-method.md) to get the actual column String value.</span></span> |
| <span data-ttu-id="ed7a3-146">`iGUID`（102）</span><span class="sxs-lookup"><span data-stu-id="ed7a3-146">`iGUID` (102)</span></span>            | <span data-ttu-id="ed7a3-147">Guid 堆積索引</span><span class="sxs-lookup"><span data-stu-id="ed7a3-147">Guid heap index</span></span> | <span data-ttu-id="ed7a3-148">*pVal*是 Guid 堆積中的索引。</span><span class="sxs-lookup"><span data-stu-id="ed7a3-148">*pVal* is an index into the Guid heap.</span></span> <span data-ttu-id="ed7a3-149">請使用[IMetadataTables：： GetGuid](imetadatatables-getguid-method.md)來取得實際的資料行 Guid 值。</span><span class="sxs-lookup"><span data-stu-id="ed7a3-149">Use [IMetadataTables::GetGuid](imetadatatables-getguid-method.md) to get the actual column Guid value.</span></span> |
| <span data-ttu-id="ed7a3-150">`iBLOB`（103）</span><span class="sxs-lookup"><span data-stu-id="ed7a3-150">`iBLOB` (103)</span></span>            | <span data-ttu-id="ed7a3-151">Blob 堆積索引</span><span class="sxs-lookup"><span data-stu-id="ed7a3-151">Blob heap index</span></span> | <span data-ttu-id="ed7a3-152">*pVal*是 Blob 堆積中的索引。</span><span class="sxs-lookup"><span data-stu-id="ed7a3-152">*pVal* is an index into the Blob heap.</span></span> <span data-ttu-id="ed7a3-153">請使用[IMetadataTables：： GetBlob](imetadatatables-getblob-method.md)來取得實際的資料行 Blob 值。</span><span class="sxs-lookup"><span data-stu-id="ed7a3-153">Use [IMetadataTables::GetBlob](imetadatatables-getblob-method.md) to get the actual column Blob value.</span></span> |
  
## <a name="requirements"></a><span data-ttu-id="ed7a3-154">規格需求</span><span class="sxs-lookup"><span data-stu-id="ed7a3-154">Requirements</span></span>  
 <span data-ttu-id="ed7a3-155">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ed7a3-155">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed7a3-156">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="ed7a3-156">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ed7a3-157">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="ed7a3-157">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ed7a3-158">**.NET Framework 版本**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed7a3-158">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed7a3-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed7a3-159">See also</span></span>

- [<span data-ttu-id="ed7a3-160">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="ed7a3-160">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="ed7a3-161">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="ed7a3-161">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)

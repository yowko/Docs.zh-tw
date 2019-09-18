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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 853f137d91e1b3eb4f3f65a06522618f8441dcb3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053681"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="a8e98-102">IMetaDataTables::GetColumn 方法</span><span class="sxs-lookup"><span data-stu-id="a8e98-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="a8e98-103">取得給定資料表中指定之資料行和資料列的儲存格所包含之值的指標。</span><span class="sxs-lookup"><span data-stu-id="a8e98-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8e98-104">語法</span><span class="sxs-lookup"><span data-stu-id="a8e98-104">Syntax</span></span>  
  
```cpp  
HRESULT GetColumn (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8e98-105">參數</span><span class="sxs-lookup"><span data-stu-id="a8e98-105">Parameters</span></span>

 `ixTbl`  
 <span data-ttu-id="a8e98-106">在資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="a8e98-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="a8e98-107">在資料表中資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="a8e98-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="a8e98-108">在資料表中的資料列索引。</span><span class="sxs-lookup"><span data-stu-id="a8e98-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="a8e98-109">脫銷儲存格中值的指標。</span><span class="sxs-lookup"><span data-stu-id="a8e98-109">[out] A pointer to the value in the cell.</span></span>  
 
## <a name="remarks"></a><span data-ttu-id="a8e98-110">備註</span><span class="sxs-lookup"><span data-stu-id="a8e98-110">Remarks</span></span>

<span data-ttu-id="a8e98-111">透過`pVal`傳回之值的 interpretion 取決於資料行的類型。</span><span class="sxs-lookup"><span data-stu-id="a8e98-111">The interpretion of the value returned through `pVal` depends on the column's type.</span></span> <span data-ttu-id="a8e98-112">您可以藉由呼叫 IMetaDataTables 來判斷資料行類型。 [GetColumnInfo](imetadatatables-getcolumninfo-method.md)。</span><span class="sxs-lookup"><span data-stu-id="a8e98-112">The column type can be determined by calling [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span></span>

- <span data-ttu-id="a8e98-113">**GetColumn**方法會自動將**Rid**或**CodedToken**類型的資料行轉換成完整 32 `mdToken`位的值。</span><span class="sxs-lookup"><span data-stu-id="a8e98-113">The **GetColumn** method automatically converts columns of type **Rid** or **CodedToken** to full 32-bit `mdToken` values.</span></span>
- <span data-ttu-id="a8e98-114">它也會自動將8位或16位的值轉換成完整的32位值。</span><span class="sxs-lookup"><span data-stu-id="a8e98-114">It also automatically converts 8-bit or 16-bit values to full 32-bit values.</span></span> 
- <span data-ttu-id="a8e98-115">若是*堆積*類型的資料行，傳回的*pVal*將會是對應堆積的索引。</span><span class="sxs-lookup"><span data-stu-id="a8e98-115">For *heap* type columns, the returned *pVal* will be an index into the corresponding heap.</span></span>

| <span data-ttu-id="a8e98-116">資料行類型</span><span class="sxs-lookup"><span data-stu-id="a8e98-116">Column type</span></span>              | <span data-ttu-id="a8e98-117">pVal 包含</span><span class="sxs-lookup"><span data-stu-id="a8e98-117">pVal contains</span></span> | <span data-ttu-id="a8e98-118">註解</span><span class="sxs-lookup"><span data-stu-id="a8e98-118">Comment</span></span>                          |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="a8e98-119">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="a8e98-119">`0`..`iRidMax`</span></span><br><span data-ttu-id="a8e98-120">（0到63）</span><span class="sxs-lookup"><span data-stu-id="a8e98-120">(0..63)</span></span>  | <span data-ttu-id="a8e98-121">mdToken</span><span class="sxs-lookup"><span data-stu-id="a8e98-121">mdToken</span></span>     | <span data-ttu-id="a8e98-122">*pVal*會包含完整的 Token。</span><span class="sxs-lookup"><span data-stu-id="a8e98-122">*pVal* will contain a full Token.</span></span> <span data-ttu-id="a8e98-123">函式會自動將 Rid 轉換成完整 token。</span><span class="sxs-lookup"><span data-stu-id="a8e98-123">The function automatically converts the Rid into a full token.</span></span> |
| <span data-ttu-id="a8e98-124">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="a8e98-124">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="a8e98-125">（64. 95）</span><span class="sxs-lookup"><span data-stu-id="a8e98-125">(64..95)</span></span> | <span data-ttu-id="a8e98-126">mdToken</span><span class="sxs-lookup"><span data-stu-id="a8e98-126">mdToken</span></span> | <span data-ttu-id="a8e98-127">傳回時， *pVal*會包含完整的 Token。</span><span class="sxs-lookup"><span data-stu-id="a8e98-127">Upon return, *pVal* will contain a full Token.</span></span> <span data-ttu-id="a8e98-128">函式會自動將 CodedToken 解壓縮至完整 token。</span><span class="sxs-lookup"><span data-stu-id="a8e98-128">The function automatically decompresses the CodedToken into a full token.</span></span> |
| <span data-ttu-id="a8e98-129">`iSHORT`（96）</span><span class="sxs-lookup"><span data-stu-id="a8e98-129">`iSHORT` (96)</span></span>            | <span data-ttu-id="a8e98-130">Int16</span><span class="sxs-lookup"><span data-stu-id="a8e98-130">Int16</span></span>         | <span data-ttu-id="a8e98-131">自動將簽章延伸至32位。</span><span class="sxs-lookup"><span data-stu-id="a8e98-131">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="a8e98-132">`iUSHORT`（97）</span><span class="sxs-lookup"><span data-stu-id="a8e98-132">`iUSHORT` (97)</span></span>           | <span data-ttu-id="a8e98-133">UInt16</span><span class="sxs-lookup"><span data-stu-id="a8e98-133">UInt16</span></span>        | <span data-ttu-id="a8e98-134">自動將簽章延伸至32位。</span><span class="sxs-lookup"><span data-stu-id="a8e98-134">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="a8e98-135">`iLONG`（98）</span><span class="sxs-lookup"><span data-stu-id="a8e98-135">`iLONG` (98)</span></span>             | <span data-ttu-id="a8e98-136">Int32</span><span class="sxs-lookup"><span data-stu-id="a8e98-136">Int32</span></span>         |                                        | 
| <span data-ttu-id="a8e98-137">`iULONG`（99）</span><span class="sxs-lookup"><span data-stu-id="a8e98-137">`iULONG` (99)</span></span>            | <span data-ttu-id="a8e98-138">UInt32</span><span class="sxs-lookup"><span data-stu-id="a8e98-138">UInt32</span></span>        |                                        |
| <span data-ttu-id="a8e98-139">`iBYTE`（100）</span><span class="sxs-lookup"><span data-stu-id="a8e98-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="a8e98-140">Byte</span><span class="sxs-lookup"><span data-stu-id="a8e98-140">Byte</span></span>          | <span data-ttu-id="a8e98-141">自動將簽章延伸至32位。</span><span class="sxs-lookup"><span data-stu-id="a8e98-141">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="a8e98-142">`iSTRING`（101）</span><span class="sxs-lookup"><span data-stu-id="a8e98-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="a8e98-143">字串堆積索引</span><span class="sxs-lookup"><span data-stu-id="a8e98-143">String heap index</span></span> | <span data-ttu-id="a8e98-144">*pVal*是字串堆積中的索引。</span><span class="sxs-lookup"><span data-stu-id="a8e98-144">*pVal* is an index into the String heap.</span></span> <span data-ttu-id="a8e98-145">請使用[IMetadataTables：： GetString](imetadatatables-getstring-method.md)來取得實際的資料行字串值。</span><span class="sxs-lookup"><span data-stu-id="a8e98-145">Use [IMetadataTables::GetString](imetadatatables-getstring-method.md) to get the actual column String value.</span></span> |
| <span data-ttu-id="a8e98-146">`iGUID`（102）</span><span class="sxs-lookup"><span data-stu-id="a8e98-146">`iGUID` (102)</span></span>            | <span data-ttu-id="a8e98-147">Guid 堆積索引</span><span class="sxs-lookup"><span data-stu-id="a8e98-147">Guid heap index</span></span> | <span data-ttu-id="a8e98-148">*pVal*是 Guid 堆積中的索引。</span><span class="sxs-lookup"><span data-stu-id="a8e98-148">*pVal* is an index into the Guid heap.</span></span> <span data-ttu-id="a8e98-149">請使用[IMetadataTables：： GetGuid](imetadatatables-getguid-method.md)來取得實際的資料行 Guid 值。</span><span class="sxs-lookup"><span data-stu-id="a8e98-149">Use [IMetadataTables::GetGuid](imetadatatables-getguid-method.md) to get the actual column Guid value.</span></span> |
| <span data-ttu-id="a8e98-150">`iBLOB`（103）</span><span class="sxs-lookup"><span data-stu-id="a8e98-150">`iBLOB` (103)</span></span>            | <span data-ttu-id="a8e98-151">Blob 堆積索引</span><span class="sxs-lookup"><span data-stu-id="a8e98-151">Blob heap index</span></span> | <span data-ttu-id="a8e98-152">*pVal*是 Blob 堆積中的索引。</span><span class="sxs-lookup"><span data-stu-id="a8e98-152">*pVal* is an index into the Blob heap.</span></span> <span data-ttu-id="a8e98-153">請使用[IMetadataTables：： GetBlob](imetadatatables-getblob-method.md)來取得實際的資料行 Blob 值。</span><span class="sxs-lookup"><span data-stu-id="a8e98-153">Use [IMetadataTables::GetBlob](imetadatatables-getblob-method.md) to get the actual column Blob value.</span></span> |
  
## <a name="requirements"></a><span data-ttu-id="a8e98-154">需求</span><span class="sxs-lookup"><span data-stu-id="a8e98-154">Requirements</span></span>  
 <span data-ttu-id="a8e98-155">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a8e98-155">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8e98-156">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="a8e98-156">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a8e98-157">**LIBRARY:** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="a8e98-157">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a8e98-158">**.NET Framework 版本**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8e98-158">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8e98-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8e98-159">See also</span></span>

- [<span data-ttu-id="a8e98-160">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="a8e98-160">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="a8e98-161">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="a8e98-161">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

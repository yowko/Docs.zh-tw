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
ms.openlocfilehash: f43d4d1547cbe92f325950e1697dada83b42c4f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177131"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="1fc1b-102">IMetaDataTables::GetColumn 方法</span><span class="sxs-lookup"><span data-stu-id="1fc1b-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="1fc1b-103">獲取指向給定表中指定列和行儲存格中包含的值的指標。</span><span class="sxs-lookup"><span data-stu-id="1fc1b-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fc1b-104">語法</span><span class="sxs-lookup"><span data-stu-id="1fc1b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetColumn (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1fc1b-105">參數</span><span class="sxs-lookup"><span data-stu-id="1fc1b-105">Parameters</span></span>

 `ixTbl`  
 <span data-ttu-id="1fc1b-106">[在]表的索引。</span><span class="sxs-lookup"><span data-stu-id="1fc1b-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="1fc1b-107">[在]表中列的索引。</span><span class="sxs-lookup"><span data-stu-id="1fc1b-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="1fc1b-108">[在]表中行的索引。</span><span class="sxs-lookup"><span data-stu-id="1fc1b-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="1fc1b-109">[出]指向儲存格中值的指標。</span><span class="sxs-lookup"><span data-stu-id="1fc1b-109">[out] A pointer to the value in the cell.</span></span>  

## <a name="remarks"></a><span data-ttu-id="1fc1b-110">備註</span><span class="sxs-lookup"><span data-stu-id="1fc1b-110">Remarks</span></span>

<span data-ttu-id="1fc1b-111">返回的值的解釋`pVal`取決於列的類型。</span><span class="sxs-lookup"><span data-stu-id="1fc1b-111">The interpretion of the value returned through `pVal` depends on the column's type.</span></span> <span data-ttu-id="1fc1b-112">可以通過調用[IMetaDataTables](imetadatatables-getcolumninfo-method.md)來確定列類型。</span><span class="sxs-lookup"><span data-stu-id="1fc1b-112">The column type can be determined by calling [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span></span>

- <span data-ttu-id="1fc1b-113">**GetColumn**方法會自動將 **"Rid"** 或"**編碼權杖"** 類型的列轉換為完整的 32 位`mdToken`值。</span><span class="sxs-lookup"><span data-stu-id="1fc1b-113">The **GetColumn** method automatically converts columns of type **Rid** or **CodedToken** to full 32-bit `mdToken` values.</span></span>
- <span data-ttu-id="1fc1b-114">它還會自動將 8 位或 16 位值轉換為完整的 32 位值。</span><span class="sxs-lookup"><span data-stu-id="1fc1b-114">It also automatically converts 8-bit or 16-bit values to full 32-bit values.</span></span>
- <span data-ttu-id="1fc1b-115">對於*堆*類型列，返回的*pVal*將是相應堆中的索引。</span><span class="sxs-lookup"><span data-stu-id="1fc1b-115">For *heap* type columns, the returned *pVal* will be an index into the corresponding heap.</span></span>

| <span data-ttu-id="1fc1b-116">資料行類型</span><span class="sxs-lookup"><span data-stu-id="1fc1b-116">Column type</span></span>              | <span data-ttu-id="1fc1b-117">pVal 包含</span><span class="sxs-lookup"><span data-stu-id="1fc1b-117">pVal contains</span></span> | <span data-ttu-id="1fc1b-118">註解</span><span class="sxs-lookup"><span data-stu-id="1fc1b-118">Comment</span></span>                          |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="1fc1b-119">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="1fc1b-119">`0`..`iRidMax`</span></span><br><span data-ttu-id="1fc1b-120">(0..63)</span><span class="sxs-lookup"><span data-stu-id="1fc1b-120">(0..63)</span></span>  | <span data-ttu-id="1fc1b-121">mdToken</span><span class="sxs-lookup"><span data-stu-id="1fc1b-121">mdToken</span></span>     | <span data-ttu-id="1fc1b-122">*pVal*將包含一個完整的權杖。</span><span class="sxs-lookup"><span data-stu-id="1fc1b-122">*pVal* will contain a full Token.</span></span> <span data-ttu-id="1fc1b-123">該函數會自動將 Rid 轉換為完整權杖。</span><span class="sxs-lookup"><span data-stu-id="1fc1b-123">The function automatically converts the Rid into a full token.</span></span> |
| <span data-ttu-id="1fc1b-124">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="1fc1b-124">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="1fc1b-125">(64..95)</span><span class="sxs-lookup"><span data-stu-id="1fc1b-125">(64..95)</span></span> | <span data-ttu-id="1fc1b-126">mdToken</span><span class="sxs-lookup"><span data-stu-id="1fc1b-126">mdToken</span></span> | <span data-ttu-id="1fc1b-127">返回後 *，pVal*將包含一個完整的權杖。</span><span class="sxs-lookup"><span data-stu-id="1fc1b-127">Upon return, *pVal* will contain a full Token.</span></span> <span data-ttu-id="1fc1b-128">該函數會自動將編碼權杖解壓縮為完整權杖。</span><span class="sxs-lookup"><span data-stu-id="1fc1b-128">The function automatically decompresses the CodedToken into a full token.</span></span> |
| <span data-ttu-id="1fc1b-129">`iSHORT`(96)</span><span class="sxs-lookup"><span data-stu-id="1fc1b-129">`iSHORT` (96)</span></span>            | <span data-ttu-id="1fc1b-130">Int16</span><span class="sxs-lookup"><span data-stu-id="1fc1b-130">Int16</span></span>         | <span data-ttu-id="1fc1b-131">自動簽名擴展到 32 位。</span><span class="sxs-lookup"><span data-stu-id="1fc1b-131">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="1fc1b-132">`iUSHORT`(97)</span><span class="sxs-lookup"><span data-stu-id="1fc1b-132">`iUSHORT` (97)</span></span>           | <span data-ttu-id="1fc1b-133">UInt16</span><span class="sxs-lookup"><span data-stu-id="1fc1b-133">UInt16</span></span>        | <span data-ttu-id="1fc1b-134">自動簽名擴展到 32 位。</span><span class="sxs-lookup"><span data-stu-id="1fc1b-134">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="1fc1b-135">`iLONG`(98)</span><span class="sxs-lookup"><span data-stu-id="1fc1b-135">`iLONG` (98)</span></span>             | <span data-ttu-id="1fc1b-136">Int32</span><span class="sxs-lookup"><span data-stu-id="1fc1b-136">Int32</span></span>         |                                        |
| <span data-ttu-id="1fc1b-137">`iULONG`(99)</span><span class="sxs-lookup"><span data-stu-id="1fc1b-137">`iULONG` (99)</span></span>            | <span data-ttu-id="1fc1b-138">UInt32</span><span class="sxs-lookup"><span data-stu-id="1fc1b-138">UInt32</span></span>        |                                        |
| <span data-ttu-id="1fc1b-139">`iBYTE`(100)</span><span class="sxs-lookup"><span data-stu-id="1fc1b-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="1fc1b-140">Byte</span><span class="sxs-lookup"><span data-stu-id="1fc1b-140">Byte</span></span>          | <span data-ttu-id="1fc1b-141">自動簽名擴展到 32 位。</span><span class="sxs-lookup"><span data-stu-id="1fc1b-141">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="1fc1b-142">`iSTRING`(101)</span><span class="sxs-lookup"><span data-stu-id="1fc1b-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="1fc1b-143">字串堆索引</span><span class="sxs-lookup"><span data-stu-id="1fc1b-143">String heap index</span></span> | <span data-ttu-id="1fc1b-144">*pVal*是字串堆中的索引。</span><span class="sxs-lookup"><span data-stu-id="1fc1b-144">*pVal* is an index into the String heap.</span></span> <span data-ttu-id="1fc1b-145">使用[IMetadataTables：：獲取String](imetadatatables-getstring-method.md)獲取實際列字串值。</span><span class="sxs-lookup"><span data-stu-id="1fc1b-145">Use [IMetadataTables::GetString](imetadatatables-getstring-method.md) to get the actual column String value.</span></span> |
| <span data-ttu-id="1fc1b-146">`iGUID`(102)</span><span class="sxs-lookup"><span data-stu-id="1fc1b-146">`iGUID` (102)</span></span>            | <span data-ttu-id="1fc1b-147">吉德堆索引</span><span class="sxs-lookup"><span data-stu-id="1fc1b-147">Guid heap index</span></span> | <span data-ttu-id="1fc1b-148">*pVal*是 Guid 堆中的索引。</span><span class="sxs-lookup"><span data-stu-id="1fc1b-148">*pVal* is an index into the Guid heap.</span></span> <span data-ttu-id="1fc1b-149">使用[IMetadataTables：：getGuid](imetadatatables-getguid-method.md)獲取實際列 Guid 值。</span><span class="sxs-lookup"><span data-stu-id="1fc1b-149">Use [IMetadataTables::GetGuid](imetadatatables-getguid-method.md) to get the actual column Guid value.</span></span> |
| <span data-ttu-id="1fc1b-150">`iBLOB`(103)</span><span class="sxs-lookup"><span data-stu-id="1fc1b-150">`iBLOB` (103)</span></span>            | <span data-ttu-id="1fc1b-151">Blob 堆索引</span><span class="sxs-lookup"><span data-stu-id="1fc1b-151">Blob heap index</span></span> | <span data-ttu-id="1fc1b-152">*pVal*是 Blob 堆中的索引。</span><span class="sxs-lookup"><span data-stu-id="1fc1b-152">*pVal* is an index into the Blob heap.</span></span> <span data-ttu-id="1fc1b-153">使用[IMetadataTables：：獲取 Blob](imetadatatables-getblob-method.md)獲取實際列 Blob 值。</span><span class="sxs-lookup"><span data-stu-id="1fc1b-153">Use [IMetadataTables::GetBlob](imetadatatables-getblob-method.md) to get the actual column Blob value.</span></span> |
  
## <a name="requirements"></a><span data-ttu-id="1fc1b-154">需求</span><span class="sxs-lookup"><span data-stu-id="1fc1b-154">Requirements</span></span>  
 <span data-ttu-id="1fc1b-155">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1fc1b-155">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fc1b-156">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="1fc1b-156">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1fc1b-157">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1fc1b-157">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1fc1b-158">**.NET 框架版本**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fc1b-158">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fc1b-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1fc1b-159">See also</span></span>

- [<span data-ttu-id="1fc1b-160">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="1fc1b-160">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="1fc1b-161">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="1fc1b-161">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

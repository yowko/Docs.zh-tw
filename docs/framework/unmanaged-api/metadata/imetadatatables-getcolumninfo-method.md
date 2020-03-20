---
title: IMetaDataTables::GetColumnInfo 方法
ms.date: 10/10/2019
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
ms.openlocfilehash: cc8aac32149fed952737d928e16a8f6efc448c79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177127"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="d9c86-102">IMetaDataTables::GetColumnInfo 方法</span><span class="sxs-lookup"><span data-stu-id="d9c86-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="d9c86-103">獲取有關指定表中指定列的資料。</span><span class="sxs-lookup"><span data-stu-id="d9c86-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9c86-104">語法</span><span class="sxs-lookup"><span data-stu-id="d9c86-104">Syntax</span></span>  
  
```cpp  
HRESULT GetColumnInfo (
    [in]  ULONG        ixTbl,  
    [in]  ULONG        ixCol,  
    [out] ULONG        *poCol,  
    [out] ULONG        *pcbCol,  
    [out] ULONG        *pType,  
    [out] const char   **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9c86-105">參數</span><span class="sxs-lookup"><span data-stu-id="d9c86-105">Parameters</span></span>
=======

 `ixTbl`  
 <span data-ttu-id="d9c86-106">[在]所需表的索引。</span><span class="sxs-lookup"><span data-stu-id="d9c86-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="d9c86-107">[在]所需列的索引。</span><span class="sxs-lookup"><span data-stu-id="d9c86-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="d9c86-108">[出]指向行中列偏移的指標。</span><span class="sxs-lookup"><span data-stu-id="d9c86-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="d9c86-109">[出]指向列的大小（以位元組為單位）的指標。</span><span class="sxs-lookup"><span data-stu-id="d9c86-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="d9c86-110">[出]指向列中數值型別的指標。</span><span class="sxs-lookup"><span data-stu-id="d9c86-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="d9c86-111">[出]指向列名稱的指標。</span><span class="sxs-lookup"><span data-stu-id="d9c86-111">[out] A pointer to a pointer to the column name.</span></span>  

## <a name="remarks"></a><span data-ttu-id="d9c86-112">備註</span><span class="sxs-lookup"><span data-stu-id="d9c86-112">Remarks</span></span>

<span data-ttu-id="d9c86-113">返回的列類型在值範圍內：</span><span class="sxs-lookup"><span data-stu-id="d9c86-113">The returned column type falls within a range of values:</span></span>

| <span data-ttu-id="d9c86-114">p類型</span><span class="sxs-lookup"><span data-stu-id="d9c86-114">pType</span></span>                    | <span data-ttu-id="d9c86-115">描述</span><span class="sxs-lookup"><span data-stu-id="d9c86-115">Description</span></span>   | <span data-ttu-id="d9c86-116">説明器功能</span><span class="sxs-lookup"><span data-stu-id="d9c86-116">Helper function</span></span>                   |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="d9c86-117">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="d9c86-117">`0`..`iRidMax`</span></span><br><span data-ttu-id="d9c86-118">(0..63)</span><span class="sxs-lookup"><span data-stu-id="d9c86-118">(0..63)</span></span>   | <span data-ttu-id="d9c86-119">擺脫</span><span class="sxs-lookup"><span data-stu-id="d9c86-119">Rid</span></span>           | <span data-ttu-id="d9c86-120">**IsRidType**</span><span class="sxs-lookup"><span data-stu-id="d9c86-120">**IsRidType**</span></span><br><span data-ttu-id="d9c86-121">**IsRidorToken**</span><span class="sxs-lookup"><span data-stu-id="d9c86-121">**IsRidOrToken**</span></span> |
| <span data-ttu-id="d9c86-122">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="d9c86-122">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="d9c86-123">(64..95)</span><span class="sxs-lookup"><span data-stu-id="d9c86-123">(64..95)</span></span> | <span data-ttu-id="d9c86-124">編碼權杖</span><span class="sxs-lookup"><span data-stu-id="d9c86-124">Coded token</span></span> | <span data-ttu-id="d9c86-125">**已編碼權杖類型**</span><span class="sxs-lookup"><span data-stu-id="d9c86-125">**IsCodedTokenType**</span></span> <br><span data-ttu-id="d9c86-126">**IsRidorToken**</span><span class="sxs-lookup"><span data-stu-id="d9c86-126">**IsRidOrToken**</span></span> |
| <span data-ttu-id="d9c86-127">`iSHORT`(96)</span><span class="sxs-lookup"><span data-stu-id="d9c86-127">`iSHORT` (96)</span></span>            | <span data-ttu-id="d9c86-128">Int16</span><span class="sxs-lookup"><span data-stu-id="d9c86-128">Int16</span></span>         | <span data-ttu-id="d9c86-129">**固定類型**</span><span class="sxs-lookup"><span data-stu-id="d9c86-129">**IsFixedType**</span></span>                   |
| <span data-ttu-id="d9c86-130">`iUSHORT`(97)</span><span class="sxs-lookup"><span data-stu-id="d9c86-130">`iUSHORT` (97)</span></span>           | <span data-ttu-id="d9c86-131">UInt16</span><span class="sxs-lookup"><span data-stu-id="d9c86-131">UInt16</span></span>        | <span data-ttu-id="d9c86-132">**固定類型**</span><span class="sxs-lookup"><span data-stu-id="d9c86-132">**IsFixedType**</span></span>                   |
| <span data-ttu-id="d9c86-133">`iLONG`(98)</span><span class="sxs-lookup"><span data-stu-id="d9c86-133">`iLONG` (98)</span></span>             | <span data-ttu-id="d9c86-134">Int32</span><span class="sxs-lookup"><span data-stu-id="d9c86-134">Int32</span></span>         | <span data-ttu-id="d9c86-135">**固定類型**</span><span class="sxs-lookup"><span data-stu-id="d9c86-135">**IsFixedType**</span></span>                   |
| <span data-ttu-id="d9c86-136">`iULONG`(99)</span><span class="sxs-lookup"><span data-stu-id="d9c86-136">`iULONG` (99)</span></span>            | <span data-ttu-id="d9c86-137">UInt32</span><span class="sxs-lookup"><span data-stu-id="d9c86-137">UInt32</span></span>        | <span data-ttu-id="d9c86-138">**固定類型**</span><span class="sxs-lookup"><span data-stu-id="d9c86-138">**IsFixedType**</span></span>                   |
| <span data-ttu-id="d9c86-139">`iBYTE`(100)</span><span class="sxs-lookup"><span data-stu-id="d9c86-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="d9c86-140">Byte</span><span class="sxs-lookup"><span data-stu-id="d9c86-140">Byte</span></span>          | <span data-ttu-id="d9c86-141">**固定類型**</span><span class="sxs-lookup"><span data-stu-id="d9c86-141">**IsFixedType**</span></span>                   |
| <span data-ttu-id="d9c86-142">`iSTRING`(101)</span><span class="sxs-lookup"><span data-stu-id="d9c86-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="d9c86-143">String</span><span class="sxs-lookup"><span data-stu-id="d9c86-143">String</span></span>        | <span data-ttu-id="d9c86-144">**IsHeap 類型**</span><span class="sxs-lookup"><span data-stu-id="d9c86-144">**IsHeapType**</span></span>                    |
| <span data-ttu-id="d9c86-145">`iGUID`(102)</span><span class="sxs-lookup"><span data-stu-id="d9c86-145">`iGUID` (102)</span></span>            | <span data-ttu-id="d9c86-146">Guid</span><span class="sxs-lookup"><span data-stu-id="d9c86-146">Guid</span></span>          | <span data-ttu-id="d9c86-147">**IsHeap 類型**</span><span class="sxs-lookup"><span data-stu-id="d9c86-147">**IsHeapType**</span></span>                    |
| <span data-ttu-id="d9c86-148">`iBLOB`(103)</span><span class="sxs-lookup"><span data-stu-id="d9c86-148">`iBLOB` (103)</span></span>            | <span data-ttu-id="d9c86-149">Blob</span><span class="sxs-lookup"><span data-stu-id="d9c86-149">Blob</span></span>          | <span data-ttu-id="d9c86-150">**IsHeap 類型**</span><span class="sxs-lookup"><span data-stu-id="d9c86-150">**IsHeapType**</span></span>                    |

<span data-ttu-id="d9c86-151">可以使用以下方式讀取堆中存儲*的值（即* `IsHeapType == true`），</span><span class="sxs-lookup"><span data-stu-id="d9c86-151">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span></span>

- <span data-ttu-id="d9c86-152">`iSTRING`**：IMetadatatables.GetString**</span><span class="sxs-lookup"><span data-stu-id="d9c86-152">`iSTRING`: **IMetadataTables.GetString**</span></span>
- <span data-ttu-id="d9c86-153">`iGUID`**：IMetadatatables.GetGUID**</span><span class="sxs-lookup"><span data-stu-id="d9c86-153">`iGUID`: **IMetadataTables.GetGUID**</span></span>
- <span data-ttu-id="d9c86-154">`iBLOB`**：IMetadatatables.獲取Blob**</span><span class="sxs-lookup"><span data-stu-id="d9c86-154">`iBLOB`: **IMetadataTables.GetBlob**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d9c86-155">要使用上表中定義的常量，請包括`#define _DEFINE_META_DATA_META_CONSTANTS`*cor.h*標標頭檔提供的指令。</span><span class="sxs-lookup"><span data-stu-id="d9c86-155">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span></span>

## <a name="requirements"></a><span data-ttu-id="d9c86-156">需求</span><span class="sxs-lookup"><span data-stu-id="d9c86-156">Requirements</span></span>  
 <span data-ttu-id="d9c86-157">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d9c86-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9c86-158">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="d9c86-158">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d9c86-159">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d9c86-159">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d9c86-160">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9c86-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9c86-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9c86-161">See also</span></span>

- [<span data-ttu-id="d9c86-162">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="d9c86-162">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="d9c86-163">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="d9c86-163">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

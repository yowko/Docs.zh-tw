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
ms.openlocfilehash: 227d9ab67ab3091508232be3018ca520a6b5dcc6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711048"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="68ac7-102">IMetaDataTables::GetColumnInfo 方法</span><span class="sxs-lookup"><span data-stu-id="68ac7-102">IMetaDataTables::GetColumnInfo Method</span></span>

<span data-ttu-id="68ac7-103">取得指定之資料表中指定之資料行的相關資料。</span><span class="sxs-lookup"><span data-stu-id="68ac7-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68ac7-104">語法</span><span class="sxs-lookup"><span data-stu-id="68ac7-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="68ac7-105">參數</span><span class="sxs-lookup"><span data-stu-id="68ac7-105">Parameters</span></span>

=======

 `ixTbl`  
 <span data-ttu-id="68ac7-106">在所需資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="68ac7-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="68ac7-107">在所需資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="68ac7-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="68ac7-108">擴展資料列中資料行位移的指標。</span><span class="sxs-lookup"><span data-stu-id="68ac7-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="68ac7-109">擴展資料行大小的指標，以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="68ac7-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="68ac7-110">擴展資料行中值的型別指標。</span><span class="sxs-lookup"><span data-stu-id="68ac7-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="68ac7-111">擴展指向資料行名稱之指標的指標。</span><span class="sxs-lookup"><span data-stu-id="68ac7-111">[out] A pointer to a pointer to the column name.</span></span>  

## <a name="remarks"></a><span data-ttu-id="68ac7-112">備註</span><span class="sxs-lookup"><span data-stu-id="68ac7-112">Remarks</span></span>

<span data-ttu-id="68ac7-113">傳回的資料行類型落在值的範圍內：</span><span class="sxs-lookup"><span data-stu-id="68ac7-113">The returned column type falls within a range of values:</span></span>

| <span data-ttu-id="68ac7-114">pType</span><span class="sxs-lookup"><span data-stu-id="68ac7-114">pType</span></span>                    | <span data-ttu-id="68ac7-115">描述</span><span class="sxs-lookup"><span data-stu-id="68ac7-115">Description</span></span>   | <span data-ttu-id="68ac7-116">Helper 函式</span><span class="sxs-lookup"><span data-stu-id="68ac7-116">Helper function</span></span>                   |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="68ac7-117">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="68ac7-117">`0`..`iRidMax`</span></span><br><span data-ttu-id="68ac7-118"> (0. 63) </span><span class="sxs-lookup"><span data-stu-id="68ac7-118">(0..63)</span></span>   | <span data-ttu-id="68ac7-119">擺脫</span><span class="sxs-lookup"><span data-stu-id="68ac7-119">Rid</span></span>           | <span data-ttu-id="68ac7-120">**IsRidType**</span><span class="sxs-lookup"><span data-stu-id="68ac7-120">**IsRidType**</span></span><br><span data-ttu-id="68ac7-121">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="68ac7-121">**IsRidOrToken**</span></span> |
| <span data-ttu-id="68ac7-122">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="68ac7-122">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="68ac7-123"> (64. 95) </span><span class="sxs-lookup"><span data-stu-id="68ac7-123">(64..95)</span></span> | <span data-ttu-id="68ac7-124">編碼的權杖</span><span class="sxs-lookup"><span data-stu-id="68ac7-124">Coded token</span></span> | <span data-ttu-id="68ac7-125">**IsCodedTokenType**</span><span class="sxs-lookup"><span data-stu-id="68ac7-125">**IsCodedTokenType**</span></span> <br><span data-ttu-id="68ac7-126">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="68ac7-126">**IsRidOrToken**</span></span> |
| <span data-ttu-id="68ac7-127">`iSHORT` (96) </span><span class="sxs-lookup"><span data-stu-id="68ac7-127">`iSHORT` (96)</span></span>            | <span data-ttu-id="68ac7-128">Int16</span><span class="sxs-lookup"><span data-stu-id="68ac7-128">Int16</span></span>         | <span data-ttu-id="68ac7-129">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="68ac7-129">**IsFixedType**</span></span>                   |
| <span data-ttu-id="68ac7-130">`iUSHORT` (97) </span><span class="sxs-lookup"><span data-stu-id="68ac7-130">`iUSHORT` (97)</span></span>           | <span data-ttu-id="68ac7-131">UInt16</span><span class="sxs-lookup"><span data-stu-id="68ac7-131">UInt16</span></span>        | <span data-ttu-id="68ac7-132">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="68ac7-132">**IsFixedType**</span></span>                   |
| <span data-ttu-id="68ac7-133">`iLONG` (98) </span><span class="sxs-lookup"><span data-stu-id="68ac7-133">`iLONG` (98)</span></span>             | <span data-ttu-id="68ac7-134">Int32</span><span class="sxs-lookup"><span data-stu-id="68ac7-134">Int32</span></span>         | <span data-ttu-id="68ac7-135">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="68ac7-135">**IsFixedType**</span></span>                   |
| <span data-ttu-id="68ac7-136">`iULONG` (99) </span><span class="sxs-lookup"><span data-stu-id="68ac7-136">`iULONG` (99)</span></span>            | <span data-ttu-id="68ac7-137">UInt32</span><span class="sxs-lookup"><span data-stu-id="68ac7-137">UInt32</span></span>        | <span data-ttu-id="68ac7-138">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="68ac7-138">**IsFixedType**</span></span>                   |
| <span data-ttu-id="68ac7-139">`iBYTE` (100) </span><span class="sxs-lookup"><span data-stu-id="68ac7-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="68ac7-140">Byte</span><span class="sxs-lookup"><span data-stu-id="68ac7-140">Byte</span></span>          | <span data-ttu-id="68ac7-141">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="68ac7-141">**IsFixedType**</span></span>                   |
| <span data-ttu-id="68ac7-142">`iSTRING` (101) </span><span class="sxs-lookup"><span data-stu-id="68ac7-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="68ac7-143">String</span><span class="sxs-lookup"><span data-stu-id="68ac7-143">String</span></span>        | <span data-ttu-id="68ac7-144">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="68ac7-144">**IsHeapType**</span></span>                    |
| <span data-ttu-id="68ac7-145">`iGUID` (102) </span><span class="sxs-lookup"><span data-stu-id="68ac7-145">`iGUID` (102)</span></span>            | <span data-ttu-id="68ac7-146">Guid</span><span class="sxs-lookup"><span data-stu-id="68ac7-146">Guid</span></span>          | <span data-ttu-id="68ac7-147">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="68ac7-147">**IsHeapType**</span></span>                    |
| <span data-ttu-id="68ac7-148">`iBLOB` (103) </span><span class="sxs-lookup"><span data-stu-id="68ac7-148">`iBLOB` (103)</span></span>            | <span data-ttu-id="68ac7-149">Blob</span><span class="sxs-lookup"><span data-stu-id="68ac7-149">Blob</span></span>          | <span data-ttu-id="68ac7-150">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="68ac7-150">**IsHeapType**</span></span>                    |

<span data-ttu-id="68ac7-151">儲存在 *堆積* 中的值 (也就是 `IsHeapType == true`) 可以使用下列方式讀取：</span><span class="sxs-lookup"><span data-stu-id="68ac7-151">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span></span>

- <span data-ttu-id="68ac7-152">`iSTRING`： **IMetadataTables. GetString**</span><span class="sxs-lookup"><span data-stu-id="68ac7-152">`iSTRING`: **IMetadataTables.GetString**</span></span>
- <span data-ttu-id="68ac7-153">`iGUID`： **IMetadataTables. GetGUID**</span><span class="sxs-lookup"><span data-stu-id="68ac7-153">`iGUID`: **IMetadataTables.GetGUID**</span></span>
- <span data-ttu-id="68ac7-154">`iBLOB`： **IMetadataTables. GetBlob**</span><span class="sxs-lookup"><span data-stu-id="68ac7-154">`iBLOB`: **IMetadataTables.GetBlob**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="68ac7-155">若要使用上表中定義的常數，請包含 `#define _DEFINE_META_DATA_META_CONSTANTS` *cor .h* 標頭檔所提供的指示詞。</span><span class="sxs-lookup"><span data-stu-id="68ac7-155">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span></span>

## <a name="requirements"></a><span data-ttu-id="68ac7-156">需求</span><span class="sxs-lookup"><span data-stu-id="68ac7-156">Requirements</span></span>  

 <span data-ttu-id="68ac7-157">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="68ac7-157">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68ac7-158">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="68ac7-158">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="68ac7-159">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="68ac7-159">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="68ac7-160">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68ac7-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68ac7-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68ac7-161">See also</span></span>

- [<span data-ttu-id="68ac7-162">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="68ac7-162">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="68ac7-163">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="68ac7-163">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)

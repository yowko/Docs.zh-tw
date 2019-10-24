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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dd67d9faafedf4fb92c69618d4464ebb2ce47dcc
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774251"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="09695-102">IMetaDataTables::GetColumnInfo 方法</span><span class="sxs-lookup"><span data-stu-id="09695-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="09695-103">取得指定資料表中指定之資料行的相關資料。</span><span class="sxs-lookup"><span data-stu-id="09695-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09695-104">語法</span><span class="sxs-lookup"><span data-stu-id="09695-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="09695-105">參數</span><span class="sxs-lookup"><span data-stu-id="09695-105">Parameters</span></span>
=======

 `ixTbl`  
 <span data-ttu-id="09695-106">在所需資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="09695-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="09695-107">在所需資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="09695-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="09695-108">脫銷資料列中資料行位移的指標。</span><span class="sxs-lookup"><span data-stu-id="09695-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="09695-109">脫銷資料行大小的指標，以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="09695-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="09695-110">脫銷資料行中數值型別的指標。</span><span class="sxs-lookup"><span data-stu-id="09695-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="09695-111">脫銷指向資料行名稱之指標的指標。</span><span class="sxs-lookup"><span data-stu-id="09695-111">[out] A pointer to a pointer to the column name.</span></span>  
 
## <a name="remarks"></a><span data-ttu-id="09695-112">備註</span><span class="sxs-lookup"><span data-stu-id="09695-112">Remarks</span></span>

<span data-ttu-id="09695-113">傳回的資料行類型落在值的範圍內：</span><span class="sxs-lookup"><span data-stu-id="09695-113">The returned column type falls within a range of values:</span></span>

| <span data-ttu-id="09695-114">pType</span><span class="sxs-lookup"><span data-stu-id="09695-114">pType</span></span>                    | <span data-ttu-id="09695-115">描述</span><span class="sxs-lookup"><span data-stu-id="09695-115">Description</span></span>   | <span data-ttu-id="09695-116">Helper 函式</span><span class="sxs-lookup"><span data-stu-id="09695-116">Helper function</span></span>                   |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="09695-117">`0`。`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="09695-117">`0`..`iRidMax`</span></span><br><span data-ttu-id="09695-118">（0到63）</span><span class="sxs-lookup"><span data-stu-id="09695-118">(0..63)</span></span>   | <span data-ttu-id="09695-119">掉</span><span class="sxs-lookup"><span data-stu-id="09695-119">Rid</span></span>           | <span data-ttu-id="09695-120">**IsRidType**</span><span class="sxs-lookup"><span data-stu-id="09695-120">**IsRidType**</span></span><br><span data-ttu-id="09695-121">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="09695-121">**IsRidOrToken**</span></span> |
| <span data-ttu-id="09695-122">`iCodedToken`。`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="09695-122">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="09695-123">（64. 95）</span><span class="sxs-lookup"><span data-stu-id="09695-123">(64..95)</span></span> | <span data-ttu-id="09695-124">程式碼標記</span><span class="sxs-lookup"><span data-stu-id="09695-124">Coded token</span></span> | <span data-ttu-id="09695-125">**IsCodedTokenType**</span><span class="sxs-lookup"><span data-stu-id="09695-125">**IsCodedTokenType**</span></span> <br><span data-ttu-id="09695-126">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="09695-126">**IsRidOrToken**</span></span> |
| <span data-ttu-id="09695-127">`iSHORT` （96）</span><span class="sxs-lookup"><span data-stu-id="09695-127">`iSHORT` (96)</span></span>            | <span data-ttu-id="09695-128">Int16</span><span class="sxs-lookup"><span data-stu-id="09695-128">Int16</span></span>         | <span data-ttu-id="09695-129">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="09695-129">**IsFixedType**</span></span>                   |
| <span data-ttu-id="09695-130">`iUSHORT` （97）</span><span class="sxs-lookup"><span data-stu-id="09695-130">`iUSHORT` (97)</span></span>           | <span data-ttu-id="09695-131">UInt16</span><span class="sxs-lookup"><span data-stu-id="09695-131">UInt16</span></span>        | <span data-ttu-id="09695-132">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="09695-132">**IsFixedType**</span></span>                   |
| <span data-ttu-id="09695-133">`iLONG` （98）</span><span class="sxs-lookup"><span data-stu-id="09695-133">`iLONG` (98)</span></span>             | <span data-ttu-id="09695-134">Int32</span><span class="sxs-lookup"><span data-stu-id="09695-134">Int32</span></span>         | <span data-ttu-id="09695-135">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="09695-135">**IsFixedType**</span></span>                   |
| <span data-ttu-id="09695-136">`iULONG` （99）</span><span class="sxs-lookup"><span data-stu-id="09695-136">`iULONG` (99)</span></span>            | <span data-ttu-id="09695-137">UInt32</span><span class="sxs-lookup"><span data-stu-id="09695-137">UInt32</span></span>        | <span data-ttu-id="09695-138">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="09695-138">**IsFixedType**</span></span>                   |
| <span data-ttu-id="09695-139">`iBYTE` （100）</span><span class="sxs-lookup"><span data-stu-id="09695-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="09695-140">Byte</span><span class="sxs-lookup"><span data-stu-id="09695-140">Byte</span></span>          | <span data-ttu-id="09695-141">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="09695-141">**IsFixedType**</span></span>                   |
| <span data-ttu-id="09695-142">`iSTRING` （101）</span><span class="sxs-lookup"><span data-stu-id="09695-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="09695-143">String</span><span class="sxs-lookup"><span data-stu-id="09695-143">String</span></span>        | <span data-ttu-id="09695-144">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="09695-144">**IsHeapType**</span></span>                    |
| <span data-ttu-id="09695-145">`iGUID` （102）</span><span class="sxs-lookup"><span data-stu-id="09695-145">`iGUID` (102)</span></span>            | <span data-ttu-id="09695-146">GUID</span><span class="sxs-lookup"><span data-stu-id="09695-146">Guid</span></span>          | <span data-ttu-id="09695-147">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="09695-147">**IsHeapType**</span></span>                    |
| <span data-ttu-id="09695-148">`iBLOB` （103）</span><span class="sxs-lookup"><span data-stu-id="09695-148">`iBLOB` (103)</span></span>            | <span data-ttu-id="09695-149">Blob</span><span class="sxs-lookup"><span data-stu-id="09695-149">Blob</span></span>          | <span data-ttu-id="09695-150">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="09695-150">**IsHeapType**</span></span>                    |

<span data-ttu-id="09695-151">您可以使用下列方式來讀取儲存在*堆積*中的值（也就是 `IsHeapType == true`）：</span><span class="sxs-lookup"><span data-stu-id="09695-151">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span></span>

- <span data-ttu-id="09695-152">`iSTRING`： **IMetadataTables. GetString**</span><span class="sxs-lookup"><span data-stu-id="09695-152">`iSTRING`: **IMetadataTables.GetString**</span></span>
- <span data-ttu-id="09695-153">`iGUID`： **IMetadataTables. GetGUID**</span><span class="sxs-lookup"><span data-stu-id="09695-153">`iGUID`: **IMetadataTables.GetGUID**</span></span>
- <span data-ttu-id="09695-154">`iBLOB`： **IMetadataTables. GetBlob**</span><span class="sxs-lookup"><span data-stu-id="09695-154">`iBLOB`: **IMetadataTables.GetBlob**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="09695-155">若要使用上表中所定義的常數，請包含*cor*標頭檔所提供的指示詞 `#define _DEFINE_META_DATA_META_CONSTANTS`。</span><span class="sxs-lookup"><span data-stu-id="09695-155">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span></span>

## <a name="requirements"></a><span data-ttu-id="09695-156">需求</span><span class="sxs-lookup"><span data-stu-id="09695-156">Requirements</span></span>  
 <span data-ttu-id="09695-157">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="09695-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09695-158">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="09695-158">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="09695-159">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="09695-159">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="09695-160">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09695-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09695-161">請參閱</span><span class="sxs-lookup"><span data-stu-id="09695-161">See also</span></span>

- [<span data-ttu-id="09695-162">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="09695-162">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="09695-163">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="09695-163">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

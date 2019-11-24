---
title: COR_FIELD_OFFSET 結構
ms.date: 03/30/2017
api_name:
- COR_FIELD_OFFSET
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_FIELD_OFFSET
helpviewer_keywords:
- COR_FIELD_OFFSET structure [.NET Framework metadata]
ms.assetid: cced5298-277f-4a5a-8ecf-a0050c1096ea
topic_type:
- apiref
ms.openlocfilehash: 646952d5cd55b74081a0ba6171a6eee6b0138512
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443958"
---
# <a name="cor_field_offset-structure"></a><span data-ttu-id="0c7af-102">COR_FIELD_OFFSET 結構</span><span class="sxs-lookup"><span data-stu-id="0c7af-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="0c7af-103">儲存指定欄位的位移 (在類別中)。</span><span class="sxs-lookup"><span data-stu-id="0c7af-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c7af-104">語法</span><span class="sxs-lookup"><span data-stu-id="0c7af-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="0c7af-105">Members</span><span class="sxs-lookup"><span data-stu-id="0c7af-105">Members</span></span>  
  
|<span data-ttu-id="0c7af-106">成員</span><span class="sxs-lookup"><span data-stu-id="0c7af-106">Member</span></span>|<span data-ttu-id="0c7af-107">描述</span><span class="sxs-lookup"><span data-stu-id="0c7af-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="0c7af-108">An `mdFieldDef` metadata token that represents the field.</span><span class="sxs-lookup"><span data-stu-id="0c7af-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="0c7af-109">The field's offset within its class.</span><span class="sxs-lookup"><span data-stu-id="0c7af-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c7af-110">備註</span><span class="sxs-lookup"><span data-stu-id="0c7af-110">Remarks</span></span>  
 <span data-ttu-id="0c7af-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span><span class="sxs-lookup"><span data-stu-id="0c7af-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c7af-112">需求</span><span class="sxs-lookup"><span data-stu-id="0c7af-112">Requirements</span></span>  
 <span data-ttu-id="0c7af-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0c7af-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c7af-114">**Header:** CorHdr.h, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="0c7af-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="0c7af-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c7af-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c7af-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="0c7af-116">See also</span></span>

- [<span data-ttu-id="0c7af-117">中繼資料結構</span><span class="sxs-lookup"><span data-stu-id="0c7af-117">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="0c7af-118">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="0c7af-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="0c7af-119">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="0c7af-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)

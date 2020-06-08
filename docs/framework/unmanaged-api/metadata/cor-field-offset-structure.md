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
ms.openlocfilehash: 8cc803e3cf1442d324bf2eed0a37d0d236acd86d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493054"
---
# <a name="cor_field_offset-structure"></a><span data-ttu-id="2a50a-102">COR_FIELD_OFFSET 結構</span><span class="sxs-lookup"><span data-stu-id="2a50a-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="2a50a-103">儲存指定欄位的位移 (在類別中)。</span><span class="sxs-lookup"><span data-stu-id="2a50a-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a50a-104">語法</span><span class="sxs-lookup"><span data-stu-id="2a50a-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="2a50a-105">成員</span><span class="sxs-lookup"><span data-stu-id="2a50a-105">Members</span></span>  
  
|<span data-ttu-id="2a50a-106">成員</span><span class="sxs-lookup"><span data-stu-id="2a50a-106">Member</span></span>|<span data-ttu-id="2a50a-107">說明</span><span class="sxs-lookup"><span data-stu-id="2a50a-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="2a50a-108">`mdFieldDef`代表欄位的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="2a50a-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="2a50a-109">欄位在其類別中的位移。</span><span class="sxs-lookup"><span data-stu-id="2a50a-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a50a-110">備註</span><span class="sxs-lookup"><span data-stu-id="2a50a-110">Remarks</span></span>  
 <span data-ttu-id="2a50a-111">[IMetaDataImport：： GetClassLayout](imetadataimport-getclasslayout-method.md)和[IMetaDataEmit：： SetClassLayout](imetadataemit-setclasslayout-method.md)方法接受型別為的參數 `COR_FIELD_OFFSET` 。</span><span class="sxs-lookup"><span data-stu-id="2a50a-111">[IMetaDataImport::GetClassLayout](imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a50a-112">規格需求</span><span class="sxs-lookup"><span data-stu-id="2a50a-112">Requirements</span></span>  
 <span data-ttu-id="2a50a-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2a50a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a50a-114">**標頭：** Corhdr.h .h，Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="2a50a-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="2a50a-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a50a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a50a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a50a-116">See also</span></span>

- [<span data-ttu-id="2a50a-117">中繼資料結構</span><span class="sxs-lookup"><span data-stu-id="2a50a-117">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="2a50a-118">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="2a50a-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="2a50a-119">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="2a50a-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)

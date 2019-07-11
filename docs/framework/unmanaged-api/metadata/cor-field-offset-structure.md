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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdfbb22d231d16be7757ff5df26a5a010928af54
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767058"
---
# <a name="corfieldoffset-structure"></a><span data-ttu-id="0a2db-102">COR_FIELD_OFFSET 結構</span><span class="sxs-lookup"><span data-stu-id="0a2db-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="0a2db-103">儲存指定欄位的位移 (在類別中)。</span><span class="sxs-lookup"><span data-stu-id="0a2db-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a2db-104">語法</span><span class="sxs-lookup"><span data-stu-id="0a2db-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="0a2db-105">成員</span><span class="sxs-lookup"><span data-stu-id="0a2db-105">Members</span></span>  
  
|<span data-ttu-id="0a2db-106">成員</span><span class="sxs-lookup"><span data-stu-id="0a2db-106">Member</span></span>|<span data-ttu-id="0a2db-107">描述</span><span class="sxs-lookup"><span data-stu-id="0a2db-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="0a2db-108">`mdFieldDef`代表欄位的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="0a2db-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="0a2db-109">欄位的位移在其類別內。</span><span class="sxs-lookup"><span data-stu-id="0a2db-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a2db-110">備註</span><span class="sxs-lookup"><span data-stu-id="0a2db-110">Remarks</span></span>  
 <span data-ttu-id="0a2db-111">[Imetadataimport:: Getclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md)並[imetadataemit:: Setclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md)方法會採用類型參數的`COR_FIELD_OFFSET`。</span><span class="sxs-lookup"><span data-stu-id="0a2db-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a2db-112">需求</span><span class="sxs-lookup"><span data-stu-id="0a2db-112">Requirements</span></span>  
 <span data-ttu-id="0a2db-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0a2db-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a2db-114">**標頭：** CorHdr.h CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="0a2db-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="0a2db-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a2db-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a2db-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a2db-116">See also</span></span>

- [<span data-ttu-id="0a2db-117">中繼資料結構</span><span class="sxs-lookup"><span data-stu-id="0a2db-117">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="0a2db-118">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="0a2db-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="0a2db-119">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="0a2db-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)

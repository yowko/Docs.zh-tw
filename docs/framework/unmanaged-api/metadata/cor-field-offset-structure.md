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
ms.openlocfilehash: 98a58c5e686a0650fa62752f6d1d50706d58e8d1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698657"
---
# <a name="corfieldoffset-structure"></a><span data-ttu-id="318c0-102">COR_FIELD_OFFSET 結構</span><span class="sxs-lookup"><span data-stu-id="318c0-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="318c0-103">儲存指定欄位的位移 (在類別中)。</span><span class="sxs-lookup"><span data-stu-id="318c0-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="318c0-104">語法</span><span class="sxs-lookup"><span data-stu-id="318c0-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="318c0-105">成員</span><span class="sxs-lookup"><span data-stu-id="318c0-105">Members</span></span>  
  
|<span data-ttu-id="318c0-106">成員</span><span class="sxs-lookup"><span data-stu-id="318c0-106">Member</span></span>|<span data-ttu-id="318c0-107">描述</span><span class="sxs-lookup"><span data-stu-id="318c0-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="318c0-108">`mdFieldDef`代表欄位的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="318c0-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="318c0-109">欄位的位移在其類別內。</span><span class="sxs-lookup"><span data-stu-id="318c0-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="318c0-110">備註</span><span class="sxs-lookup"><span data-stu-id="318c0-110">Remarks</span></span>  
 <span data-ttu-id="318c0-111">[Imetadataimport:: Getclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md)並[imetadataemit:: Setclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md)方法會採用類型參數的`COR_FIELD_OFFSET`。</span><span class="sxs-lookup"><span data-stu-id="318c0-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="318c0-112">需求</span><span class="sxs-lookup"><span data-stu-id="318c0-112">Requirements</span></span>  
 <span data-ttu-id="318c0-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="318c0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="318c0-114">**標頭：** CorHdr.h CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="318c0-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="318c0-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="318c0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="318c0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="318c0-116">See also</span></span>
- [<span data-ttu-id="318c0-117">中繼資料結構</span><span class="sxs-lookup"><span data-stu-id="318c0-117">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="318c0-118">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="318c0-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="318c0-119">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="318c0-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)

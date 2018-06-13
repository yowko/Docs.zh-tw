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
ms.openlocfilehash: 8c4a5c8efc87940b7df0bfd532beaa67931a8c81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442114"
---
# <a name="corfieldoffset-structure"></a><span data-ttu-id="25237-102">COR_FIELD_OFFSET 結構</span><span class="sxs-lookup"><span data-stu-id="25237-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="25237-103">儲存指定欄位的位移 (在類別中)。</span><span class="sxs-lookup"><span data-stu-id="25237-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25237-104">語法</span><span class="sxs-lookup"><span data-stu-id="25237-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="25237-105">成員</span><span class="sxs-lookup"><span data-stu-id="25237-105">Members</span></span>  
  
|<span data-ttu-id="25237-106">成員</span><span class="sxs-lookup"><span data-stu-id="25237-106">Member</span></span>|<span data-ttu-id="25237-107">描述</span><span class="sxs-lookup"><span data-stu-id="25237-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="25237-108">`mdFieldDef`中繼資料語彙基元所代表的欄位。</span><span class="sxs-lookup"><span data-stu-id="25237-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="25237-109">欄位的位移在其類別中。</span><span class="sxs-lookup"><span data-stu-id="25237-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25237-110">備註</span><span class="sxs-lookup"><span data-stu-id="25237-110">Remarks</span></span>  
 <span data-ttu-id="25237-111">[Imetadataimport:: Getclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md)和[imetadataemit:: Setclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md)方法會採用一個參數類型`COR_FIELD_OFFSET`。</span><span class="sxs-lookup"><span data-stu-id="25237-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25237-112">需求</span><span class="sxs-lookup"><span data-stu-id="25237-112">Requirements</span></span>  
 <span data-ttu-id="25237-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="25237-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25237-114">**標頭：** CorHdr.h、 CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="25237-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="25237-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25237-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25237-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25237-116">See Also</span></span>  
 [<span data-ttu-id="25237-117">中繼資料結構</span><span class="sxs-lookup"><span data-stu-id="25237-117">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="25237-118">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="25237-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="25237-119">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="25237-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)

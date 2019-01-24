---
title: IMetaDataImport::GetMethodSemantics 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodSemantics
helpviewer_keywords:
- GetMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::GetMethodSemantics method [.NET Framework metadata]
ms.assetid: 5e018eaa-d60e-4a0b-a2c5-8c36bd09d905
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a12310f1281da99706589894a4793c2a28c5b938
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745952"
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="365c2-102">IMetaDataImport::GetMethodSemantics 方法</span><span class="sxs-lookup"><span data-stu-id="365c2-102">IMetaDataImport::GetMethodSemantics Method</span></span>
<span data-ttu-id="365c2-103">取得旗標，表示與指定 EventProp 所參考的事件與指定的 MethodDef 語彙基元和成對的屬性所參考的方法之間的關聯性的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="365c2-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="365c2-104">語法</span><span class="sxs-lookup"><span data-stu-id="365c2-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="365c2-105">參數</span><span class="sxs-lookup"><span data-stu-id="365c2-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="365c2-106">[in]表示要取得的語意的角色資訊的方法的 MethodDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="365c2-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="365c2-107">[in]語彙基元，代表成對的屬性和事件，為其取得方法的角色。</span><span class="sxs-lookup"><span data-stu-id="365c2-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="365c2-108">[out]相關聯的語意旗標的指標。</span><span class="sxs-lookup"><span data-stu-id="365c2-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="365c2-109">這個值是從位元遮罩[CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="365c2-109">This value is a bitmask from the [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="365c2-110">備註</span><span class="sxs-lookup"><span data-stu-id="365c2-110">Remarks</span></span>  
 <span data-ttu-id="365c2-111">[Imetadataemit:: Defineproperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)方法設定方法的語意旗標。</span><span class="sxs-lookup"><span data-stu-id="365c2-111">The [IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="365c2-112">需求</span><span class="sxs-lookup"><span data-stu-id="365c2-112">Requirements</span></span>  
 <span data-ttu-id="365c2-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="365c2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="365c2-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="365c2-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="365c2-115">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="365c2-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="365c2-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="365c2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="365c2-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="365c2-117">See also</span></span>
- [<span data-ttu-id="365c2-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="365c2-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="365c2-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="365c2-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

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
ms.openlocfilehash: 57ddbd8c6935f2c0275c132e30ea175c6f198fac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200086"
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="26b6e-102">IMetaDataImport::GetMethodSemantics 方法</span><span class="sxs-lookup"><span data-stu-id="26b6e-102">IMetaDataImport::GetMethodSemantics Method</span></span>
<span data-ttu-id="26b6e-103">取得旗標，表示與指定 EventProp 所參考的事件與指定的 MethodDef 語彙基元和成對的屬性所參考的方法之間的關聯性的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="26b6e-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26b6e-104">語法</span><span class="sxs-lookup"><span data-stu-id="26b6e-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26b6e-105">參數</span><span class="sxs-lookup"><span data-stu-id="26b6e-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="26b6e-106">[in]表示要取得的語意的角色資訊的方法的 MethodDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="26b6e-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="26b6e-107">[in]語彙基元，代表成對的屬性和事件，為其取得方法的角色。</span><span class="sxs-lookup"><span data-stu-id="26b6e-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="26b6e-108">[out]相關聯的語意旗標的指標。</span><span class="sxs-lookup"><span data-stu-id="26b6e-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="26b6e-109">這個值是從位元遮罩[CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="26b6e-109">This value is a bitmask from the [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26b6e-110">備註</span><span class="sxs-lookup"><span data-stu-id="26b6e-110">Remarks</span></span>  
 <span data-ttu-id="26b6e-111">[Imetadataemit:: Defineproperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)方法設定方法的語意旗標。</span><span class="sxs-lookup"><span data-stu-id="26b6e-111">The [IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26b6e-112">需求</span><span class="sxs-lookup"><span data-stu-id="26b6e-112">Requirements</span></span>  
 <span data-ttu-id="26b6e-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="26b6e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26b6e-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="26b6e-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="26b6e-115">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="26b6e-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="26b6e-116">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="26b6e-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="26b6e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26b6e-117">See also</span></span>

- [<span data-ttu-id="26b6e-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="26b6e-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="26b6e-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="26b6e-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

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
ms.openlocfilehash: 2cfb66203d8f2d69ea188f6913a5ef34dd74791e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503597"
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="7c886-102">IMetaDataImport::GetMethodSemantics 方法</span><span class="sxs-lookup"><span data-stu-id="7c886-102">IMetaDataImport::GetMethodSemantics Method</span></span>
<span data-ttu-id="7c886-103">取得旗標，指出指定的 MethodDef token 所參考的方法與指定的 EventProp token 所參考的配對屬性與事件之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="7c886-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c886-104">語法</span><span class="sxs-lookup"><span data-stu-id="7c886-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c886-105">參數</span><span class="sxs-lookup"><span data-stu-id="7c886-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="7c886-106">在MethodDef token，代表要取得其語義角色資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="7c886-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="7c886-107">在Token，代表要取得方法角色的配對屬性和事件。</span><span class="sxs-lookup"><span data-stu-id="7c886-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="7c886-108">脫銷相關聯之語義旗標的指標。</span><span class="sxs-lookup"><span data-stu-id="7c886-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="7c886-109">這個值是[CorMethodSemanticsAttr](cormethodsemanticsattr-enumeration.md)列舉中的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="7c886-109">This value is a bitmask from the [CorMethodSemanticsAttr](cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c886-110">備註</span><span class="sxs-lookup"><span data-stu-id="7c886-110">Remarks</span></span>  
 <span data-ttu-id="7c886-111">[IMetaDataEmit：:D efineproperty](imetadataemit-defineproperty-method.md)方法會設定方法的語義旗標。</span><span class="sxs-lookup"><span data-stu-id="7c886-111">The [IMetaDataEmit::DefineProperty](imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c886-112">規格需求</span><span class="sxs-lookup"><span data-stu-id="7c886-112">Requirements</span></span>  
 <span data-ttu-id="7c886-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7c886-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c886-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="7c886-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7c886-115">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7c886-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7c886-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c886-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c886-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c886-117">See also</span></span>

- [<span data-ttu-id="7c886-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="7c886-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="7c886-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="7c886-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)

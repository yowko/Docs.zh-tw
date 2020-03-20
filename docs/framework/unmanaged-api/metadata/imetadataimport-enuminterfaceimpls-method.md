---
title: IMetaDataImport::EnumInterfaceImpls 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
ms.openlocfilehash: b535fdd5027a26cc4dd0eafec9883f0186773dd1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175495"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="272c5-102">IMetaDataImport::EnumInterfaceImpls 方法</span><span class="sxs-lookup"><span data-stu-id="272c5-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="272c5-103">枚舉指定`TypeDef`實現的所有介面。</span><span class="sxs-lookup"><span data-stu-id="272c5-103">Enumerates all interfaces implemented by the specified `TypeDef`.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="272c5-104">語法</span><span class="sxs-lookup"><span data-stu-id="272c5-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="272c5-105">參數</span><span class="sxs-lookup"><span data-stu-id="272c5-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="272c5-106">[進出]指向枚舉器的指標。</span><span class="sxs-lookup"><span data-stu-id="272c5-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="272c5-107">[在]要枚舉其表示介面實現的 TypeDef 權杖的權杖。</span><span class="sxs-lookup"><span data-stu-id="272c5-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="272c5-108">[出]用於存儲 MethodDef 權杖的陣列。</span><span class="sxs-lookup"><span data-stu-id="272c5-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="272c5-109">[在]`rImpls`陣列的最大長度。</span><span class="sxs-lookup"><span data-stu-id="272c5-109">[in] The maximum length of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="272c5-110">[出]在 中`rImpls`返回的實際權杖數。</span><span class="sxs-lookup"><span data-stu-id="272c5-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="272c5-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="272c5-111">Return Value</span></span>  
  
|<span data-ttu-id="272c5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="272c5-112">HRESULT</span></span>|<span data-ttu-id="272c5-113">描述</span><span class="sxs-lookup"><span data-stu-id="272c5-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="272c5-114">`EnumInterfaceImpls`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="272c5-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="272c5-115">沒有要枚舉的 MethodDef 權杖。</span><span class="sxs-lookup"><span data-stu-id="272c5-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="272c5-116">在這種情況下，`pcImpls`設置為零。</span><span class="sxs-lookup"><span data-stu-id="272c5-116">In that case, `pcImpls` is set to zero.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="272c5-117">備註</span><span class="sxs-lookup"><span data-stu-id="272c5-117">Remarks</span></span>

<span data-ttu-id="272c5-118">枚舉返回指定`mdInterfaceImpl``TypeDef`實現的每個介面的權杖集合。</span><span class="sxs-lookup"><span data-stu-id="272c5-118">The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`.</span></span> <span data-ttu-id="272c5-119">介面權杖按指定介面（通過`DefineTypeDef`或`SetTypeDefProps`）的順序返回。</span><span class="sxs-lookup"><span data-stu-id="272c5-119">Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`).</span></span> <span data-ttu-id="272c5-120">返回的`mdInterfaceImpl`權杖的屬性可以使用[GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md)查詢。</span><span class="sxs-lookup"><span data-stu-id="272c5-120">Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="272c5-121">需求</span><span class="sxs-lookup"><span data-stu-id="272c5-121">Requirements</span></span>  
 <span data-ttu-id="272c5-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="272c5-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="272c5-123">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="272c5-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="272c5-124">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="272c5-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="272c5-125">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="272c5-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="272c5-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="272c5-126">See also</span></span>

- [<span data-ttu-id="272c5-127">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="272c5-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="272c5-128">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="272c5-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

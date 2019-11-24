---
title: IMetaDataImport::GetInterfaceImplProps 方法
ms.date: 02/25/2019
api_name:
- IMetaDataImport.GetInterfaceImplProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type:
- apiref
ms.openlocfilehash: e5eb735acac73d694a0719c206bd22711a8c0333
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437546"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="b6df3-102">IMetaDataImport::GetInterfaceImplProps 方法</span><span class="sxs-lookup"><span data-stu-id="b6df3-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="b6df3-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span><span class="sxs-lookup"><span data-stu-id="b6df3-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="b6df3-104">語法</span><span class="sxs-lookup"><span data-stu-id="b6df3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6df3-105">參數</span><span class="sxs-lookup"><span data-stu-id="b6df3-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="b6df3-106">[in] The metadata token representing the method to return the class and interface tokens for.</span><span class="sxs-lookup"><span data-stu-id="b6df3-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="b6df3-107">[out] The metadata token representing the class that implements the method.</span><span class="sxs-lookup"><span data-stu-id="b6df3-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="b6df3-108">[out] The metadata token representing the interface that defines the implemented method.</span><span class="sxs-lookup"><span data-stu-id="b6df3-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  

## <a name="remarks"></a><span data-ttu-id="b6df3-109">備註</span><span class="sxs-lookup"><span data-stu-id="b6df3-109">Remarks</span></span>

 <span data-ttu-id="b6df3-110">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="b6df3-110">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span></span>
 
 <span data-ttu-id="b6df3-111">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span><span class="sxs-lookup"><span data-stu-id="b6df3-111">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span></span> 

- <span data-ttu-id="b6df3-112">0x02000003 (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="b6df3-112">0x02000003 (TypeDef)</span></span>
- <span data-ttu-id="b6df3-113">0x0100000A (TypeRef)</span><span class="sxs-lookup"><span data-stu-id="b6df3-113">0x0100000A (TypeRef)</span></span>
- <span data-ttu-id="b6df3-114">0x0200001C (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="b6df3-114">0x0200001C (TypeDef)</span></span>

<span data-ttu-id="b6df3-115">Conceptually, this information is stored into an interface implementation table as:</span><span class="sxs-lookup"><span data-stu-id="b6df3-115">Conceptually, this information is stored into an interface implementation table as:</span></span>

| <span data-ttu-id="b6df3-116">Row number</span><span class="sxs-lookup"><span data-stu-id="b6df3-116">Row number</span></span> | <span data-ttu-id="b6df3-117">Class token</span><span class="sxs-lookup"><span data-stu-id="b6df3-117">Class token</span></span> | <span data-ttu-id="b6df3-118">Interface token</span><span class="sxs-lookup"><span data-stu-id="b6df3-118">Interface token</span></span> |
|------------|-------------|-----------------|
| <span data-ttu-id="b6df3-119">4</span><span class="sxs-lookup"><span data-stu-id="b6df3-119">4</span></span>          |             |                 |
| <span data-ttu-id="b6df3-120">5</span><span class="sxs-lookup"><span data-stu-id="b6df3-120">5</span></span>          | <span data-ttu-id="b6df3-121">02000007</span><span class="sxs-lookup"><span data-stu-id="b6df3-121">02000007</span></span>    | <span data-ttu-id="b6df3-122">02000003</span><span class="sxs-lookup"><span data-stu-id="b6df3-122">02000003</span></span>        |
| <span data-ttu-id="b6df3-123">6</span><span class="sxs-lookup"><span data-stu-id="b6df3-123">6</span></span>          | <span data-ttu-id="b6df3-124">02000007</span><span class="sxs-lookup"><span data-stu-id="b6df3-124">02000007</span></span>    | <span data-ttu-id="b6df3-125">0100000A</span><span class="sxs-lookup"><span data-stu-id="b6df3-125">0100000A</span></span>        |
| <span data-ttu-id="b6df3-126">7</span><span class="sxs-lookup"><span data-stu-id="b6df3-126">7</span></span>          |             |                 |
| <span data-ttu-id="b6df3-127">8</span><span class="sxs-lookup"><span data-stu-id="b6df3-127">8</span></span>          | <span data-ttu-id="b6df3-128">02000007</span><span class="sxs-lookup"><span data-stu-id="b6df3-128">02000007</span></span>    | <span data-ttu-id="b6df3-129">0200001C</span><span class="sxs-lookup"><span data-stu-id="b6df3-129">0200001C</span></span>        |

<span data-ttu-id="b6df3-130">Recall, the token is a 4-byte value:</span><span class="sxs-lookup"><span data-stu-id="b6df3-130">Recall, the token is a 4-byte value:</span></span>

- <span data-ttu-id="b6df3-131">The lower 3 bytes hold the row number, or RID.</span><span class="sxs-lookup"><span data-stu-id="b6df3-131">The lower 3 bytes hold the row number, or RID.</span></span>
- <span data-ttu-id="b6df3-132">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span><span class="sxs-lookup"><span data-stu-id="b6df3-132">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span></span>

<span data-ttu-id="b6df3-133">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span><span class="sxs-lookup"><span data-stu-id="b6df3-133">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span></span> 
  
## <a name="requirements"></a><span data-ttu-id="b6df3-134">需求</span><span class="sxs-lookup"><span data-stu-id="b6df3-134">Requirements</span></span>  
 <span data-ttu-id="b6df3-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6df3-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6df3-136">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b6df3-136">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b6df3-137">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b6df3-137">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b6df3-138">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6df3-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6df3-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="b6df3-139">See also</span></span>

- [<span data-ttu-id="b6df3-140">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="b6df3-140">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b6df3-141">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="b6df3-141">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

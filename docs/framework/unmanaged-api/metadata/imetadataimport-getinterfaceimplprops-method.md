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
ms.openlocfilehash: 4b8ddf7fec12d175f030c0ea0ed982c6fb334aee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175378"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="1c767-102">IMetaDataImport::GetInterfaceImplProps 方法</span><span class="sxs-lookup"><span data-stu-id="1c767-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="1c767-103">獲取實現指定方法的 的 中繼資料<xref:System.Type>權杖以及聲明該方法的介面的指標。</span><span class="sxs-lookup"><span data-stu-id="1c767-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="1c767-104">語法</span><span class="sxs-lookup"><span data-stu-id="1c767-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c767-105">參數</span><span class="sxs-lookup"><span data-stu-id="1c767-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="1c767-106">[在]表示要返回類和介面權杖的方法的中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="1c767-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="1c767-107">[出]表示實現方法的類的中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="1c767-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="1c767-108">[出]表示定義已實現方法的介面的中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="1c767-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  

## <a name="remarks"></a><span data-ttu-id="1c767-109">備註</span><span class="sxs-lookup"><span data-stu-id="1c767-109">Remarks</span></span>

 <span data-ttu-id="1c767-110">通過調用`iImpl`[EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md)方法，可以獲取 的值。</span><span class="sxs-lookup"><span data-stu-id="1c767-110">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span></span>

 <span data-ttu-id="1c767-111">例如，假設一個類的`mdTypeDef`權杖值為 0x02000007，並且它實現了三個介面，其類型具有權杖：</span><span class="sxs-lookup"><span data-stu-id="1c767-111">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span></span>

- <span data-ttu-id="1c767-112">0x0200003 （類型定義）</span><span class="sxs-lookup"><span data-stu-id="1c767-112">0x02000003 (TypeDef)</span></span>
- <span data-ttu-id="1c767-113">0x0100000A （類型參考）</span><span class="sxs-lookup"><span data-stu-id="1c767-113">0x0100000A (TypeRef)</span></span>
- <span data-ttu-id="1c767-114">0x0200001C （類型定義）</span><span class="sxs-lookup"><span data-stu-id="1c767-114">0x0200001C (TypeDef)</span></span>

<span data-ttu-id="1c767-115">從概念上講，此資訊存儲在介面實現表中，如：</span><span class="sxs-lookup"><span data-stu-id="1c767-115">Conceptually, this information is stored into an interface implementation table as:</span></span>

| <span data-ttu-id="1c767-116">行號</span><span class="sxs-lookup"><span data-stu-id="1c767-116">Row number</span></span> | <span data-ttu-id="1c767-117">類權杖</span><span class="sxs-lookup"><span data-stu-id="1c767-117">Class token</span></span> | <span data-ttu-id="1c767-118">介面權杖</span><span class="sxs-lookup"><span data-stu-id="1c767-118">Interface token</span></span> |
|------------|-------------|-----------------|
| <span data-ttu-id="1c767-119">4</span><span class="sxs-lookup"><span data-stu-id="1c767-119">4</span></span>          |             |                 |
| <span data-ttu-id="1c767-120">5</span><span class="sxs-lookup"><span data-stu-id="1c767-120">5</span></span>          | <span data-ttu-id="1c767-121">02000007</span><span class="sxs-lookup"><span data-stu-id="1c767-121">02000007</span></span>    | <span data-ttu-id="1c767-122">02000003</span><span class="sxs-lookup"><span data-stu-id="1c767-122">02000003</span></span>        |
| <span data-ttu-id="1c767-123">6</span><span class="sxs-lookup"><span data-stu-id="1c767-123">6</span></span>          | <span data-ttu-id="1c767-124">02000007</span><span class="sxs-lookup"><span data-stu-id="1c767-124">02000007</span></span>    | <span data-ttu-id="1c767-125">0100000A</span><span class="sxs-lookup"><span data-stu-id="1c767-125">0100000A</span></span>        |
| <span data-ttu-id="1c767-126">7</span><span class="sxs-lookup"><span data-stu-id="1c767-126">7</span></span>          |             |                 |
| <span data-ttu-id="1c767-127">8</span><span class="sxs-lookup"><span data-stu-id="1c767-127">8</span></span>          | <span data-ttu-id="1c767-128">02000007</span><span class="sxs-lookup"><span data-stu-id="1c767-128">02000007</span></span>    | <span data-ttu-id="1c767-129">0200001C</span><span class="sxs-lookup"><span data-stu-id="1c767-129">0200001C</span></span>        |

<span data-ttu-id="1c767-130">回想，權杖是 4 位元組的值：</span><span class="sxs-lookup"><span data-stu-id="1c767-130">Recall, the token is a 4-byte value:</span></span>

- <span data-ttu-id="1c767-131">較低的 3 個位元組保留行號或 RID。</span><span class="sxs-lookup"><span data-stu-id="1c767-131">The lower 3 bytes hold the row number, or RID.</span></span>
- <span data-ttu-id="1c767-132">上位元組保存的權杖類型 = 0x09。 `mdtInterfaceImpl`</span><span class="sxs-lookup"><span data-stu-id="1c767-132">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span></span>

<span data-ttu-id="1c767-133">`GetInterfaceImplProps`返回您在`iImpl`參數中提供的權杖行中持有的資訊。</span><span class="sxs-lookup"><span data-stu-id="1c767-133">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="1c767-134">需求</span><span class="sxs-lookup"><span data-stu-id="1c767-134">Requirements</span></span>  
 <span data-ttu-id="1c767-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1c767-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c767-136">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="1c767-136">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1c767-137">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="1c767-137">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1c767-138">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c767-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c767-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c767-139">See also</span></span>

- [<span data-ttu-id="1c767-140">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="1c767-140">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="1c767-141">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="1c767-141">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

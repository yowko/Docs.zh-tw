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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2a4305b94d785a764671a2d73f43facefd0da0e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782377"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="72834-102">IMetaDataImport::GetInterfaceImplProps 方法</span><span class="sxs-lookup"><span data-stu-id="72834-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="72834-103">取得中繼資料語彙基元的指標<xref:System.Type>實作指定的方法和介面宣告該方法。</span><span class="sxs-lookup"><span data-stu-id="72834-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="72834-104">語法</span><span class="sxs-lookup"><span data-stu-id="72834-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72834-105">參數</span><span class="sxs-lookup"><span data-stu-id="72834-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="72834-106">[in]中繼資料語彙基元，代表這個方法傳回的類別和介面 token。</span><span class="sxs-lookup"><span data-stu-id="72834-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="72834-107">[out]中繼資料語彙基元，表示實作方法的類別。</span><span class="sxs-lookup"><span data-stu-id="72834-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="72834-108">[out]中繼資料語彙基元，代表定義的實作的方法的介面。</span><span class="sxs-lookup"><span data-stu-id="72834-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  

## <a name="remarks"></a><span data-ttu-id="72834-109">備註</span><span class="sxs-lookup"><span data-stu-id="72834-109">Remarks</span></span>

 <span data-ttu-id="72834-110">取得值，如`iImpl`藉由呼叫[EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="72834-110">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span></span>
 
 <span data-ttu-id="72834-111">例如，假設 的類別有`mdTypeDef`k 0x02000007 的值，它會實作它的型別具有權杖的三個介面：</span><span class="sxs-lookup"><span data-stu-id="72834-111">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span></span> 

- <span data-ttu-id="72834-112">0x02000003 (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="72834-112">0x02000003 (TypeDef)</span></span>
- <span data-ttu-id="72834-113">0x0100000A (TypeRef)</span><span class="sxs-lookup"><span data-stu-id="72834-113">0x0100000A (TypeRef)</span></span>
- <span data-ttu-id="72834-114">0x0200001C (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="72834-114">0x0200001C (TypeDef)</span></span>

<span data-ttu-id="72834-115">就概念而言，這項資訊會儲存至介面實作資料表為：</span><span class="sxs-lookup"><span data-stu-id="72834-115">Conceptually, this information is stored into an interface implementation table as:</span></span>

| <span data-ttu-id="72834-116">資料列數目</span><span class="sxs-lookup"><span data-stu-id="72834-116">Row number</span></span> | <span data-ttu-id="72834-117">類別的語彙基元</span><span class="sxs-lookup"><span data-stu-id="72834-117">Class token</span></span> | <span data-ttu-id="72834-118">介面的語彙基元</span><span class="sxs-lookup"><span data-stu-id="72834-118">Interface token</span></span> |
|------------|-------------|-----------------|
| <span data-ttu-id="72834-119">4</span><span class="sxs-lookup"><span data-stu-id="72834-119">4</span></span>          |             |                 |
| <span data-ttu-id="72834-120">5</span><span class="sxs-lookup"><span data-stu-id="72834-120">5</span></span>          | <span data-ttu-id="72834-121">02000007</span><span class="sxs-lookup"><span data-stu-id="72834-121">02000007</span></span>    | <span data-ttu-id="72834-122">02000003</span><span class="sxs-lookup"><span data-stu-id="72834-122">02000003</span></span>        |
| <span data-ttu-id="72834-123">6</span><span class="sxs-lookup"><span data-stu-id="72834-123">6</span></span>          | <span data-ttu-id="72834-124">02000007</span><span class="sxs-lookup"><span data-stu-id="72834-124">02000007</span></span>    | <span data-ttu-id="72834-125">0100000A</span><span class="sxs-lookup"><span data-stu-id="72834-125">0100000A</span></span>        |
| <span data-ttu-id="72834-126">7</span><span class="sxs-lookup"><span data-stu-id="72834-126">7</span></span>          |             |                 |
| <span data-ttu-id="72834-127">8</span><span class="sxs-lookup"><span data-stu-id="72834-127">8</span></span>          | <span data-ttu-id="72834-128">02000007</span><span class="sxs-lookup"><span data-stu-id="72834-128">02000007</span></span>    | <span data-ttu-id="72834-129">0200001C</span><span class="sxs-lookup"><span data-stu-id="72834-129">0200001C</span></span>        |

<span data-ttu-id="72834-130">請記住，此語彙基元是 4 位元組值：</span><span class="sxs-lookup"><span data-stu-id="72834-130">Recall, the token is a 4-byte value:</span></span>

- <span data-ttu-id="72834-131">較低的 3 個位元組會保存資料列數目，或 RID。</span><span class="sxs-lookup"><span data-stu-id="72834-131">The lower 3 bytes hold the row number, or RID.</span></span>
- <span data-ttu-id="72834-132">上方的位元組會保存語彙基元的型別 – 為 0x09 `mdtInterfaceImpl`。</span><span class="sxs-lookup"><span data-stu-id="72834-132">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span></span>

<span data-ttu-id="72834-133">`GetInterfaceImplProps` 傳回的資訊保留在資料列中提供的語彙基元`iImpl`引數。</span><span class="sxs-lookup"><span data-stu-id="72834-133">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span></span> 
  
## <a name="requirements"></a><span data-ttu-id="72834-134">需求</span><span class="sxs-lookup"><span data-stu-id="72834-134">Requirements</span></span>  
 <span data-ttu-id="72834-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="72834-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72834-136">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="72834-136">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="72834-137">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="72834-137">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="72834-138">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72834-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72834-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72834-139">See also</span></span>

- [<span data-ttu-id="72834-140">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="72834-140">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="72834-141">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="72834-141">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

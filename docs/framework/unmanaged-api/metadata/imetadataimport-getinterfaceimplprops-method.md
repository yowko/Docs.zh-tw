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
ms.openlocfilehash: 76e2ebbd47a5e36a722fce33ba67d7efb4db8675
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115930"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="29580-102">IMetaDataImport::GetInterfaceImplProps 方法</span><span class="sxs-lookup"><span data-stu-id="29580-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="29580-103">取得中繼資料語彙基元的指標<xref:System.Type>實作指定的方法和介面宣告該方法。</span><span class="sxs-lookup"><span data-stu-id="29580-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="29580-104">語法</span><span class="sxs-lookup"><span data-stu-id="29580-104">Syntax</span></span>  
  
```  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29580-105">參數</span><span class="sxs-lookup"><span data-stu-id="29580-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="29580-106">[in]中繼資料語彙基元，代表這個方法傳回的類別和介面 token。</span><span class="sxs-lookup"><span data-stu-id="29580-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="29580-107">[out]中繼資料語彙基元，表示實作方法的類別。</span><span class="sxs-lookup"><span data-stu-id="29580-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="29580-108">[out]中繼資料語彙基元，代表定義的實作的方法的介面。</span><span class="sxs-lookup"><span data-stu-id="29580-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  

## <a name="remarks"></a><span data-ttu-id="29580-109">備註</span><span class="sxs-lookup"><span data-stu-id="29580-109">Remarks</span></span>

 <span data-ttu-id="29580-110">取得值，如`iImpl`藉由呼叫[EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="29580-110">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span></span>
 
 <span data-ttu-id="29580-111">例如，假設 的類別有`mdTypeDef`k 0x02000007 的值，它會實作它的型別具有權杖的三個介面：</span><span class="sxs-lookup"><span data-stu-id="29580-111">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span></span> 

- <span data-ttu-id="29580-112">0x02000003 (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="29580-112">0x02000003 (TypeDef)</span></span>
- <span data-ttu-id="29580-113">0x0100000A (TypeRef)</span><span class="sxs-lookup"><span data-stu-id="29580-113">0x0100000A (TypeRef)</span></span>
- <span data-ttu-id="29580-114">0x0200001C (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="29580-114">0x0200001C (TypeDef)</span></span>

<span data-ttu-id="29580-115">就概念而言，這項資訊會儲存至介面實作資料表為：</span><span class="sxs-lookup"><span data-stu-id="29580-115">Conceptually, this information is stored into an interface implementation table as:</span></span>

| <span data-ttu-id="29580-116">資料列數目</span><span class="sxs-lookup"><span data-stu-id="29580-116">Row number</span></span> | <span data-ttu-id="29580-117">類別的語彙基元</span><span class="sxs-lookup"><span data-stu-id="29580-117">Class token</span></span> | <span data-ttu-id="29580-118">介面的語彙基元</span><span class="sxs-lookup"><span data-stu-id="29580-118">Interface token</span></span> |
|------------|-------------|-----------------|
| <span data-ttu-id="29580-119">4</span><span class="sxs-lookup"><span data-stu-id="29580-119">4</span></span>          |             |                 |
| <span data-ttu-id="29580-120">5</span><span class="sxs-lookup"><span data-stu-id="29580-120">5</span></span>          | <span data-ttu-id="29580-121">02000007</span><span class="sxs-lookup"><span data-stu-id="29580-121">02000007</span></span>    | <span data-ttu-id="29580-122">02000003</span><span class="sxs-lookup"><span data-stu-id="29580-122">02000003</span></span>        |
| <span data-ttu-id="29580-123">6</span><span class="sxs-lookup"><span data-stu-id="29580-123">6</span></span>          | <span data-ttu-id="29580-124">02000007</span><span class="sxs-lookup"><span data-stu-id="29580-124">02000007</span></span>    | <span data-ttu-id="29580-125">0100000A</span><span class="sxs-lookup"><span data-stu-id="29580-125">0100000A</span></span>        |
| <span data-ttu-id="29580-126">7</span><span class="sxs-lookup"><span data-stu-id="29580-126">7</span></span>          |             |                 |
| <span data-ttu-id="29580-127">8</span><span class="sxs-lookup"><span data-stu-id="29580-127">8</span></span>          | <span data-ttu-id="29580-128">02000007</span><span class="sxs-lookup"><span data-stu-id="29580-128">02000007</span></span>    | <span data-ttu-id="29580-129">0200001C</span><span class="sxs-lookup"><span data-stu-id="29580-129">0200001C</span></span>        |

<span data-ttu-id="29580-130">請記住，此語彙基元是 4 位元組值：</span><span class="sxs-lookup"><span data-stu-id="29580-130">Recall, the token is a 4-byte value:</span></span>

- <span data-ttu-id="29580-131">較低的 3 個位元組會保存資料列數目，或 RID。</span><span class="sxs-lookup"><span data-stu-id="29580-131">The lower 3 bytes hold the row number, or RID.</span></span>
- <span data-ttu-id="29580-132">上方的位元組會保存語彙基元的型別 – 為 0x09 `mdtInterfaceImpl`。</span><span class="sxs-lookup"><span data-stu-id="29580-132">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span></span>

`GetInterfaceImplProps` <span data-ttu-id="29580-133">傳回的資訊保留在資料列中提供的語彙基元`iImpl`引數。</span><span class="sxs-lookup"><span data-stu-id="29580-133">returns the information held in the row whose token you provide in the `iImpl` argument.</span></span> 
  
## <a name="requirements"></a><span data-ttu-id="29580-134">需求</span><span class="sxs-lookup"><span data-stu-id="29580-134">Requirements</span></span>  
 <span data-ttu-id="29580-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="29580-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29580-136">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="29580-136">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="29580-137">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="29580-137">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="29580-138">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="29580-138">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="29580-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29580-139">See also</span></span>

- [<span data-ttu-id="29580-140">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="29580-140">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="29580-141">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="29580-141">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

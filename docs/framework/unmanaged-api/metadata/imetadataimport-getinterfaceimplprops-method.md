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
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="d75fa-102">IMetaDataImport::GetInterfaceImplProps 方法</span><span class="sxs-lookup"><span data-stu-id="d75fa-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="d75fa-103">取得執行指定方法之 <xref:System.Type> 的元資料標記指標，以及宣告該方法之介面的指標。</span><span class="sxs-lookup"><span data-stu-id="d75fa-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="d75fa-104">語法</span><span class="sxs-lookup"><span data-stu-id="d75fa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d75fa-105">參數</span><span class="sxs-lookup"><span data-stu-id="d75fa-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="d75fa-106">在元資料標記，代表要傳回其類別和介面標記的方法。</span><span class="sxs-lookup"><span data-stu-id="d75fa-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="d75fa-107">脫銷元資料標記，代表可執行方法的類別。</span><span class="sxs-lookup"><span data-stu-id="d75fa-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="d75fa-108">脫銷元資料標記，代表定義已執行之方法的介面。</span><span class="sxs-lookup"><span data-stu-id="d75fa-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  

## <a name="remarks"></a><span data-ttu-id="d75fa-109">備註</span><span class="sxs-lookup"><span data-stu-id="d75fa-109">Remarks</span></span>

 <span data-ttu-id="d75fa-110">您可以藉由呼叫[EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md)方法來取得 `iImpl` 的值。</span><span class="sxs-lookup"><span data-stu-id="d75fa-110">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span></span>
 
 <span data-ttu-id="d75fa-111">例如，假設類別具有0x02000007 的 `mdTypeDef` token 值，而且它會實作為類型具有權杖的三個介面：</span><span class="sxs-lookup"><span data-stu-id="d75fa-111">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span></span> 

- <span data-ttu-id="d75fa-112">0x02000003 （TypeDef）</span><span class="sxs-lookup"><span data-stu-id="d75fa-112">0x02000003 (TypeDef)</span></span>
- <span data-ttu-id="d75fa-113">0x0100000A （TypeRef）</span><span class="sxs-lookup"><span data-stu-id="d75fa-113">0x0100000A (TypeRef)</span></span>
- <span data-ttu-id="d75fa-114">0x0200001C （TypeDef）</span><span class="sxs-lookup"><span data-stu-id="d75fa-114">0x0200001C (TypeDef)</span></span>

<span data-ttu-id="d75fa-115">就概念而言，這種資訊會儲存在介面執行資料表中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d75fa-115">Conceptually, this information is stored into an interface implementation table as:</span></span>

| <span data-ttu-id="d75fa-116">資料列編號</span><span class="sxs-lookup"><span data-stu-id="d75fa-116">Row number</span></span> | <span data-ttu-id="d75fa-117">類別 token</span><span class="sxs-lookup"><span data-stu-id="d75fa-117">Class token</span></span> | <span data-ttu-id="d75fa-118">介面 token</span><span class="sxs-lookup"><span data-stu-id="d75fa-118">Interface token</span></span> |
|------------|-------------|-----------------|
| <span data-ttu-id="d75fa-119">4</span><span class="sxs-lookup"><span data-stu-id="d75fa-119">4</span></span>          |             |                 |
| <span data-ttu-id="d75fa-120">5</span><span class="sxs-lookup"><span data-stu-id="d75fa-120">5</span></span>          | <span data-ttu-id="d75fa-121">02000007</span><span class="sxs-lookup"><span data-stu-id="d75fa-121">02000007</span></span>    | <span data-ttu-id="d75fa-122">02000003</span><span class="sxs-lookup"><span data-stu-id="d75fa-122">02000003</span></span>        |
| <span data-ttu-id="d75fa-123">6</span><span class="sxs-lookup"><span data-stu-id="d75fa-123">6</span></span>          | <span data-ttu-id="d75fa-124">02000007</span><span class="sxs-lookup"><span data-stu-id="d75fa-124">02000007</span></span>    | <span data-ttu-id="d75fa-125">0100000A</span><span class="sxs-lookup"><span data-stu-id="d75fa-125">0100000A</span></span>        |
| <span data-ttu-id="d75fa-126">7</span><span class="sxs-lookup"><span data-stu-id="d75fa-126">7</span></span>          |             |                 |
| <span data-ttu-id="d75fa-127">8</span><span class="sxs-lookup"><span data-stu-id="d75fa-127">8</span></span>          | <span data-ttu-id="d75fa-128">02000007</span><span class="sxs-lookup"><span data-stu-id="d75fa-128">02000007</span></span>    | <span data-ttu-id="d75fa-129">0200001C</span><span class="sxs-lookup"><span data-stu-id="d75fa-129">0200001C</span></span>        |

<span data-ttu-id="d75fa-130">回想一下，權杖是4個位元組的值：</span><span class="sxs-lookup"><span data-stu-id="d75fa-130">Recall, the token is a 4-byte value:</span></span>

- <span data-ttu-id="d75fa-131">較低的3個位元組會保存資料列編號或 RID。</span><span class="sxs-lookup"><span data-stu-id="d75fa-131">The lower 3 bytes hold the row number, or RID.</span></span>
- <span data-ttu-id="d75fa-132">大小上限會保存 `mdtInterfaceImpl`的 token 類型-0x09。</span><span class="sxs-lookup"><span data-stu-id="d75fa-132">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span></span>

<span data-ttu-id="d75fa-133">`GetInterfaceImplProps` 會傳回您在 `iImpl` 引數中提供之權杖的資料列中所保存的資訊。</span><span class="sxs-lookup"><span data-stu-id="d75fa-133">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span></span> 
  
## <a name="requirements"></a><span data-ttu-id="d75fa-134">需求</span><span class="sxs-lookup"><span data-stu-id="d75fa-134">Requirements</span></span>  
 <span data-ttu-id="d75fa-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d75fa-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d75fa-136">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="d75fa-136">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d75fa-137">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d75fa-137">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d75fa-138">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d75fa-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d75fa-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d75fa-139">See also</span></span>

- [<span data-ttu-id="d75fa-140">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="d75fa-140">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d75fa-141">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="d75fa-141">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

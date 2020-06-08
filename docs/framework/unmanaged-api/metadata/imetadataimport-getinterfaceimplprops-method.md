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
ms.openlocfilehash: 1c9d9647084aa729817eeeb17ee3f5cd320c0d29
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491221"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="6cfd2-102">IMetaDataImport::GetInterfaceImplProps 方法</span><span class="sxs-lookup"><span data-stu-id="6cfd2-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="6cfd2-103">取得的元資料標記指標，其可執行 <xref:System.Type> 指定的方法，以及宣告該方法之介面的。</span><span class="sxs-lookup"><span data-stu-id="6cfd2-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="6cfd2-104">語法</span><span class="sxs-lookup"><span data-stu-id="6cfd2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6cfd2-105">參數</span><span class="sxs-lookup"><span data-stu-id="6cfd2-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="6cfd2-106">在元資料標記，代表要傳回其類別和介面標記的方法。</span><span class="sxs-lookup"><span data-stu-id="6cfd2-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="6cfd2-107">脫銷元資料標記，代表可執行方法的類別。</span><span class="sxs-lookup"><span data-stu-id="6cfd2-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="6cfd2-108">脫銷元資料標記，代表定義已執行之方法的介面。</span><span class="sxs-lookup"><span data-stu-id="6cfd2-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  

## <a name="remarks"></a><span data-ttu-id="6cfd2-109">備註</span><span class="sxs-lookup"><span data-stu-id="6cfd2-109">Remarks</span></span>

 <span data-ttu-id="6cfd2-110">您可以藉 `iImpl` 由呼叫[EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md)方法來取得的值。</span><span class="sxs-lookup"><span data-stu-id="6cfd2-110">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span></span>

 <span data-ttu-id="6cfd2-111">例如，假設類別的 `mdTypeDef` token 值為0x02000007，而且它會實作為類型具有權杖的三個介面：</span><span class="sxs-lookup"><span data-stu-id="6cfd2-111">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span></span>

- <span data-ttu-id="6cfd2-112">0x02000003 （TypeDef）</span><span class="sxs-lookup"><span data-stu-id="6cfd2-112">0x02000003 (TypeDef)</span></span>
- <span data-ttu-id="6cfd2-113">0x0100000A （TypeRef）</span><span class="sxs-lookup"><span data-stu-id="6cfd2-113">0x0100000A (TypeRef)</span></span>
- <span data-ttu-id="6cfd2-114">0x0200001C （TypeDef）</span><span class="sxs-lookup"><span data-stu-id="6cfd2-114">0x0200001C (TypeDef)</span></span>

<span data-ttu-id="6cfd2-115">就概念而言，這種資訊會儲存在介面執行資料表中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6cfd2-115">Conceptually, this information is stored into an interface implementation table as:</span></span>

| <span data-ttu-id="6cfd2-116">資料列編號</span><span class="sxs-lookup"><span data-stu-id="6cfd2-116">Row number</span></span> | <span data-ttu-id="6cfd2-117">類別 token</span><span class="sxs-lookup"><span data-stu-id="6cfd2-117">Class token</span></span> | <span data-ttu-id="6cfd2-118">介面 token</span><span class="sxs-lookup"><span data-stu-id="6cfd2-118">Interface token</span></span> |
|------------|-------------|-----------------|
| <span data-ttu-id="6cfd2-119">4</span><span class="sxs-lookup"><span data-stu-id="6cfd2-119">4</span></span>          |             |                 |
| <span data-ttu-id="6cfd2-120">5</span><span class="sxs-lookup"><span data-stu-id="6cfd2-120">5</span></span>          | <span data-ttu-id="6cfd2-121">02000007</span><span class="sxs-lookup"><span data-stu-id="6cfd2-121">02000007</span></span>    | <span data-ttu-id="6cfd2-122">02000003</span><span class="sxs-lookup"><span data-stu-id="6cfd2-122">02000003</span></span>        |
| <span data-ttu-id="6cfd2-123">6</span><span class="sxs-lookup"><span data-stu-id="6cfd2-123">6</span></span>          | <span data-ttu-id="6cfd2-124">02000007</span><span class="sxs-lookup"><span data-stu-id="6cfd2-124">02000007</span></span>    | <span data-ttu-id="6cfd2-125">0100000A</span><span class="sxs-lookup"><span data-stu-id="6cfd2-125">0100000A</span></span>        |
| <span data-ttu-id="6cfd2-126">7</span><span class="sxs-lookup"><span data-stu-id="6cfd2-126">7</span></span>          |             |                 |
| <span data-ttu-id="6cfd2-127">8</span><span class="sxs-lookup"><span data-stu-id="6cfd2-127">8</span></span>          | <span data-ttu-id="6cfd2-128">02000007</span><span class="sxs-lookup"><span data-stu-id="6cfd2-128">02000007</span></span>    | <span data-ttu-id="6cfd2-129">0200001C</span><span class="sxs-lookup"><span data-stu-id="6cfd2-129">0200001C</span></span>        |

<span data-ttu-id="6cfd2-130">回想一下，權杖是4個位元組的值：</span><span class="sxs-lookup"><span data-stu-id="6cfd2-130">Recall, the token is a 4-byte value:</span></span>

- <span data-ttu-id="6cfd2-131">較低的3個位元組會保存資料列編號或 RID。</span><span class="sxs-lookup"><span data-stu-id="6cfd2-131">The lower 3 bytes hold the row number, or RID.</span></span>
- <span data-ttu-id="6cfd2-132">上層位元組會保存的 token 類型-0x09 `mdtInterfaceImpl` 。</span><span class="sxs-lookup"><span data-stu-id="6cfd2-132">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span></span>

<span data-ttu-id="6cfd2-133">`GetInterfaceImplProps`傳回資料列中保留的資訊，您在引數中提供其 token `iImpl` 。</span><span class="sxs-lookup"><span data-stu-id="6cfd2-133">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="6cfd2-134">規格需求</span><span class="sxs-lookup"><span data-stu-id="6cfd2-134">Requirements</span></span>  
 <span data-ttu-id="6cfd2-135">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6cfd2-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cfd2-136">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="6cfd2-136">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6cfd2-137">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6cfd2-137">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6cfd2-138">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cfd2-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cfd2-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cfd2-139">See also</span></span>

- [<span data-ttu-id="6cfd2-140">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="6cfd2-140">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="6cfd2-141">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="6cfd2-141">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)

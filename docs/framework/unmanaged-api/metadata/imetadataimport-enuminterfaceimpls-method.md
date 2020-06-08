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
ms.openlocfilehash: 910c40413075131765a37e00703ac892e3f39641
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492183"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="e1f45-102">IMetaDataImport::EnumInterfaceImpls 方法</span><span class="sxs-lookup"><span data-stu-id="e1f45-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="e1f45-103">列舉由指定的所實作為的所有介面 `TypeDef` 。</span><span class="sxs-lookup"><span data-stu-id="e1f45-103">Enumerates all interfaces implemented by the specified `TypeDef`.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="e1f45-104">語法</span><span class="sxs-lookup"><span data-stu-id="e1f45-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1f45-105">參數</span><span class="sxs-lookup"><span data-stu-id="e1f45-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e1f45-106">[in、out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="e1f45-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="e1f45-107">在要列舉其 MethodDef token 代表介面執行的 TypeDef 標記。</span><span class="sxs-lookup"><span data-stu-id="e1f45-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="e1f45-108">脫銷用來儲存 MethodDef 標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="e1f45-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e1f45-109">在陣列的最大長度 `rImpls` 。</span><span class="sxs-lookup"><span data-stu-id="e1f45-109">[in] The maximum length of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="e1f45-110">脫銷在中傳回的實際權杖數目 `rImpls` 。</span><span class="sxs-lookup"><span data-stu-id="e1f45-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1f45-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="e1f45-111">Return Value</span></span>  
  
|<span data-ttu-id="e1f45-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e1f45-112">HRESULT</span></span>|<span data-ttu-id="e1f45-113">說明</span><span class="sxs-lookup"><span data-stu-id="e1f45-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e1f45-114">`EnumInterfaceImpls`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="e1f45-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e1f45-115">沒有要列舉的 MethodDef 標記。</span><span class="sxs-lookup"><span data-stu-id="e1f45-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="e1f45-116">在此情況下， `pcImpls` 會設定為零。</span><span class="sxs-lookup"><span data-stu-id="e1f45-116">In that case, `pcImpls` is set to zero.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="e1f45-117">備註</span><span class="sxs-lookup"><span data-stu-id="e1f45-117">Remarks</span></span>

<span data-ttu-id="e1f45-118">列舉會 `mdInterfaceImpl` 針對所指定的每個介面傳回標記的集合 `TypeDef` 。</span><span class="sxs-lookup"><span data-stu-id="e1f45-118">The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`.</span></span> <span data-ttu-id="e1f45-119">介面權杖會依照指定介面的順序（透過 `DefineTypeDef` 或 `SetTypeDefProps` ）傳回。</span><span class="sxs-lookup"><span data-stu-id="e1f45-119">Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`).</span></span> <span data-ttu-id="e1f45-120">您 `mdInterfaceImpl` 可以使用[GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md)來查詢傳回之權杖的屬性。</span><span class="sxs-lookup"><span data-stu-id="e1f45-120">Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="e1f45-121">規格需求</span><span class="sxs-lookup"><span data-stu-id="e1f45-121">Requirements</span></span>  
 <span data-ttu-id="e1f45-122">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e1f45-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1f45-123">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="e1f45-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e1f45-124">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e1f45-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e1f45-125">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1f45-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1f45-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1f45-126">See also</span></span>

- [<span data-ttu-id="e1f45-127">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="e1f45-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="e1f45-128">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="e1f45-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)

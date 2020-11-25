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
ms.openlocfilehash: 0b040a2741a44b9d361dabc38c26b8934659003b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711516"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="07adf-102">IMetaDataImport::EnumInterfaceImpls 方法</span><span class="sxs-lookup"><span data-stu-id="07adf-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>

<span data-ttu-id="07adf-103">列舉由指定的所執行的所有介面 `TypeDef` 。</span><span class="sxs-lookup"><span data-stu-id="07adf-103">Enumerates all interfaces implemented by the specified `TypeDef`.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="07adf-104">語法</span><span class="sxs-lookup"><span data-stu-id="07adf-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07adf-105">參數</span><span class="sxs-lookup"><span data-stu-id="07adf-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="07adf-106">[in，out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="07adf-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="07adf-107">在要列舉其 MethodDef token 表示介面實作為的 TypeDef 標記。</span><span class="sxs-lookup"><span data-stu-id="07adf-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="07adf-108">擴展用來儲存 MethodDef 標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="07adf-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="07adf-109">在陣列的最大長度 `rImpls` 。</span><span class="sxs-lookup"><span data-stu-id="07adf-109">[in] The maximum length of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="07adf-110">擴展在中傳回的實際標記數目 `rImpls` 。</span><span class="sxs-lookup"><span data-stu-id="07adf-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07adf-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="07adf-111">Return Value</span></span>  
  
|<span data-ttu-id="07adf-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="07adf-112">HRESULT</span></span>|<span data-ttu-id="07adf-113">描述</span><span class="sxs-lookup"><span data-stu-id="07adf-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="07adf-114">`EnumInterfaceImpls` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="07adf-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="07adf-115">沒有要列舉的 MethodDef 標記。</span><span class="sxs-lookup"><span data-stu-id="07adf-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="07adf-116">在此情況下， `pcImpls` 會設定為零。</span><span class="sxs-lookup"><span data-stu-id="07adf-116">In that case, `pcImpls` is set to zero.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="07adf-117">備註</span><span class="sxs-lookup"><span data-stu-id="07adf-117">Remarks</span></span>

<span data-ttu-id="07adf-118">列舉會傳回 `mdInterfaceImpl` 所指定的每個介面的標記集合 `TypeDef` 。</span><span class="sxs-lookup"><span data-stu-id="07adf-118">The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`.</span></span> <span data-ttu-id="07adf-119">介面標記會依照 (透過或) 指定介面的順序傳回 `DefineTypeDef` `SetTypeDefProps` 。</span><span class="sxs-lookup"><span data-stu-id="07adf-119">Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`).</span></span> <span data-ttu-id="07adf-120">您 `mdInterfaceImpl` 可以使用 [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md)來查詢所傳回權杖的屬性。</span><span class="sxs-lookup"><span data-stu-id="07adf-120">Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="07adf-121">需求</span><span class="sxs-lookup"><span data-stu-id="07adf-121">Requirements</span></span>  

 <span data-ttu-id="07adf-122">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="07adf-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07adf-123">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="07adf-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="07adf-124">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="07adf-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="07adf-125">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07adf-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07adf-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07adf-126">See also</span></span>

- [<span data-ttu-id="07adf-127">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="07adf-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="07adf-128">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="07adf-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)

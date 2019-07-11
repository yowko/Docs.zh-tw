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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d0f94949cdc82cdecd52f003f3400c43014fabf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780467"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="df3db-102">IMetaDataImport::EnumInterfaceImpls 方法</span><span class="sxs-lookup"><span data-stu-id="df3db-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="df3db-103">列舉所指定實作的所有介面`TypeDef`。</span><span class="sxs-lookup"><span data-stu-id="df3db-103">Enumerates all interfaces implemented by the specified `TypeDef`.</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="df3db-104">語法</span><span class="sxs-lookup"><span data-stu-id="df3db-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,   
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],   
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df3db-105">參數</span><span class="sxs-lookup"><span data-stu-id="df3db-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="df3db-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="df3db-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="df3db-107">[in]代表介面實作的 methoddef 語彙基元是要列舉的 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="df3db-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="df3db-108">[out]陣列，用來儲存 methoddef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="df3db-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="df3db-109">[in] `rImpls` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="df3db-109">[in] The maximum size of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="df3db-110">[out]權杖中傳回的實際數目`rImpls`。</span><span class="sxs-lookup"><span data-stu-id="df3db-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="df3db-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="df3db-111">Return Value</span></span>  
  
|<span data-ttu-id="df3db-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="df3db-112">HRESULT</span></span>|<span data-ttu-id="df3db-113">描述</span><span class="sxs-lookup"><span data-stu-id="df3db-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="df3db-114">`EnumInterfaceImpls` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="df3db-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="df3db-115">沒有列舉 MethodDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="df3db-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="df3db-116">在此情況下，`pcImpls`設為零。</span><span class="sxs-lookup"><span data-stu-id="df3db-116">In that case, `pcImpls` is set to zero.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="df3db-117">備註</span><span class="sxs-lookup"><span data-stu-id="df3db-117">Remarks</span></span>

<span data-ttu-id="df3db-118">此列舉會傳回的集合`mdInterfaceImpl`每個介面實作所指定的語彙基元`TypeDef`。</span><span class="sxs-lookup"><span data-stu-id="df3db-118">The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`.</span></span> <span data-ttu-id="df3db-119">介面權杖會傳回指定之介面的順序 (透過`DefineTypeDef`或`SetTypeDefProps`)。</span><span class="sxs-lookup"><span data-stu-id="df3db-119">Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`).</span></span> <span data-ttu-id="df3db-120">屬性傳回之`mdInterfaceImpl`您可以使用查詢語彙基元[GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md)。</span><span class="sxs-lookup"><span data-stu-id="df3db-120">Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="df3db-121">需求</span><span class="sxs-lookup"><span data-stu-id="df3db-121">Requirements</span></span>  
 <span data-ttu-id="df3db-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="df3db-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df3db-123">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="df3db-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="df3db-124">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="df3db-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="df3db-125">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df3db-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df3db-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df3db-126">See also</span></span>

- [<span data-ttu-id="df3db-127">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="df3db-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="df3db-128">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="df3db-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

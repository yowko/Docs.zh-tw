---
title: IMetaDataEmit::DefineTypeDef 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeDef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type:
- apiref
ms.openlocfilehash: 031996813718a074eebab62ff54a2de52b898c22
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450223"
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="6f08e-102">IMetaDataEmit::DefineTypeDef 方法</span><span class="sxs-lookup"><span data-stu-id="6f08e-102">IMetaDataEmit::DefineTypeDef Method</span></span>
<span data-ttu-id="6f08e-103">建立 common language runtime 類型的類型定義，並取得該類型定義的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="6f08e-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f08e-104">語法</span><span class="sxs-lookup"><span data-stu-id="6f08e-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeDef (   
    [in]  LPCWSTR     szTypeDef,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f08e-105">參數</span><span class="sxs-lookup"><span data-stu-id="6f08e-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="6f08e-106">在Unicode 中的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="6f08e-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="6f08e-107">[in] `TypeDef` 屬性。</span><span class="sxs-lookup"><span data-stu-id="6f08e-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="6f08e-108">這是 `CoreTypeAttr` 值的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="6f08e-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="6f08e-109">在基類的 token。</span><span class="sxs-lookup"><span data-stu-id="6f08e-109">[in] The token of the base class.</span></span> <span data-ttu-id="6f08e-110">它必須是 `mdTypeDef` 或 `mdTypeRef` token。</span><span class="sxs-lookup"><span data-stu-id="6f08e-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="6f08e-111">在Token 的陣列，指定此類別或介面所要執行的介面。</span><span class="sxs-lookup"><span data-stu-id="6f08e-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="6f08e-112">脫銷指派的 `mdTypeDef` token。</span><span class="sxs-lookup"><span data-stu-id="6f08e-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f08e-113">備註</span><span class="sxs-lookup"><span data-stu-id="6f08e-113">Remarks</span></span>  
 <span data-ttu-id="6f08e-114">`dwTypeDefFlags` 中的旗標會指定所建立的型別是通用型別系統參考型別（類別或介面）還是一般型別系統實值型別。</span><span class="sxs-lookup"><span data-stu-id="6f08e-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="6f08e-115">視提供的參數而定，這個方法也可能會為這個類型所繼承或執行的每個介面建立 `mdInterfaceImpl` 記錄。</span><span class="sxs-lookup"><span data-stu-id="6f08e-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="6f08e-116">不過，這個方法不會傳回這些 `mdInterfaceImpl` token 中的任何一個。</span><span class="sxs-lookup"><span data-stu-id="6f08e-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="6f08e-117">如果用戶端想要在稍後新增或修改 `mdInterfaceImpl` token，它必須使用 `IMetaDataImport` 介面來列舉它們。</span><span class="sxs-lookup"><span data-stu-id="6f08e-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="6f08e-118">如果您想要使用 `[default]` 介面的 COM 語義，您應該提供預設介面做為 `rtkImplements`中的第一個元素。在類別上設定的自訂屬性會指出類別具有預設介面（一律假設為類別的第一個 `mdInterfaceImpl` token）。</span><span class="sxs-lookup"><span data-stu-id="6f08e-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="6f08e-119">`rtkImplements` 陣列的每個元素都會保留 `mdTypeDef` 或 `mdTypeRef` token。</span><span class="sxs-lookup"><span data-stu-id="6f08e-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="6f08e-120">陣列中的最後一個元素必須 `mdTokenNil`。</span><span class="sxs-lookup"><span data-stu-id="6f08e-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f08e-121">需求</span><span class="sxs-lookup"><span data-stu-id="6f08e-121">Requirements</span></span>  
 <span data-ttu-id="6f08e-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6f08e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f08e-123">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="6f08e-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6f08e-124">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="6f08e-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f08e-125">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f08e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f08e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f08e-126">See also</span></span>

- [<span data-ttu-id="6f08e-127">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="6f08e-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="6f08e-128">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="6f08e-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

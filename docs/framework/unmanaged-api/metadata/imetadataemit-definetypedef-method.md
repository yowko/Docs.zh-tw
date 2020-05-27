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
ms.openlocfilehash: dc064b00e32bb6b1d8c2d0c20f571b35919eae23
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009336"
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="efe71-102">IMetaDataEmit::DefineTypeDef 方法</span><span class="sxs-lookup"><span data-stu-id="efe71-102">IMetaDataEmit::DefineTypeDef Method</span></span>
<span data-ttu-id="efe71-103">建立 common language runtime 類型的類型定義，並取得該類型定義的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="efe71-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efe71-104">語法</span><span class="sxs-lookup"><span data-stu-id="efe71-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeDef (
    [in]  LPCWSTR     szTypeDef,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efe71-105">參數</span><span class="sxs-lookup"><span data-stu-id="efe71-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="efe71-106">在Unicode 中的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="efe71-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="efe71-107">[in] `TypeDef`特性.</span><span class="sxs-lookup"><span data-stu-id="efe71-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="efe71-108">這是值的位元遮罩 `CoreTypeAttr` 。</span><span class="sxs-lookup"><span data-stu-id="efe71-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="efe71-109">在基類的 token。</span><span class="sxs-lookup"><span data-stu-id="efe71-109">[in] The token of the base class.</span></span> <span data-ttu-id="efe71-110">它必須是 `mdTypeDef` 或 `mdTypeRef` 權杖。</span><span class="sxs-lookup"><span data-stu-id="efe71-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="efe71-111">在Token 的陣列，指定此類別或介面所要執行的介面。</span><span class="sxs-lookup"><span data-stu-id="efe71-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="efe71-112">脫銷`mdTypeDef`指派的 token。</span><span class="sxs-lookup"><span data-stu-id="efe71-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efe71-113">備註</span><span class="sxs-lookup"><span data-stu-id="efe71-113">Remarks</span></span>  
 <span data-ttu-id="efe71-114">中的旗標 `dwTypeDefFlags` 會指定所建立的型別是通用型別系統參考型別（類別或介面）還是一般型別系統實值型別。</span><span class="sxs-lookup"><span data-stu-id="efe71-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="efe71-115">視提供的參數而定，這個方法也可能會 `mdInterfaceImpl` 為這個類型所繼承或執行的每個介面建立一筆記錄。</span><span class="sxs-lookup"><span data-stu-id="efe71-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="efe71-116">不過，這個方法不會傳回任何這些 `mdInterfaceImpl` 標記。</span><span class="sxs-lookup"><span data-stu-id="efe71-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="efe71-117">如果用戶端想要在稍後新增或修改 `mdInterfaceImpl` 權杖，它必須使用 `IMetaDataImport` 介面來加以列舉。</span><span class="sxs-lookup"><span data-stu-id="efe71-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="efe71-118">如果您想要使用介面的 COM 語義 `[default]` ，您應該提供預設介面做為中的第一個元素 `rtkImplements` ; 在類別上設定的自訂屬性會指出該類別具有預設介面（一律假設為類別的第一個 `mdInterfaceImpl` token）。</span><span class="sxs-lookup"><span data-stu-id="efe71-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="efe71-119">陣列的每個元素都 `rtkImplements` 包含 `mdTypeDef` 或 `mdTypeRef` token。</span><span class="sxs-lookup"><span data-stu-id="efe71-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="efe71-120">陣列中的最後一個元素必須是 `mdTokenNil` 。</span><span class="sxs-lookup"><span data-stu-id="efe71-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efe71-121">需求</span><span class="sxs-lookup"><span data-stu-id="efe71-121">Requirements</span></span>  
 <span data-ttu-id="efe71-122">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="efe71-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efe71-123">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="efe71-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="efe71-124">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="efe71-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="efe71-125">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efe71-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efe71-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="efe71-126">See also</span></span>

- [<span data-ttu-id="efe71-127">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="efe71-127">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="efe71-128">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="efe71-128">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

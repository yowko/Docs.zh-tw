---
title: IMetaDataEmit::SetFieldProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldProps
helpviewer_keywords:
- IMetaDataEmit::SetFieldProps method [.NET Framework metadata]
- SetFieldProps method [.NET Framework metadata]
ms.assetid: 47132dda-fa92-4bd1-ae4b-24cd9a60665a
topic_type:
- apiref
ms.openlocfilehash: efc627619d9abf9cfa6010e1c0ca709989b9cad3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445459"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="dd951-102">IMetaDataEmit::SetFieldProps 方法</span><span class="sxs-lookup"><span data-stu-id="dd951-102">IMetaDataEmit::SetFieldProps Method</span></span>
<span data-ttu-id="dd951-103">設定或更新指定欄位標記所參考之欄位的預設值。</span><span class="sxs-lookup"><span data-stu-id="dd951-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd951-104">語法</span><span class="sxs-lookup"><span data-stu-id="dd951-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,   
    [in]  DWORD       dwFieldFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd951-105">參數</span><span class="sxs-lookup"><span data-stu-id="dd951-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="dd951-106">在目標欄位的 token。</span><span class="sxs-lookup"><span data-stu-id="dd951-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="dd951-107">在欄位屬性。</span><span class="sxs-lookup"><span data-stu-id="dd951-107">[in] Field attributes.</span></span> <span data-ttu-id="dd951-108">這是 `CorFieldAttr` 值的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="dd951-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="dd951-109">在常數值的 `ELEMENT_TYPE_` *\** 。</span><span class="sxs-lookup"><span data-stu-id="dd951-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="dd951-110">這是 `CorElementType` 值。</span><span class="sxs-lookup"><span data-stu-id="dd951-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="dd951-111">如果沒有定義常數，請將此值設定為 `ELEMENT_TYPE_END`。</span><span class="sxs-lookup"><span data-stu-id="dd951-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="dd951-112">在欄位的常數值。</span><span class="sxs-lookup"><span data-stu-id="dd951-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="dd951-113">在`pValue`的大小，以 Unicode 字元為單位。</span><span class="sxs-lookup"><span data-stu-id="dd951-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd951-114">需求</span><span class="sxs-lookup"><span data-stu-id="dd951-114">Requirements</span></span>  
 <span data-ttu-id="dd951-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dd951-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd951-116">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="dd951-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dd951-117">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="dd951-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dd951-118">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd951-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd951-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd951-119">See also</span></span>

- [<span data-ttu-id="dd951-120">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="dd951-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="dd951-121">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="dd951-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

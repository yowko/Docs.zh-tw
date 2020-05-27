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
ms.openlocfilehash: 220556ec130c7bff7c413405820c4fee0582b051
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008010"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="1d311-102">IMetaDataEmit::SetFieldProps 方法</span><span class="sxs-lookup"><span data-stu-id="1d311-102">IMetaDataEmit::SetFieldProps Method</span></span>
<span data-ttu-id="1d311-103">設定或更新指定欄位標記所參考之欄位的預設值。</span><span class="sxs-lookup"><span data-stu-id="1d311-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d311-104">語法</span><span class="sxs-lookup"><span data-stu-id="1d311-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,
    [in]  DWORD       dwFieldFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d311-105">參數</span><span class="sxs-lookup"><span data-stu-id="1d311-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="1d311-106">在目標欄位的 token。</span><span class="sxs-lookup"><span data-stu-id="1d311-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="1d311-107">在欄位屬性。</span><span class="sxs-lookup"><span data-stu-id="1d311-107">[in] Field attributes.</span></span> <span data-ttu-id="1d311-108">這是值的位元遮罩 `CorFieldAttr` 。</span><span class="sxs-lookup"><span data-stu-id="1d311-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="1d311-109">在`ELEMENT_TYPE_` *\** 常數值的。</span><span class="sxs-lookup"><span data-stu-id="1d311-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="1d311-110">這是 `CorElementType` 值。</span><span class="sxs-lookup"><span data-stu-id="1d311-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="1d311-111">如果沒有定義常數，請將此值設定為 `ELEMENT_TYPE_END` 。</span><span class="sxs-lookup"><span data-stu-id="1d311-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="1d311-112">在欄位的常數值。</span><span class="sxs-lookup"><span data-stu-id="1d311-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="1d311-113">在的大小，以 Unicode 字元為單位 `pValue` 。</span><span class="sxs-lookup"><span data-stu-id="1d311-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d311-114">需求</span><span class="sxs-lookup"><span data-stu-id="1d311-114">Requirements</span></span>  
 <span data-ttu-id="1d311-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1d311-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d311-116">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="1d311-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1d311-117">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="1d311-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1d311-118">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d311-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d311-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d311-119">See also</span></span>

- [<span data-ttu-id="1d311-120">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="1d311-120">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="1d311-121">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="1d311-121">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

---
title: IMetaDataImport::EnumTypeDefs 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeDefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type:
- apiref
ms.openlocfilehash: 4545f5f8d78e588c655a72340210a785b0feb619
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720408"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="6b0e8-102">IMetaDataImport::EnumTypeDefs 方法</span><span class="sxs-lookup"><span data-stu-id="6b0e8-102">IMetaDataImport::EnumTypeDefs Method</span></span>

<span data-ttu-id="6b0e8-103">列舉代表目前範圍內的所有類型的 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="6b0e8-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b0e8-104">語法</span><span class="sxs-lookup"><span data-stu-id="6b0e8-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b0e8-105">參數</span><span class="sxs-lookup"><span data-stu-id="6b0e8-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="6b0e8-106">擴展新列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="6b0e8-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="6b0e8-107">此方法的第一個呼叫必須是 Null。</span><span class="sxs-lookup"><span data-stu-id="6b0e8-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="6b0e8-108">在用來儲存 TypeDef 標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="6b0e8-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6b0e8-109">[in] `rTypeDefs` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="6b0e8-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="6b0e8-110">擴展傳回的 TypeDef 標記數目 `rTypeDefs` 。</span><span class="sxs-lookup"><span data-stu-id="6b0e8-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b0e8-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="6b0e8-111">Return Value</span></span>  
  
|<span data-ttu-id="6b0e8-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6b0e8-112">HRESULT</span></span>|<span data-ttu-id="6b0e8-113">描述</span><span class="sxs-lookup"><span data-stu-id="6b0e8-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6b0e8-114">`EnumTypeDefs` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="6b0e8-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6b0e8-115">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="6b0e8-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="6b0e8-116">在此情況下， `pcTypeDefs` 是零。</span><span class="sxs-lookup"><span data-stu-id="6b0e8-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b0e8-117">備註</span><span class="sxs-lookup"><span data-stu-id="6b0e8-117">Remarks</span></span>  

 <span data-ttu-id="6b0e8-118">TypeDef token 代表型別，例如類別或介面，以及透過擴充性機制加入的任何型別。</span><span class="sxs-lookup"><span data-stu-id="6b0e8-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b0e8-119">需求</span><span class="sxs-lookup"><span data-stu-id="6b0e8-119">Requirements</span></span>  

 <span data-ttu-id="6b0e8-120">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6b0e8-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b0e8-121">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="6b0e8-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6b0e8-122">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="6b0e8-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6b0e8-123">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b0e8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b0e8-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b0e8-124">See also</span></span>

- [<span data-ttu-id="6b0e8-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="6b0e8-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="6b0e8-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="6b0e8-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)

---
title: IMetaDataAssemblyImport::EnumExportedTypes 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumExportedTypes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumExportedTypes
helpviewer_keywords:
- EnumExportedTypes method [.NET Framework metadata]
- IMetaDataAssemblyImport::EnumExportedTypes method [.NET Framework metadata]
ms.assetid: e5912ed8-e4ce-438b-8ea3-d9e4c288d109
topic_type:
- apiref
ms.openlocfilehash: f00fe5bce2f808265add228406dfaa2ccc267545
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176002"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="f0574-102">IMetaDataAssemblyImport::EnumExportedTypes 方法</span><span class="sxs-lookup"><span data-stu-id="f0574-102">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>
<span data-ttu-id="f0574-103">枚舉當前中繼資料作用域中組件資訊清單中引用的匯出類型。</span><span class="sxs-lookup"><span data-stu-id="f0574-103">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0574-104">語法</span><span class="sxs-lookup"><span data-stu-id="f0574-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,
    [out] mdExportedType   rExportedTypes[],
    [in]  ULONG            cMax,
    [out] ULONG            *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0574-105">參數</span><span class="sxs-lookup"><span data-stu-id="f0574-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f0574-106">[進出]指向枚舉器的指標。</span><span class="sxs-lookup"><span data-stu-id="f0574-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="f0574-107">當首次調用該方法時，`EnumExportedTypes`這必須是 null 值。</span><span class="sxs-lookup"><span data-stu-id="f0574-107">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="f0574-108">[出]中繼資料權杖的`mdExportedType`枚舉。</span><span class="sxs-lookup"><span data-stu-id="f0574-108">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f0574-109">[在]可放置在`rExportedTypes`陣列中`mdExportedType`的最大權杖數。</span><span class="sxs-lookup"><span data-stu-id="f0574-109">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="f0574-110">[出]實際放置在`mdExportedType`中的`rExportedTypes`權杖數。</span><span class="sxs-lookup"><span data-stu-id="f0574-110">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0574-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="f0574-111">Return Value</span></span>  
  
|<span data-ttu-id="f0574-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f0574-112">HRESULT</span></span>|<span data-ttu-id="f0574-113">描述</span><span class="sxs-lookup"><span data-stu-id="f0574-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f0574-114">`EnumExportedTypes`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="f0574-114">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f0574-115">沒有要枚舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="f0574-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="f0574-116">在這種情況下，`pcTokens`設置為零。</span><span class="sxs-lookup"><span data-stu-id="f0574-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f0574-117">需求</span><span class="sxs-lookup"><span data-stu-id="f0574-117">Requirements</span></span>  
 <span data-ttu-id="f0574-118">**平臺：** 請參閱[系統要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f0574-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0574-119">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="f0574-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f0574-120">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f0574-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f0574-121">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0574-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0574-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0574-122">See also</span></span>

- [<span data-ttu-id="f0574-123">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="f0574-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)

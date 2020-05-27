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
ms.openlocfilehash: 514488c6e0d2e89de0d8ee483def485ec9f3ef25
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009095"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="600f5-102">IMetaDataAssemblyImport::EnumExportedTypes 方法</span><span class="sxs-lookup"><span data-stu-id="600f5-102">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>
<span data-ttu-id="600f5-103">列舉目前中繼資料範圍中的組件資訊清單所參考的匯出類型。</span><span class="sxs-lookup"><span data-stu-id="600f5-103">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="600f5-104">語法</span><span class="sxs-lookup"><span data-stu-id="600f5-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,
    [out] mdExportedType   rExportedTypes[],
    [in]  ULONG            cMax,
    [out] ULONG            *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="600f5-105">參數</span><span class="sxs-lookup"><span data-stu-id="600f5-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="600f5-106">[in、out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="600f5-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="600f5-107">第一次呼叫方法時，這必須是 null 值 `EnumExportedTypes` 。</span><span class="sxs-lookup"><span data-stu-id="600f5-107">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="600f5-108">脫銷`mdExportedType`元資料標記的列舉。</span><span class="sxs-lookup"><span data-stu-id="600f5-108">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="600f5-109">在`mdExportedType`可以放在陣列中的 token 數目上限 `rExportedTypes` 。</span><span class="sxs-lookup"><span data-stu-id="600f5-109">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="600f5-110">脫銷`mdExportedType`實際放入的權杖數目 `rExportedTypes` 。</span><span class="sxs-lookup"><span data-stu-id="600f5-110">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="600f5-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="600f5-111">Return Value</span></span>  
  
|<span data-ttu-id="600f5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="600f5-112">HRESULT</span></span>|<span data-ttu-id="600f5-113">描述</span><span class="sxs-lookup"><span data-stu-id="600f5-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="600f5-114">`EnumExportedTypes`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="600f5-114">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="600f5-115">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="600f5-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="600f5-116">在此情況下， `pcTokens` 會設定為零。</span><span class="sxs-lookup"><span data-stu-id="600f5-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="600f5-117">需求</span><span class="sxs-lookup"><span data-stu-id="600f5-117">Requirements</span></span>  
 <span data-ttu-id="600f5-118">**平臺：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="600f5-118">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="600f5-119">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="600f5-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="600f5-120">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="600f5-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="600f5-121">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="600f5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="600f5-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="600f5-122">See also</span></span>

- [<span data-ttu-id="600f5-123">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="600f5-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)

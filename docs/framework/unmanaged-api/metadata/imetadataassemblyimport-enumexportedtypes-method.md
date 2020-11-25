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
ms.openlocfilehash: a8b2377c48331ff9f0e69876c51fb78c7190f694
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708890"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="a550e-102">IMetaDataAssemblyImport::EnumExportedTypes 方法</span><span class="sxs-lookup"><span data-stu-id="a550e-102">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>

<span data-ttu-id="a550e-103">列舉目前中繼資料範圍內組件資訊清單中所參考的匯出類型。</span><span class="sxs-lookup"><span data-stu-id="a550e-103">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a550e-104">語法</span><span class="sxs-lookup"><span data-stu-id="a550e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,
    [out] mdExportedType   rExportedTypes[],
    [in]  ULONG            cMax,
    [out] ULONG            *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a550e-105">參數</span><span class="sxs-lookup"><span data-stu-id="a550e-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="a550e-106">[in，out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="a550e-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="a550e-107">第一次呼叫方法時，此值必須為 null 值 `EnumExportedTypes` 。</span><span class="sxs-lookup"><span data-stu-id="a550e-107">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="a550e-108">擴展 `mdExportedType` 元資料標記的列舉。</span><span class="sxs-lookup"><span data-stu-id="a550e-108">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a550e-109">在 `mdExportedType` 可放置在陣列中的最大 token 數目 `rExportedTypes` 。</span><span class="sxs-lookup"><span data-stu-id="a550e-109">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="a550e-110">擴展 `mdExportedType` 實際放置的權杖數目 `rExportedTypes` 。</span><span class="sxs-lookup"><span data-stu-id="a550e-110">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a550e-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="a550e-111">Return Value</span></span>  
  
|<span data-ttu-id="a550e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a550e-112">HRESULT</span></span>|<span data-ttu-id="a550e-113">描述</span><span class="sxs-lookup"><span data-stu-id="a550e-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a550e-114">`EnumExportedTypes` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="a550e-114">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a550e-115">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="a550e-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="a550e-116">在此情況下， `pcTokens` 會設定為零。</span><span class="sxs-lookup"><span data-stu-id="a550e-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a550e-117">需求</span><span class="sxs-lookup"><span data-stu-id="a550e-117">Requirements</span></span>  

 <span data-ttu-id="a550e-118">**平臺：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a550e-118">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a550e-119">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="a550e-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a550e-120">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="a550e-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a550e-121">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a550e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a550e-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a550e-122">See also</span></span>

- [<span data-ttu-id="a550e-123">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="a550e-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)

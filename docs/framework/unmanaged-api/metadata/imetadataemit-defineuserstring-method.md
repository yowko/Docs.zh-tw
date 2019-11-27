---
title: IMetaDataEmit::DefineUserString 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineUserString
helpviewer_keywords:
- DefineUserString method [.NET Framework metadata]
- IMetaDataEmit::DefineUserString method [.NET Framework metadata]
ms.assetid: 88fb7ef3-bbdf-429c-b678-c9c153456461
topic_type:
- apiref
ms.openlocfilehash: aa5d66d2408010d7a7b52ec68a18f667097795ae
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450182"
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="c138c-102">IMetaDataEmit::DefineUserString 方法</span><span class="sxs-lookup"><span data-stu-id="c138c-102">IMetaDataEmit::DefineUserString Method</span></span>
<span data-ttu-id="c138c-103">取得指定之文字字串的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="c138c-103">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c138c-104">語法</span><span class="sxs-lookup"><span data-stu-id="c138c-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineUserString (   
    [in]  LPCWSTR     szString,   
    [in]  ULONG       cchString,   
    [out] mdString    *pstk   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c138c-105">參數</span><span class="sxs-lookup"><span data-stu-id="c138c-105">Parameters</span></span>  
 `szString`  
 <span data-ttu-id="c138c-106">在要儲存的使用者字串。</span><span class="sxs-lookup"><span data-stu-id="c138c-106">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="c138c-107">在`szString`中寬字元的計數。</span><span class="sxs-lookup"><span data-stu-id="c138c-107">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="c138c-108">脫銷指派的字串 token。</span><span class="sxs-lookup"><span data-stu-id="c138c-108">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c138c-109">需求</span><span class="sxs-lookup"><span data-stu-id="c138c-109">Requirements</span></span>  
 <span data-ttu-id="c138c-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c138c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c138c-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="c138c-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c138c-112">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="c138c-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c138c-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c138c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c138c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c138c-114">See also</span></span>

- [<span data-ttu-id="c138c-115">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="c138c-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c138c-116">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="c138c-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

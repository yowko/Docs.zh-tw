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
ms.openlocfilehash: def77bb64e21b1421983cf263d488ecc1ddb9452
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009312"
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="33a13-102">IMetaDataEmit::DefineUserString 方法</span><span class="sxs-lookup"><span data-stu-id="33a13-102">IMetaDataEmit::DefineUserString Method</span></span>
<span data-ttu-id="33a13-103">取得指定之文字字串的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="33a13-103">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33a13-104">語法</span><span class="sxs-lookup"><span data-stu-id="33a13-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineUserString (
    [in]  LPCWSTR     szString,
    [in]  ULONG       cchString,
    [out] mdString    *pstk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33a13-105">參數</span><span class="sxs-lookup"><span data-stu-id="33a13-105">Parameters</span></span>  
 `szString`  
 <span data-ttu-id="33a13-106">在要儲存的使用者字串。</span><span class="sxs-lookup"><span data-stu-id="33a13-106">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="33a13-107">在中的寬字元計數 `szString` 。</span><span class="sxs-lookup"><span data-stu-id="33a13-107">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="33a13-108">脫銷指派的字串 token。</span><span class="sxs-lookup"><span data-stu-id="33a13-108">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33a13-109">需求</span><span class="sxs-lookup"><span data-stu-id="33a13-109">Requirements</span></span>  
 <span data-ttu-id="33a13-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="33a13-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33a13-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="33a13-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="33a13-112">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="33a13-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="33a13-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33a13-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33a13-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33a13-114">See also</span></span>

- [<span data-ttu-id="33a13-115">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="33a13-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="33a13-116">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="33a13-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

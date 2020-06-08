---
title: IMetaDataImport2::EnumMethodSpecs 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumMethodSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type:
- apiref
ms.openlocfilehash: 8f6fbc570e7ea85aca5b365611d58a1700fb27cd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490714"
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="4883a-102">IMetaDataImport2::EnumMethodSpecs 方法</span><span class="sxs-lookup"><span data-stu-id="4883a-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="4883a-103">取得與指定的 MethodDef 或 MemberRef token 相關聯的 MethodSpec 標記陣列的列舉值。</span><span class="sxs-lookup"><span data-stu-id="4883a-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4883a-104">語法</span><span class="sxs-lookup"><span data-stu-id="4883a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="4883a-105">參數</span><span class="sxs-lookup"><span data-stu-id="4883a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="4883a-106">[in、out]列舉值的指標 `rMethodSpecs` 。</span><span class="sxs-lookup"><span data-stu-id="4883a-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="4883a-107">在MemberRef 或 MethodDef token，代表要列舉其 MethodSpec 標記的方法。</span><span class="sxs-lookup"><span data-stu-id="4883a-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="4883a-108">如果的值 `tk` 為0（零），則會列舉範圍中的所有 MethodSpec token。</span><span class="sxs-lookup"><span data-stu-id="4883a-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="4883a-109">脫銷要列舉之 MethodSpec 標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="4883a-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4883a-110">在要放置在中的要求最大權杖數目 `rMethodSpecs` 。</span><span class="sxs-lookup"><span data-stu-id="4883a-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="4883a-111">脫銷所傳回的權杖數目 `rMethodSpecs` 。</span><span class="sxs-lookup"><span data-stu-id="4883a-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4883a-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="4883a-112">Return Value</span></span>  
  
|<span data-ttu-id="4883a-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4883a-113">HRESULT</span></span>|<span data-ttu-id="4883a-114">說明</span><span class="sxs-lookup"><span data-stu-id="4883a-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4883a-115">`EnumMethodSpecs`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="4883a-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="4883a-116">`phEnum`沒有成員元素。</span><span class="sxs-lookup"><span data-stu-id="4883a-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="4883a-117">在此情況下， `pcMethodSpecs` 會設為0（零）。</span><span class="sxs-lookup"><span data-stu-id="4883a-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4883a-118">規格需求</span><span class="sxs-lookup"><span data-stu-id="4883a-118">Requirements</span></span>  
 <span data-ttu-id="4883a-119">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4883a-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4883a-120">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="4883a-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4883a-121">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="4883a-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4883a-122">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4883a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4883a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4883a-123">See also</span></span>

- [<span data-ttu-id="4883a-124">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="4883a-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="4883a-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="4883a-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)

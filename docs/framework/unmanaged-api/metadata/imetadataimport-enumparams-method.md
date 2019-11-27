---
title: IMetaDataImport::EnumParams 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumParams
helpviewer_keywords:
- IMetaDataImport::EnumParams method [.NET Framework metadata]
- EnumParams method [.NET Framework metadata]
ms.assetid: 52118dc9-fe6e-4b39-aa48-c3cc3ea4214d
topic_type:
- apiref
ms.openlocfilehash: e5fa3647c86d97730e7ad6a2576dd34af75251d6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433953"
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="8dba4-102">IMetaDataImport::EnumParams 方法</span><span class="sxs-lookup"><span data-stu-id="8dba4-102">IMetaDataImport::EnumParams Method</span></span>
<span data-ttu-id="8dba4-103">列舉 ParamDef 語彙基元，其代表指定 MethodDef 語彙基元所參考之方法的參數。</span><span class="sxs-lookup"><span data-stu-id="8dba4-103">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dba4-104">語法</span><span class="sxs-lookup"><span data-stu-id="8dba4-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8dba4-105">參數</span><span class="sxs-lookup"><span data-stu-id="8dba4-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="8dba4-106">[in、out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="8dba4-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="8dba4-107">第一次呼叫此方法時，此值必須為 Null。</span><span class="sxs-lookup"><span data-stu-id="8dba4-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="8dba4-108">在MethodDef token，代表具有要列舉之參數的方法。</span><span class="sxs-lookup"><span data-stu-id="8dba4-108">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="8dba4-109">脫銷用來儲存 ParamDef 標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="8dba4-109">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8dba4-110">[in] `rParams` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="8dba4-110">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="8dba4-111">脫銷`rParams`中傳回的 ParamDef token 數目。</span><span class="sxs-lookup"><span data-stu-id="8dba4-111">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8dba4-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="8dba4-112">Return Value</span></span>  
  
|<span data-ttu-id="8dba4-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8dba4-113">HRESULT</span></span>|<span data-ttu-id="8dba4-114">描述</span><span class="sxs-lookup"><span data-stu-id="8dba4-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="8dba4-115">已成功傳回 `EnumParams`。</span><span class="sxs-lookup"><span data-stu-id="8dba4-115">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="8dba4-116">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="8dba4-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="8dba4-117">在此情況下，`pcTokens` 為零。</span><span class="sxs-lookup"><span data-stu-id="8dba4-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8dba4-118">需求</span><span class="sxs-lookup"><span data-stu-id="8dba4-118">Requirements</span></span>  
 <span data-ttu-id="8dba4-119">**平臺：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8dba4-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8dba4-120">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="8dba4-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8dba4-121">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="8dba4-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8dba4-122">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8dba4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dba4-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="8dba4-123">See also</span></span>

- [<span data-ttu-id="8dba4-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="8dba4-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="8dba4-125">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="8dba4-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

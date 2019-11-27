---
title: IMetaDataImport::GetRVA 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
ms.openlocfilehash: a3a5cadc1b5a9df7967aae271ff10296843121dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436952"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="529f6-102">IMetaDataImport::GetRVA 方法</span><span class="sxs-lookup"><span data-stu-id="529f6-102">IMetaDataImport::GetRVA Method</span></span>
<span data-ttu-id="529f6-103">取得指定標記所代表之方法或欄位的相對虛擬位址（RVA）和執行旗標。</span><span class="sxs-lookup"><span data-stu-id="529f6-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="529f6-104">語法</span><span class="sxs-lookup"><span data-stu-id="529f6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,   
   [out] ULONG       *pulCodeRVA,   
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="529f6-105">參數</span><span class="sxs-lookup"><span data-stu-id="529f6-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="529f6-106">在MethodDef 或 FieldDef 元資料標記，代表要為其傳回 RVA 的程式碼物件。</span><span class="sxs-lookup"><span data-stu-id="529f6-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="529f6-107">如果權杖是 FieldDef，此欄位必須是全域變數。</span><span class="sxs-lookup"><span data-stu-id="529f6-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="529f6-108">脫銷標記所表示之程式碼物件的相對虛擬位址的指標。</span><span class="sxs-lookup"><span data-stu-id="529f6-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="529f6-109">脫銷方法之執行旗標的指標。</span><span class="sxs-lookup"><span data-stu-id="529f6-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="529f6-110">這個值是[CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)列舉中的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="529f6-110">This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="529f6-111">只有在 `tk` 是 MethodDef token 時，`pdwImplFlags` 的值才有效。</span><span class="sxs-lookup"><span data-stu-id="529f6-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="529f6-112">需求</span><span class="sxs-lookup"><span data-stu-id="529f6-112">Requirements</span></span>  
 <span data-ttu-id="529f6-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="529f6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="529f6-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="529f6-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="529f6-115">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="529f6-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="529f6-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="529f6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="529f6-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="529f6-117">See also</span></span>

- [<span data-ttu-id="529f6-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="529f6-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="529f6-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="529f6-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

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
ms.openlocfilehash: 190bcacc84646cfd9294cf2b6b53b0474f38758f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177221"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="c2528-102">IMetaDataImport::GetRVA 方法</span><span class="sxs-lookup"><span data-stu-id="c2528-102">IMetaDataImport::GetRVA Method</span></span>
<span data-ttu-id="c2528-103">獲取由指定權杖表示的方法或欄位的相對虛擬位址 （RVA） 和實現標誌。</span><span class="sxs-lookup"><span data-stu-id="c2528-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2528-104">語法</span><span class="sxs-lookup"><span data-stu-id="c2528-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,
   [out] ULONG       *pulCodeRVA,
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2528-105">參數</span><span class="sxs-lookup"><span data-stu-id="c2528-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="c2528-106">[在]表示要返回 RVA 的代碼物件的 MethodDef 或 FieldDef 中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="c2528-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="c2528-107">如果權杖是 FieldDef，則該欄位必須是全域變數。</span><span class="sxs-lookup"><span data-stu-id="c2528-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="c2528-108">[出]指向權杖表示的代碼物件的相對虛擬位址的指標。</span><span class="sxs-lookup"><span data-stu-id="c2528-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="c2528-109">[出]指向方法的實現標誌的指標。</span><span class="sxs-lookup"><span data-stu-id="c2528-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="c2528-110">此值是[CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)枚舉中的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="c2528-110">This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="c2528-111">僅當 是`pdwImplFlags`MethodDef`tk`權杖時，值才有效。</span><span class="sxs-lookup"><span data-stu-id="c2528-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2528-112">需求</span><span class="sxs-lookup"><span data-stu-id="c2528-112">Requirements</span></span>  
 <span data-ttu-id="c2528-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c2528-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2528-114">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="c2528-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c2528-115">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="c2528-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c2528-116">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2528-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2528-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2528-117">See also</span></span>

- [<span data-ttu-id="c2528-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="c2528-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c2528-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="c2528-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

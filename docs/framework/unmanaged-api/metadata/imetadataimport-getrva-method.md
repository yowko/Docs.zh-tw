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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 96c013cd3e45e4ede0cbc9f42bf511a2eb3fc12d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223585"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="5e0ed-102">IMetaDataImport::GetRVA 方法</span><span class="sxs-lookup"><span data-stu-id="5e0ed-102">IMetaDataImport::GetRVA Method</span></span>
<span data-ttu-id="5e0ed-103">取得相對虛擬位址 (RVA) 和欄位指定的語彙基元所代表之方法的實作旗標。</span><span class="sxs-lookup"><span data-stu-id="5e0ed-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e0ed-104">語法</span><span class="sxs-lookup"><span data-stu-id="5e0ed-104">Syntax</span></span>  
  
```  
HRESULT GetRVA (  
   [in]  mdToken     tk,   
   [out] ULONG       *pulCodeRVA,   
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e0ed-105">參數</span><span class="sxs-lookup"><span data-stu-id="5e0ed-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="5e0ed-106">[in]MethodDef 或 FieldDef 中繼資料語彙基元，表示要傳回的 RVA 的程式碼物件。</span><span class="sxs-lookup"><span data-stu-id="5e0ed-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="5e0ed-107">如果 FieldDef 語彙基元，欄位必須是全域變數。</span><span class="sxs-lookup"><span data-stu-id="5e0ed-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="5e0ed-108">[out]語彙基元所代表的程式碼物件的相對虛擬位址指標。</span><span class="sxs-lookup"><span data-stu-id="5e0ed-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="5e0ed-109">[out]指標，該方法的實作旗標。</span><span class="sxs-lookup"><span data-stu-id="5e0ed-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="5e0ed-110">這個值是從位元遮罩[CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="5e0ed-110">This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="5e0ed-111">值`pdwImplFlags`無效，只有當`tk`為 MethodDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="5e0ed-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e0ed-112">需求</span><span class="sxs-lookup"><span data-stu-id="5e0ed-112">Requirements</span></span>  
 <span data-ttu-id="5e0ed-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5e0ed-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e0ed-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5e0ed-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5e0ed-115">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5e0ed-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="5e0ed-116">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="5e0ed-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5e0ed-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e0ed-117">See also</span></span>

- [<span data-ttu-id="5e0ed-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="5e0ed-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="5e0ed-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="5e0ed-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

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
ms.openlocfilehash: 1232e8c574f263f709a9b66c7b1b3d06cca5e4da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447207"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="f6e39-102">IMetaDataImport::GetRVA 方法</span><span class="sxs-lookup"><span data-stu-id="f6e39-102">IMetaDataImport::GetRVA Method</span></span>
<span data-ttu-id="f6e39-103">取得相對虛擬位址 (RVA) 和指定的語彙基元所代表的欄位之方法的實作旗標。</span><span class="sxs-lookup"><span data-stu-id="f6e39-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6e39-104">語法</span><span class="sxs-lookup"><span data-stu-id="f6e39-104">Syntax</span></span>  
  
```  
HRESULT GetRVA (  
   [in]  mdToken     tk,   
   [out] ULONG       *pulCodeRVA,   
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f6e39-105">參數</span><span class="sxs-lookup"><span data-stu-id="f6e39-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="f6e39-106">[in]MethodDef 或 FieldDef 中繼資料語彙基元，代表要傳回的 RVA 的程式碼物件。</span><span class="sxs-lookup"><span data-stu-id="f6e39-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="f6e39-107">如果 FieldDef 語彙基元，則此欄位必須是全域變數。</span><span class="sxs-lookup"><span data-stu-id="f6e39-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="f6e39-108">[out]語彙基元所代表的程式碼物件的相對虛擬位址指標。</span><span class="sxs-lookup"><span data-stu-id="f6e39-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="f6e39-109">[out]指標，該方法的實作旗標。</span><span class="sxs-lookup"><span data-stu-id="f6e39-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="f6e39-110">這個值是從位元遮罩[CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="f6e39-110">This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="f6e39-111">值`pdwImplFlags`有效才`tk`是 MethodDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f6e39-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6e39-112">需求</span><span class="sxs-lookup"><span data-stu-id="f6e39-112">Requirements</span></span>  
 <span data-ttu-id="f6e39-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f6e39-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6e39-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f6e39-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f6e39-115">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f6e39-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f6e39-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6e39-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6e39-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6e39-117">See Also</span></span>  
 [<span data-ttu-id="f6e39-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="f6e39-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="f6e39-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="f6e39-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

---
title: IMetaDataImport::GetParamForMethodIndex 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamForMethodIndex
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamForMethodIndex
helpviewer_keywords:
- IMetaDataImport::GetParamForMethodIndex method [.NET Framework metadata]
- GetParamForMethodIndex method [.NET Framework metadata]
ms.assetid: ec3bfa95-1920-4511-932e-3ff23d76fcb8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 28d4c9098076699de250ab1c43e5f9e353dc9752
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740108"
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="a06f8-102">IMetaDataImport::GetParamForMethodIndex 方法</span><span class="sxs-lookup"><span data-stu-id="a06f8-102">IMetaDataImport::GetParamForMethodIndex Method</span></span>
<span data-ttu-id="a06f8-103">取得表示指定的參數，指定 MethodDef 語彙基元所代表之方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a06f8-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a06f8-104">語法</span><span class="sxs-lookup"><span data-stu-id="a06f8-104">Syntax</span></span>  
  
```  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a06f8-105">參數</span><span class="sxs-lookup"><span data-stu-id="a06f8-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="a06f8-106">[in]語彙基元，表示這個方法傳回的參數 token。</span><span class="sxs-lookup"><span data-stu-id="a06f8-106">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="a06f8-107">[in]參數清單中要發生要求的參數序數的位置。</span><span class="sxs-lookup"><span data-stu-id="a06f8-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="a06f8-108">參數編號從一方法的傳回值在位置零開始。</span><span class="sxs-lookup"><span data-stu-id="a06f8-108">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="a06f8-109">[out]表示要求的參數 ParamDef 語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="a06f8-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a06f8-110">需求</span><span class="sxs-lookup"><span data-stu-id="a06f8-110">Requirements</span></span>  
 <span data-ttu-id="a06f8-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a06f8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a06f8-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a06f8-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a06f8-113">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a06f8-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a06f8-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a06f8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a06f8-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a06f8-115">See also</span></span>
- [<span data-ttu-id="a06f8-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="a06f8-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="a06f8-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="a06f8-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

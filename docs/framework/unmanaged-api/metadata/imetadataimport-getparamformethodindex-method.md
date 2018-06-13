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
ms.openlocfilehash: 31096f7a5fd23bbd54f2beb9258c9d529e94f373
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448755"
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="fb8e6-102">IMetaDataImport::GetParamForMethodIndex 方法</span><span class="sxs-lookup"><span data-stu-id="fb8e6-102">IMetaDataImport::GetParamForMethodIndex Method</span></span>
<span data-ttu-id="fb8e6-103">取得代表指定 MethodDef 語彙基元所表示之方法的指定的參數的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="fb8e6-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb8e6-104">語法</span><span class="sxs-lookup"><span data-stu-id="fb8e6-104">Syntax</span></span>  
  
```  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb8e6-105">參數</span><span class="sxs-lookup"><span data-stu-id="fb8e6-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="fb8e6-106">[in]表示要傳回的參數語彙基元的方法語彙基元。</span><span class="sxs-lookup"><span data-stu-id="fb8e6-106">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="fb8e6-107">[in]參數清單中要發生要求的參數序數的位置。</span><span class="sxs-lookup"><span data-stu-id="fb8e6-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="fb8e6-108">參數的編號從一方法的傳回值，在位置零開始。</span><span class="sxs-lookup"><span data-stu-id="fb8e6-108">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="fb8e6-109">[out]ParamDef 語彙基元，代表所要求的參數的指標。</span><span class="sxs-lookup"><span data-stu-id="fb8e6-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb8e6-110">需求</span><span class="sxs-lookup"><span data-stu-id="fb8e6-110">Requirements</span></span>  
 <span data-ttu-id="fb8e6-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fb8e6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb8e6-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fb8e6-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fb8e6-113">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fb8e6-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fb8e6-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb8e6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb8e6-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb8e6-115">See Also</span></span>  
 [<span data-ttu-id="fb8e6-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="fb8e6-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="fb8e6-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="fb8e6-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

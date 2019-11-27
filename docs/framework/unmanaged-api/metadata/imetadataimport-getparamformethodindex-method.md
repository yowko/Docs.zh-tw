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
ms.openlocfilehash: a70691b9c519bc59ae7df7a86d5d6697db565575
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437172"
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="5dba1-102">IMetaDataImport::GetParamForMethodIndex 方法</span><span class="sxs-lookup"><span data-stu-id="5dba1-102">IMetaDataImport::GetParamForMethodIndex Method</span></span>
<span data-ttu-id="5dba1-103">取得權杖，表示指定的 MethodDef token 所表示之方法的指定參數。</span><span class="sxs-lookup"><span data-stu-id="5dba1-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dba1-104">語法</span><span class="sxs-lookup"><span data-stu-id="5dba1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5dba1-105">參數</span><span class="sxs-lookup"><span data-stu-id="5dba1-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="5dba1-106">在Token，表示要為其傳回參數 token 的方法。</span><span class="sxs-lookup"><span data-stu-id="5dba1-106">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="5dba1-107">在參數清單中要求的參數發生所在的序數位置。</span><span class="sxs-lookup"><span data-stu-id="5dba1-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="5dba1-108">參數是從1開始編號，且方法的傳回值位於位置零。</span><span class="sxs-lookup"><span data-stu-id="5dba1-108">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="5dba1-109">脫銷ParamDef token 的指標，表示要求的參數。</span><span class="sxs-lookup"><span data-stu-id="5dba1-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dba1-110">需求</span><span class="sxs-lookup"><span data-stu-id="5dba1-110">Requirements</span></span>  
 <span data-ttu-id="5dba1-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5dba1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5dba1-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="5dba1-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5dba1-113">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5dba1-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5dba1-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5dba1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dba1-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5dba1-115">See also</span></span>

- [<span data-ttu-id="5dba1-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="5dba1-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="5dba1-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="5dba1-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

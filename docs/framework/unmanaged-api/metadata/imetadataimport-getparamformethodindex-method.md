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
ms.openlocfilehash: d4d3ba5713398876b55c072f0cda7eb5d599c4d5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729276"
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="a9bb0-102">IMetaDataImport::GetParamForMethodIndex 方法</span><span class="sxs-lookup"><span data-stu-id="a9bb0-102">IMetaDataImport::GetParamForMethodIndex Method</span></span>

<span data-ttu-id="a9bb0-103">取得 token，表示指定之 MethodDef token 所代表之方法的指定參數。</span><span class="sxs-lookup"><span data-stu-id="a9bb0-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9bb0-104">語法</span><span class="sxs-lookup"><span data-stu-id="a9bb0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9bb0-105">參數</span><span class="sxs-lookup"><span data-stu-id="a9bb0-105">Parameters</span></span>  

 `md`  
 <span data-ttu-id="a9bb0-106">在表示傳回參數標記之方法的 token。</span><span class="sxs-lookup"><span data-stu-id="a9bb0-106">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="a9bb0-107">在參數清單中的序數位置，其中出現要求的參數。</span><span class="sxs-lookup"><span data-stu-id="a9bb0-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="a9bb0-108">參數的編號是從1開始，而方法的傳回值是在位置零。</span><span class="sxs-lookup"><span data-stu-id="a9bb0-108">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="a9bb0-109">擴展ParamDef token 的指標，代表所要求的參數。</span><span class="sxs-lookup"><span data-stu-id="a9bb0-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9bb0-110">需求</span><span class="sxs-lookup"><span data-stu-id="a9bb0-110">Requirements</span></span>  

 <span data-ttu-id="a9bb0-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a9bb0-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9bb0-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="a9bb0-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a9bb0-113">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="a9bb0-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a9bb0-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9bb0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9bb0-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9bb0-115">See also</span></span>

- [<span data-ttu-id="a9bb0-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="a9bb0-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="a9bb0-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="a9bb0-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)

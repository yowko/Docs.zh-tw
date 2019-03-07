---
title: IMetaDataImport::GetPinvokeMap 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPinvokeMap
helpviewer_keywords:
- IMetaDataImport::GetPinvokeMap method [.NET Framework metadata]
- GetPinvokeMap method [.NET Framework metadata]
ms.assetid: b8685c1e-b80c-4198-8eb3-748d6f48a99e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec32b285713e3e506359c4c831eb076d2b47a967
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499759"
---
# <a name="imetadataimportgetpinvokemap-method"></a><span data-ttu-id="6032b-102">IMetaDataImport::GetPinvokeMap 方法</span><span class="sxs-lookup"><span data-stu-id="6032b-102">IMetaDataImport::GetPinvokeMap Method</span></span>
<span data-ttu-id="6032b-103">取得 ModuleRef 語彙基元以代表 PInvoke 呼叫的目標組件。</span><span class="sxs-lookup"><span data-stu-id="6032b-103">Gets a ModuleRef token to represent the target assembly of a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6032b-104">語法</span><span class="sxs-lookup"><span data-stu-id="6032b-104">Syntax</span></span>  
  
```  
HRESULT GetPinvokeMap (  
   [in]  mdToken       tk,  
   [out] DWORD         *pdwMappingFlags,  
   [out] LPWSTR        szImportName,  
   [in]  ULONG         cchImportName,  
   [out] ULONG         *pchImportName,  
   [out] mdModuleRef   *pmrImportDLL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6032b-105">參數</span><span class="sxs-lookup"><span data-stu-id="6032b-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="6032b-106">[in]若要取得 PInvoke 對應中繼資料的 fielddef 語彙或 MethodDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="6032b-106">[in] A FieldDef or MethodDef token to get the PInvoke mapping metadata for.</span></span>  
  
 `pdwMappingFlags`  
 <span data-ttu-id="6032b-107">[out]指標，用於對應的旗標。</span><span class="sxs-lookup"><span data-stu-id="6032b-107">[out] A pointer to flags used for mapping.</span></span> <span data-ttu-id="6032b-108">這個值是從位元遮罩[CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="6032b-108">This value is a bitmask from the [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) enumeration.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="6032b-109">[out]未受管理的目標 DLL 的名稱。</span><span class="sxs-lookup"><span data-stu-id="6032b-109">[out] The name of the unmanaged target DLL.</span></span>  
  
 `cchImportName`  
 <span data-ttu-id="6032b-110">[in]寬字元大小`szImportName`。</span><span class="sxs-lookup"><span data-stu-id="6032b-110">[in] The size in wide characters of `szImportName`.</span></span>  
  
 `pchImportName`  
 <span data-ttu-id="6032b-111">[out]中傳回的寬字元數目`szImportName`。</span><span class="sxs-lookup"><span data-stu-id="6032b-111">[out] The number of wide characters returned in `szImportName`.</span></span>  
  
 `pmrImportDLL`  
 <span data-ttu-id="6032b-112">[out]表示未受管理的目標物件程式庫 ModuleRef 語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="6032b-112">[out] A pointer to a ModuleRef token that represents the unmanaged target object library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6032b-113">需求</span><span class="sxs-lookup"><span data-stu-id="6032b-113">Requirements</span></span>  
 <span data-ttu-id="6032b-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6032b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6032b-115">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6032b-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6032b-116">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6032b-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6032b-117">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6032b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6032b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6032b-118">See also</span></span>
- [<span data-ttu-id="6032b-119">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="6032b-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6032b-120">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="6032b-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

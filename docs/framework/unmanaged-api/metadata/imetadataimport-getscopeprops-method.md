---
title: IMetaDataImport::GetScopeProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetScopeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7c41e05ecf4e33f7ca711befdd90275452439df
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718854"
---
# <a name="imetadataimportgetscopeprops-method"></a><span data-ttu-id="f7699-102">IMetaDataImport::GetScopeProps 方法</span><span class="sxs-lookup"><span data-stu-id="f7699-102">IMetaDataImport::GetScopeProps Method</span></span>
<span data-ttu-id="f7699-103">取得目前中繼資料範圍內組件或模組的名稱以及選擇性地取得其版本識別項。</span><span class="sxs-lookup"><span data-stu-id="f7699-103">Gets the name and optionally the version identifier of the assembly or module in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7699-104">語法</span><span class="sxs-lookup"><span data-stu-id="f7699-104">Syntax</span></span>  
  
```  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7699-105">參數</span><span class="sxs-lookup"><span data-stu-id="f7699-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="f7699-106">[out]組件或模組名稱的的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f7699-106">[out] A buffer for the assembly or module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="f7699-107">[in]寬字元大小`szName`。</span><span class="sxs-lookup"><span data-stu-id="f7699-107">[in] The size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="f7699-108">[out]中傳回的寬字元數目`szName`。</span><span class="sxs-lookup"><span data-stu-id="f7699-108">[out] The number of wide characters returned in `szName`.</span></span>  
  
 `pmvid`  
 <span data-ttu-id="f7699-109">[out，optional]可唯一識別組件或模組的版本 GUID 指標。</span><span class="sxs-lookup"><span data-stu-id="f7699-109">[out, optional] A pointer to a GUID that uniquely identifies the version of the assembly or module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7699-110">備註</span><span class="sxs-lookup"><span data-stu-id="f7699-110">Remarks</span></span>  
 <span data-ttu-id="f7699-111">[Imetadataemit:: Setmoduleprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md)方法用來設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="f7699-111">The [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) method is used to set these properties.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7699-112">需求</span><span class="sxs-lookup"><span data-stu-id="f7699-112">Requirements</span></span>  
 <span data-ttu-id="f7699-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f7699-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7699-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f7699-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f7699-115">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f7699-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f7699-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7699-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7699-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7699-117">See also</span></span>
- [<span data-ttu-id="f7699-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="f7699-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f7699-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="f7699-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

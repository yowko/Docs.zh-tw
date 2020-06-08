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
ms.openlocfilehash: 0916b6382bb9352616d85e21f423301dc6aa9fa9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490844"
---
# <a name="imetadataimportgetscopeprops-method"></a><span data-ttu-id="5e836-102">IMetaDataImport::GetScopeProps 方法</span><span class="sxs-lookup"><span data-stu-id="5e836-102">IMetaDataImport::GetScopeProps Method</span></span>
<span data-ttu-id="5e836-103">取得目前中繼資料範圍內組件或模組的名稱以及選擇性地取得其版本識別項。</span><span class="sxs-lookup"><span data-stu-id="5e836-103">Gets the name and optionally the version identifier of the assembly or module in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e836-104">語法</span><span class="sxs-lookup"><span data-stu-id="5e836-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e836-105">參數</span><span class="sxs-lookup"><span data-stu-id="5e836-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="5e836-106">脫銷元件或模組名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="5e836-106">[out] A buffer for the assembly or module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="5e836-107">在的大小（以寬字元為單位） `szName` 。</span><span class="sxs-lookup"><span data-stu-id="5e836-107">[in] The size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="5e836-108">脫銷在中傳回的寬字元數 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="5e836-108">[out] The number of wide characters returned in `szName`.</span></span>  
  
 `pmvid`  
 <span data-ttu-id="5e836-109">[out，optional]GUID 的指標，可唯一識別元件或模組的版本。</span><span class="sxs-lookup"><span data-stu-id="5e836-109">[out, optional] A pointer to a GUID that uniquely identifies the version of the assembly or module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e836-110">備註</span><span class="sxs-lookup"><span data-stu-id="5e836-110">Remarks</span></span>  
 <span data-ttu-id="5e836-111">[IMetaDataEmit：： SetModuleProps](imetadataemit-setmoduleprops-method.md)方法是用來設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="5e836-111">The [IMetaDataEmit::SetModuleProps](imetadataemit-setmoduleprops-method.md) method is used to set these properties.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e836-112">規格需求</span><span class="sxs-lookup"><span data-stu-id="5e836-112">Requirements</span></span>  
 <span data-ttu-id="5e836-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5e836-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e836-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="5e836-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5e836-115">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5e836-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5e836-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e836-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e836-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e836-117">See also</span></span>

- [<span data-ttu-id="5e836-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="5e836-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="5e836-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="5e836-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)

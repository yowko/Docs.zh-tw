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
ms.openlocfilehash: 5a89d1406daa9a2416a708b63d88fd9005234015
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729196"
---
# <a name="imetadataimportgetscopeprops-method"></a><span data-ttu-id="81789-102">IMetaDataImport::GetScopeProps 方法</span><span class="sxs-lookup"><span data-stu-id="81789-102">IMetaDataImport::GetScopeProps Method</span></span>

<span data-ttu-id="81789-103">取得目前中繼資料範圍內組件或模組的名稱以及選擇性地取得其版本識別項。</span><span class="sxs-lookup"><span data-stu-id="81789-103">Gets the name and optionally the version identifier of the assembly or module in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81789-104">語法</span><span class="sxs-lookup"><span data-stu-id="81789-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81789-105">參數</span><span class="sxs-lookup"><span data-stu-id="81789-105">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="81789-106">擴展元件或模組名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="81789-106">[out] A buffer for the assembly or module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="81789-107">在的大小（以寬字元為單位） `szName` 。</span><span class="sxs-lookup"><span data-stu-id="81789-107">[in] The size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="81789-108">擴展傳回的寬字元數 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="81789-108">[out] The number of wide characters returned in `szName`.</span></span>  
  
 `pmvid`  
 <span data-ttu-id="81789-109">[out，optional]GUID 的指標，可唯一識別元件或模組的版本。</span><span class="sxs-lookup"><span data-stu-id="81789-109">[out, optional] A pointer to a GUID that uniquely identifies the version of the assembly or module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81789-110">備註</span><span class="sxs-lookup"><span data-stu-id="81789-110">Remarks</span></span>  

 <span data-ttu-id="81789-111">[IMetaDataEmit：： SetModuleProps](imetadataemit-setmoduleprops-method.md)方法是用來設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="81789-111">The [IMetaDataEmit::SetModuleProps](imetadataemit-setmoduleprops-method.md) method is used to set these properties.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81789-112">需求</span><span class="sxs-lookup"><span data-stu-id="81789-112">Requirements</span></span>  

 <span data-ttu-id="81789-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="81789-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81789-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="81789-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="81789-115">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="81789-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="81789-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81789-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81789-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81789-117">See also</span></span>

- [<span data-ttu-id="81789-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="81789-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="81789-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="81789-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)

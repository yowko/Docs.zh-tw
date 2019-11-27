---
title: IMetaDataImport::GetTypeRefProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeRefProps
helpviewer_keywords:
- IMetaDataImport::GetTypeRefProps method [.NET Framework metadata]
- GetTypeRefProps method [.NET Framework metadata]
ms.assetid: 01837955-ce1e-4068-b338-fd473bd77d1d
topic_type:
- apiref
ms.openlocfilehash: 6ea7605e062eb77e0488b3a9561c4d83be16fa7d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436705"
---
# <a name="imetadataimportgettyperefprops-method"></a><span data-ttu-id="81883-102">IMetaDataImport::GetTypeRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="81883-102">IMetaDataImport::GetTypeRefProps Method</span></span>
<span data-ttu-id="81883-103">取得與指定的 TypeRef 標記所參考的 <xref:System.Type> 相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="81883-103">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81883-104">語法</span><span class="sxs-lookup"><span data-stu-id="81883-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81883-105">參數</span><span class="sxs-lookup"><span data-stu-id="81883-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="81883-106">在表示要傳回中繼資料之類型的 TypeRef token。</span><span class="sxs-lookup"><span data-stu-id="81883-106">[in] The TypeRef token that represents the type to return metadata for.</span></span>  
  
 `ptkResolutionScope`  
 <span data-ttu-id="81883-107">脫銷做為參考之範圍的指標。</span><span class="sxs-lookup"><span data-stu-id="81883-107">[out] A pointer to the scope in which the reference is made.</span></span> <span data-ttu-id="81883-108">這個值是 AssemblyRef 或 ModuleRef token。</span><span class="sxs-lookup"><span data-stu-id="81883-108">This value is an AssemblyRef or ModuleRef token.</span></span>  
  
 `szName`  
 <span data-ttu-id="81883-109">脫銷包含型別名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="81883-109">[out] A buffer containing the type name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="81883-110">在要求的大小，以 `szName`的寬字元為單位。</span><span class="sxs-lookup"><span data-stu-id="81883-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="81883-111">脫銷`szName`的寬字元傳回大小。</span><span class="sxs-lookup"><span data-stu-id="81883-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81883-112">需求</span><span class="sxs-lookup"><span data-stu-id="81883-112">Requirements</span></span>  
 <span data-ttu-id="81883-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="81883-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81883-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="81883-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="81883-115">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="81883-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="81883-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81883-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81883-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="81883-117">See also</span></span>

- [<span data-ttu-id="81883-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="81883-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="81883-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="81883-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

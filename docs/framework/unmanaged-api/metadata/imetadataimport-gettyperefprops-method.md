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
ms.openlocfilehash: 273922e00c3e5319d5a03652cc77b69f4479ea67
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503519"
---
# <a name="imetadataimportgettyperefprops-method"></a><span data-ttu-id="a8d53-102">IMetaDataImport::GetTypeRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="a8d53-102">IMetaDataImport::GetTypeRefProps Method</span></span>
<span data-ttu-id="a8d53-103">取得與指定的 TypeRef 標記所參考之相關聯的中繼資料 <xref:System.Type> 。</span><span class="sxs-lookup"><span data-stu-id="a8d53-103">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8d53-104">語法</span><span class="sxs-lookup"><span data-stu-id="a8d53-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8d53-105">參數</span><span class="sxs-lookup"><span data-stu-id="a8d53-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="a8d53-106">在表示要傳回中繼資料之類型的 TypeRef token。</span><span class="sxs-lookup"><span data-stu-id="a8d53-106">[in] The TypeRef token that represents the type to return metadata for.</span></span>  
  
 `ptkResolutionScope`  
 <span data-ttu-id="a8d53-107">脫銷做為參考之範圍的指標。</span><span class="sxs-lookup"><span data-stu-id="a8d53-107">[out] A pointer to the scope in which the reference is made.</span></span> <span data-ttu-id="a8d53-108">這個值是 AssemblyRef 或 ModuleRef token。</span><span class="sxs-lookup"><span data-stu-id="a8d53-108">This value is an AssemblyRef or ModuleRef token.</span></span>  
  
 `szName`  
 <span data-ttu-id="a8d53-109">脫銷包含型別名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="a8d53-109">[out] A buffer containing the type name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="a8d53-110">在所要求的大小（以寬字元為單位） `szName` 。</span><span class="sxs-lookup"><span data-stu-id="a8d53-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="a8d53-111">脫銷傳回的大小（以寬字元為單位） `szName` 。</span><span class="sxs-lookup"><span data-stu-id="a8d53-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8d53-112">規格需求</span><span class="sxs-lookup"><span data-stu-id="a8d53-112">Requirements</span></span>  
 <span data-ttu-id="a8d53-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a8d53-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8d53-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="a8d53-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a8d53-115">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a8d53-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a8d53-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8d53-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8d53-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8d53-117">See also</span></span>

- [<span data-ttu-id="a8d53-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="a8d53-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="a8d53-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="a8d53-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)

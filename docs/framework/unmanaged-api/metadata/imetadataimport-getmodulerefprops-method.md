---
title: IMetaDataImport::GetModuleRefProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleRefProps
helpviewer_keywords:
- GetModuleRefProps method [.NET Framework metadata]
- IMetaDataImport::GetModuleRefProps method [.NET Framework metadata]
ms.assetid: b558e766-4c11-4628-ae47-b4e0a1800168
topic_type:
- apiref
ms.openlocfilehash: 606a3f2cfba05b014960842c5db77149f449193d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733122"
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="5d4f8-102">IMetaDataImport::GetModuleRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="5d4f8-102">IMetaDataImport::GetModuleRefProps Method</span></span>

<span data-ttu-id="5d4f8-103">取得指定中繼資料語彙基元所參考的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="5d4f8-103">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d4f8-104">語法</span><span class="sxs-lookup"><span data-stu-id="5d4f8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,
   [in]  ULONG               cchName,
   [out] ULONG               *pchName
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d4f8-105">參數</span><span class="sxs-lookup"><span data-stu-id="5d4f8-105">Parameters</span></span>  

 `mur`  
 <span data-ttu-id="5d4f8-106">在參考模組的 ModuleRef 元資料標記，以取得的中繼資料資訊。</span><span class="sxs-lookup"><span data-stu-id="5d4f8-106">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="5d4f8-107">擴展保存模組名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="5d4f8-107">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="5d4f8-108">在要求的大小（ `szName` 以寬字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="5d4f8-108">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="5d4f8-109">擴展傳回的大小（ `szName` 以寬字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="5d4f8-109">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d4f8-110">需求</span><span class="sxs-lookup"><span data-stu-id="5d4f8-110">Requirements</span></span>  

 <span data-ttu-id="5d4f8-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5d4f8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d4f8-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="5d4f8-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5d4f8-113">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="5d4f8-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5d4f8-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d4f8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d4f8-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d4f8-115">See also</span></span>

- [<span data-ttu-id="5d4f8-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="5d4f8-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="5d4f8-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="5d4f8-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)

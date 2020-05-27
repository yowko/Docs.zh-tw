---
title: IMetaDataEmit::DefineModuleRef 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineModuleRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineModuleRef
helpviewer_keywords:
- DefineModuleRef method [.NET Framework metadata]
- IMetaDataEmit::DefineModuleRef method [.NET Framework metadata]
ms.assetid: f2833594-d90b-4a71-9a53-34b12470c64a
topic_type:
- apiref
ms.openlocfilehash: efff491d92ac7910f43f76965ef98d1d0e4ba0aa
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004422"
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="7c996-102">IMetaDataEmit::DefineModuleRef 方法</span><span class="sxs-lookup"><span data-stu-id="7c996-102">IMetaDataEmit::DefineModuleRef Method</span></span>
<span data-ttu-id="7c996-103">建立具有指定名稱之模組的中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="7c996-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c996-104">語法</span><span class="sxs-lookup"><span data-stu-id="7c996-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineModuleRef (
    [in]  LPCWSTR           szName,
    [out] mdModuleRef       *pmur
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c996-105">參數</span><span class="sxs-lookup"><span data-stu-id="7c996-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="7c996-106">在其他中繼資料檔案的名稱，通常是 DLL。</span><span class="sxs-lookup"><span data-stu-id="7c996-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="7c996-107">此為檔案名。</span><span class="sxs-lookup"><span data-stu-id="7c996-107">This is the file name only.</span></span> <span data-ttu-id="7c996-108">請勿使用完整路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="7c996-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="7c996-109">脫銷指派的 `mdModuleRef` token。</span><span class="sxs-lookup"><span data-stu-id="7c996-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c996-110">需求</span><span class="sxs-lookup"><span data-stu-id="7c996-110">Requirements</span></span>  
 <span data-ttu-id="7c996-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7c996-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c996-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="7c996-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7c996-113">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="7c996-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c996-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c996-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c996-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c996-115">See also</span></span>

- [<span data-ttu-id="7c996-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="7c996-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="7c996-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="7c996-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

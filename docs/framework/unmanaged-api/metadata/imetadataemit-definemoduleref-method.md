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
ms.openlocfilehash: 96d24705d80dabcda691edec497a4a30b6d37dc4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719550"
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="f1b80-102">IMetaDataEmit::DefineModuleRef 方法</span><span class="sxs-lookup"><span data-stu-id="f1b80-102">IMetaDataEmit::DefineModuleRef Method</span></span>

<span data-ttu-id="f1b80-103">使用指定的名稱，建立模組的中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="f1b80-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1b80-104">語法</span><span class="sxs-lookup"><span data-stu-id="f1b80-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineModuleRef (
    [in]  LPCWSTR           szName,
    [out] mdModuleRef       *pmur
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1b80-105">參數</span><span class="sxs-lookup"><span data-stu-id="f1b80-105">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="f1b80-106">在其他中繼資料檔案的名稱，通常是 DLL。</span><span class="sxs-lookup"><span data-stu-id="f1b80-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="f1b80-107">這是唯一的檔案名。</span><span class="sxs-lookup"><span data-stu-id="f1b80-107">This is the file name only.</span></span> <span data-ttu-id="f1b80-108">請勿使用完整路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="f1b80-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="f1b80-109">擴展指派的 `mdModuleRef` 標記。</span><span class="sxs-lookup"><span data-stu-id="f1b80-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1b80-110">需求</span><span class="sxs-lookup"><span data-stu-id="f1b80-110">Requirements</span></span>  

 <span data-ttu-id="f1b80-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f1b80-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1b80-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="f1b80-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f1b80-113">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="f1b80-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1b80-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1b80-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1b80-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1b80-115">See also</span></span>

- [<span data-ttu-id="f1b80-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="f1b80-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="f1b80-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="f1b80-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

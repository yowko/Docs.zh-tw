---
title: IMetaDataEmit::DefineMemberRef 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMemberRef
helpviewer_keywords:
- DefineMemberRef method [.NET Framework metadata]
- IMetaDataEmit::DefineMemberRef method [.NET Framework metadata]
ms.assetid: 21b5bcb8-ea75-4962-8acc-ad17584061e5
topic_type:
- apiref
ms.openlocfilehash: 576f4561ed782f091840ac378831110a1bfef9c6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004685"
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="f05f9-102">IMetaDataEmit::DefineMemberRef 方法</span><span class="sxs-lookup"><span data-stu-id="f05f9-102">IMetaDataEmit::DefineMemberRef Method</span></span>
<span data-ttu-id="f05f9-103">定義對目前範圍外之模組成員的參考，並取得該參考定義的 token。</span><span class="sxs-lookup"><span data-stu-id="f05f9-103">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f05f9-104">語法</span><span class="sxs-lookup"><span data-stu-id="f05f9-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMemberRef (
    [in]  mdToken           tkImport,
    [in]  LPCWSTR           szName,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMemberRef       *pmr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f05f9-105">參數</span><span class="sxs-lookup"><span data-stu-id="f05f9-105">Parameters</span></span>  
 `tkImport`  
 <span data-ttu-id="f05f9-106">在如果成員不是全域，則為目標成員的類別或介面的 Token;如果成員為全域，則 `mdModuleRef` 為該其他檔案的標記。</span><span class="sxs-lookup"><span data-stu-id="f05f9-106">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="f05f9-107">在目標成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="f05f9-107">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="f05f9-108">在目標成員的簽章。</span><span class="sxs-lookup"><span data-stu-id="f05f9-108">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="f05f9-109">在中的位元組計數 `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="f05f9-109">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="f05f9-110">脫銷`mdMemberRef`指派的 token。</span><span class="sxs-lookup"><span data-stu-id="f05f9-110">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f05f9-111">需求</span><span class="sxs-lookup"><span data-stu-id="f05f9-111">Requirements</span></span>  
 <span data-ttu-id="f05f9-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f05f9-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f05f9-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="f05f9-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f05f9-114">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="f05f9-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f05f9-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f05f9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f05f9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f05f9-116">See also</span></span>

- [<span data-ttu-id="f05f9-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="f05f9-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="f05f9-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="f05f9-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

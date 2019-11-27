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
ms.openlocfilehash: 696389b51328e167212fb2292a873c34b9263811
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431827"
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="ab324-102">IMetaDataEmit::DefineMemberRef 方法</span><span class="sxs-lookup"><span data-stu-id="ab324-102">IMetaDataEmit::DefineMemberRef Method</span></span>
<span data-ttu-id="ab324-103">定義對目前範圍外之模組成員的參考，並取得該參考定義的 token。</span><span class="sxs-lookup"><span data-stu-id="ab324-103">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab324-104">語法</span><span class="sxs-lookup"><span data-stu-id="ab324-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMemberRef (   
    [in]  mdToken           tkImport,   
    [in]  LPCWSTR           szName,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMemberRef       *pmr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab324-105">參數</span><span class="sxs-lookup"><span data-stu-id="ab324-105">Parameters</span></span>  
 `tkImport`  
 <span data-ttu-id="ab324-106">在如果成員不是全域，則為目標成員的類別或介面的 Token;如果成員為全域，則為該其他檔案的 `mdModuleRef` token。</span><span class="sxs-lookup"><span data-stu-id="ab324-106">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="ab324-107">在目標成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="ab324-107">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="ab324-108">在目標成員的簽章。</span><span class="sxs-lookup"><span data-stu-id="ab324-108">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="ab324-109">在`pvSigBlob`中的位元組計數。</span><span class="sxs-lookup"><span data-stu-id="ab324-109">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="ab324-110">脫銷指派的 `mdMemberRef` token。</span><span class="sxs-lookup"><span data-stu-id="ab324-110">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab324-111">需求</span><span class="sxs-lookup"><span data-stu-id="ab324-111">Requirements</span></span>  
 <span data-ttu-id="ab324-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ab324-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab324-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="ab324-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ab324-114">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="ab324-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab324-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab324-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab324-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab324-116">See also</span></span>

- [<span data-ttu-id="ab324-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="ab324-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ab324-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="ab324-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

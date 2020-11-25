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
ms.openlocfilehash: 597ba1884351ee6d8b7eb7e0f3f01ce3ad733304
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716638"
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="875b6-102">IMetaDataEmit::DefineMemberRef 方法</span><span class="sxs-lookup"><span data-stu-id="875b6-102">IMetaDataEmit::DefineMemberRef Method</span></span>

<span data-ttu-id="875b6-103">定義對目前範圍之外之模組成員的參考，並取得該參考定義的標記。</span><span class="sxs-lookup"><span data-stu-id="875b6-103">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="875b6-104">語法</span><span class="sxs-lookup"><span data-stu-id="875b6-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMemberRef (
    [in]  mdToken           tkImport,
    [in]  LPCWSTR           szName,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMemberRef       *pmr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="875b6-105">參數</span><span class="sxs-lookup"><span data-stu-id="875b6-105">Parameters</span></span>  

 `tkImport`  
 <span data-ttu-id="875b6-106">在如果成員不是全域的，則為目標成員的類別或介面的 Token;如果成員是全域的，則 `mdModuleRef` 為該其他檔案的標記。</span><span class="sxs-lookup"><span data-stu-id="875b6-106">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="875b6-107">在目標成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="875b6-107">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="875b6-108">在目標成員的簽章。</span><span class="sxs-lookup"><span data-stu-id="875b6-108">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="875b6-109">在中的位元組計數 `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="875b6-109">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="875b6-110">擴展 `mdMemberRef` 指派的權杖。</span><span class="sxs-lookup"><span data-stu-id="875b6-110">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="875b6-111">需求</span><span class="sxs-lookup"><span data-stu-id="875b6-111">Requirements</span></span>  

 <span data-ttu-id="875b6-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="875b6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="875b6-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="875b6-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="875b6-114">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="875b6-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="875b6-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="875b6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="875b6-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="875b6-116">See also</span></span>

- [<span data-ttu-id="875b6-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="875b6-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="875b6-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="875b6-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

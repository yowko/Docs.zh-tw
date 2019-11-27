---
title: ICeeGen::GetSectionDataLen 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionDataLen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionDataLen
helpviewer_keywords:
- ICeeGen::GetSectionDataLen method [.NET Framework metadata]
- GetSectionDataLen method [.NET Framework metadata]
ms.assetid: e2a06ee4-b8ee-49c7-935a-c1031a29eef2
topic_type:
- apiref
ms.openlocfilehash: 277e2584049fae397cf91281a65d05b0b49d9454
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448085"
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="27179-102">ICeeGen::GetSectionDataLen 方法</span><span class="sxs-lookup"><span data-stu-id="27179-102">ICeeGen::GetSectionDataLen Method</span></span>
<span data-ttu-id="27179-103">取得指定區段的長度。</span><span class="sxs-lookup"><span data-stu-id="27179-103">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="27179-104">這個方法已過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="27179-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27179-105">語法</span><span class="sxs-lookup"><span data-stu-id="27179-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27179-106">參數</span><span class="sxs-lookup"><span data-stu-id="27179-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="27179-107">在將取得其長度的資料區段。</span><span class="sxs-lookup"><span data-stu-id="27179-107">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="27179-108">脫銷所指定區段的傳回長度。</span><span class="sxs-lookup"><span data-stu-id="27179-108">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27179-109">備註</span><span class="sxs-lookup"><span data-stu-id="27179-109">Remarks</span></span>  
 <span data-ttu-id="27179-110">只有在您有其他方法未處理的特殊區段需求時，才呼叫 `GetSectionDataLen`。</span><span class="sxs-lookup"><span data-stu-id="27179-110">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27179-111">需求</span><span class="sxs-lookup"><span data-stu-id="27179-111">Requirements</span></span>  
 <span data-ttu-id="27179-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="27179-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27179-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="27179-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="27179-114">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="27179-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="27179-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27179-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27179-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27179-116">See also</span></span>

- [<span data-ttu-id="27179-117">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="27179-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)

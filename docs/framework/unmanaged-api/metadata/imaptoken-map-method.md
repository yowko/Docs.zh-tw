---
title: IMapToken::Map 方法
ms.date: 03/30/2017
api_name:
- IMapToken.Map
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type:
- apiref
ms.openlocfilehash: 027694cee1b3e4d990796ba31300918f6d859679
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008192"
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="e631e-102">IMapToken::Map 方法</span><span class="sxs-lookup"><span data-stu-id="e631e-102">IMapToken::Map Method</span></span>
<span data-ttu-id="e631e-103">使用中繼資料簽章來對應元件之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="e631e-103">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e631e-104">語法</span><span class="sxs-lookup"><span data-stu-id="e631e-104">Syntax</span></span>  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e631e-105">參數</span><span class="sxs-lookup"><span data-stu-id="e631e-105">Parameters</span></span>  
 `tkImp`  
 <span data-ttu-id="e631e-106">在表示已匯入之程式碼物件的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="e631e-106">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="e631e-107">在表示發出的程式碼物件的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="e631e-107">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e631e-108">備註</span><span class="sxs-lookup"><span data-stu-id="e631e-108">Remarks</span></span>  
 <span data-ttu-id="e631e-109">在合併期間發生權杖重新對應時，會將原始權杖的範圍限定在匯入的（來源）中繼資料範圍內，而新的 token 會限定在發出的（目標）中繼資料範圍中。</span><span class="sxs-lookup"><span data-stu-id="e631e-109">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e631e-110">需求</span><span class="sxs-lookup"><span data-stu-id="e631e-110">Requirements</span></span>  
 <span data-ttu-id="e631e-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e631e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e631e-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="e631e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e631e-113">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="e631e-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e631e-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e631e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e631e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e631e-115">See also</span></span>

- [<span data-ttu-id="e631e-116">IMapToken 介面</span><span class="sxs-lookup"><span data-stu-id="e631e-116">IMapToken Interface</span></span>](imaptoken-interface.md)

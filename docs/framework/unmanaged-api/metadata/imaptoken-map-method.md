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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ece12247e48a0a005fd542bf76a32a1c6eeaa7cb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478398"
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="0682d-102">IMapToken::Map 方法</span><span class="sxs-lookup"><span data-stu-id="0682d-102">IMapToken::Map Method</span></span>
<span data-ttu-id="0682d-103">對應使用中繼資料簽章的組件之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="0682d-103">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0682d-104">語法</span><span class="sxs-lookup"><span data-stu-id="0682d-104">Syntax</span></span>  
  
```  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0682d-105">參數</span><span class="sxs-lookup"><span data-stu-id="0682d-105">Parameters</span></span>  
 `tkImp`  
 <span data-ttu-id="0682d-106">[in]表示匯入的程式碼物件的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="0682d-106">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="0682d-107">[in]表示發出的程式碼物件的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="0682d-107">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0682d-108">備註</span><span class="sxs-lookup"><span data-stu-id="0682d-108">Remarks</span></span>  
 <span data-ttu-id="0682d-109">當語彙基元重新對應，就會發生在合併期間時，原始的語彙基元的範圍匯入 （來源） 中繼資料範圍內，新的語彙基元的範圍中發出 （目標） 中繼資料範圍。</span><span class="sxs-lookup"><span data-stu-id="0682d-109">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0682d-110">需求</span><span class="sxs-lookup"><span data-stu-id="0682d-110">Requirements</span></span>  
 <span data-ttu-id="0682d-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0682d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0682d-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0682d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0682d-113">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0682d-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0682d-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0682d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0682d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0682d-115">See also</span></span>
- [<span data-ttu-id="0682d-116">IMapToken 介面</span><span class="sxs-lookup"><span data-stu-id="0682d-116">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)

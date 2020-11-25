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
ms.openlocfilehash: 51cca1ab61027090b0d22781dfd740038bc9372d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718198"
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="9f018-102">IMapToken::Map 方法</span><span class="sxs-lookup"><span data-stu-id="9f018-102">IMapToken::Map Method</span></span>

<span data-ttu-id="9f018-103">使用中繼資料簽章對應元件之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="9f018-103">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f018-104">語法</span><span class="sxs-lookup"><span data-stu-id="9f018-104">Syntax</span></span>  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f018-105">參數</span><span class="sxs-lookup"><span data-stu-id="9f018-105">Parameters</span></span>  

 `tkImp`  
 <span data-ttu-id="9f018-106">在代表匯入之程式碼物件的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="9f018-106">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="9f018-107">在代表發出的程式碼物件的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="9f018-107">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f018-108">備註</span><span class="sxs-lookup"><span data-stu-id="9f018-108">Remarks</span></span>  

 <span data-ttu-id="9f018-109">在合併期間發生權杖重新對應時，原始的權杖範圍會限定在匯入的 (源) 中繼資料範圍內，而新的權杖會限定在發出的 (目標) 中繼資料範圍內。</span><span class="sxs-lookup"><span data-stu-id="9f018-109">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f018-110">需求</span><span class="sxs-lookup"><span data-stu-id="9f018-110">Requirements</span></span>  

 <span data-ttu-id="9f018-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9f018-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f018-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="9f018-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9f018-113">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="9f018-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9f018-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f018-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f018-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f018-115">See also</span></span>

- [<span data-ttu-id="9f018-116">IMapToken 介面</span><span class="sxs-lookup"><span data-stu-id="9f018-116">IMapToken Interface</span></span>](imaptoken-interface.md)

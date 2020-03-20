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
ms.openlocfilehash: 428b022ed560648f59798154d5987d382938c280
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176067"
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="a87a1-102">IMapToken::Map 方法</span><span class="sxs-lookup"><span data-stu-id="a87a1-102">IMapToken::Map Method</span></span>
<span data-ttu-id="a87a1-103">使用中繼資料簽名對應程式集之間的關係。</span><span class="sxs-lookup"><span data-stu-id="a87a1-103">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a87a1-104">語法</span><span class="sxs-lookup"><span data-stu-id="a87a1-104">Syntax</span></span>  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a87a1-105">參數</span><span class="sxs-lookup"><span data-stu-id="a87a1-105">Parameters</span></span>  
 `tkImp`  
 <span data-ttu-id="a87a1-106">[在]表示導入的代碼物件的中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="a87a1-106">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="a87a1-107">[在]表示已發出的代碼物件的中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="a87a1-107">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a87a1-108">備註</span><span class="sxs-lookup"><span data-stu-id="a87a1-108">Remarks</span></span>  
 <span data-ttu-id="a87a1-109">當令牌重新映射在合併期間發生時，原始權杖在導入的（源）中繼資料作用域中作用域，新權杖在已發出（目標）中繼資料作用域中作用域。</span><span class="sxs-lookup"><span data-stu-id="a87a1-109">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a87a1-110">需求</span><span class="sxs-lookup"><span data-stu-id="a87a1-110">Requirements</span></span>  
 <span data-ttu-id="a87a1-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a87a1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a87a1-112">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="a87a1-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a87a1-113">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a87a1-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a87a1-114">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a87a1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a87a1-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a87a1-115">See also</span></span>

- [<span data-ttu-id="a87a1-116">IMapToken 介面</span><span class="sxs-lookup"><span data-stu-id="a87a1-116">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)

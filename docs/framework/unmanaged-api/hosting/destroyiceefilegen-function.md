---
title: DestroyICeeFileGen 函式
ms.date: 03/30/2017
api_name:
- DestroyICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- DestroyICeeFileGen
helpviewer_keywords:
- DestroyICeeFileGen function [.NET Framework hosting]
ms.assetid: dc1e2235-e721-4cb2-a0b8-6b0c030d7bab
topic_type:
- apiref
ms.openlocfilehash: 495d84470c559df13ea64b63dd00582f4335d4e3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673172"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="43674-102">DestroyICeeFileGen 函式</span><span class="sxs-lookup"><span data-stu-id="43674-102">DestroyICeeFileGen Function</span></span>

<span data-ttu-id="43674-103">終結 [ICeeFileGen](iceefilegen-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="43674-103">Destroys an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="43674-104">此函式已在 .NET Framework 4 中被取代。</span><span class="sxs-lookup"><span data-stu-id="43674-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43674-105">語法</span><span class="sxs-lookup"><span data-stu-id="43674-105">Syntax</span></span>  
  
```cpp  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43674-106">參數</span><span class="sxs-lookup"><span data-stu-id="43674-106">Parameters</span></span>  

 `ceeFileGen`  
 <span data-ttu-id="43674-107">在要終結的 `ICeeFileGen` 物件。</span><span class="sxs-lookup"><span data-stu-id="43674-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43674-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="43674-108">Return Value</span></span>  

 <span data-ttu-id="43674-109">這個方法會傳回標準 COM 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="43674-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43674-110">備註</span><span class="sxs-lookup"><span data-stu-id="43674-110">Remarks</span></span>  

 <span data-ttu-id="43674-111">`DestroyICeeFileGen` 終結 `ICeeFileGen` [CreateICeeFileGen](createiceefilegen-function.md) 函數所建立的物件。</span><span class="sxs-lookup"><span data-stu-id="43674-111">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43674-112">需求</span><span class="sxs-lookup"><span data-stu-id="43674-112">Requirements</span></span>  

 <span data-ttu-id="43674-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="43674-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43674-114">**標頭：** ICeeFileGen。h</span><span class="sxs-lookup"><span data-stu-id="43674-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="43674-115">連結 **庫：** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="43674-115">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="43674-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43674-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43674-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43674-117">See also</span></span>

- [<span data-ttu-id="43674-118">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="43674-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)

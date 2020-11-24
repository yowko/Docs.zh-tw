---
title: CreateICeeFileGen 函式
ms.date: 03/30/2017
api_name:
- CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- CreateICeeFileGen
helpviewer_keywords:
- CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type:
- apiref
ms.openlocfilehash: 454cfa2dd1b676f32649050625b1074fbd776d54
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673328"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="780c1-102">CreateICeeFileGen 函式</span><span class="sxs-lookup"><span data-stu-id="780c1-102">CreateICeeFileGen Function</span></span>

<span data-ttu-id="780c1-103">建立 [ICeeFileGen](iceefilegen-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="780c1-103">Creates an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="780c1-104">此函式已在 .NET Framework 4 中被取代。</span><span class="sxs-lookup"><span data-stu-id="780c1-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="780c1-105">語法</span><span class="sxs-lookup"><span data-stu-id="780c1-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="780c1-106">參數</span><span class="sxs-lookup"><span data-stu-id="780c1-106">Parameters</span></span>  

 `ceeFileGen`  
 <span data-ttu-id="780c1-107">擴展新物件的位址指標 `ICeeFileGen` 。</span><span class="sxs-lookup"><span data-stu-id="780c1-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="780c1-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="780c1-108">Return Value</span></span>  

 <span data-ttu-id="780c1-109">這個方法會傳回標準 COM 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="780c1-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="780c1-110">備註</span><span class="sxs-lookup"><span data-stu-id="780c1-110">Remarks</span></span>  

 <span data-ttu-id="780c1-111">`ICeeFileGen`物件是用來 (CLR) 可攜式可執行檔 (PE) 檔來建立 common language runtime。</span><span class="sxs-lookup"><span data-stu-id="780c1-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="780c1-112">呼叫 [DestroyICeeFileGen](destroyiceefilegen-function.md) 函式，以 `ICeeFileGen` 在完成時終結物件。</span><span class="sxs-lookup"><span data-stu-id="780c1-112">Call the [DestroyICeeFileGen](destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="780c1-113">需求</span><span class="sxs-lookup"><span data-stu-id="780c1-113">Requirements</span></span>  

 <span data-ttu-id="780c1-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="780c1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="780c1-115">**標頭：** ICeeFileGen。h</span><span class="sxs-lookup"><span data-stu-id="780c1-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="780c1-116">連結 **庫：** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="780c1-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="780c1-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="780c1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="780c1-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="780c1-118">See also</span></span>

- [<span data-ttu-id="780c1-119">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="780c1-119">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)

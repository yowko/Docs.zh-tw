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
ms.openlocfilehash: 294b82efd66704014aab1b73171afe9165f17664
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616446"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="12858-102">CreateICeeFileGen 函式</span><span class="sxs-lookup"><span data-stu-id="12858-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="12858-103">建立[ICeeFileGen](iceefilegen-class.md)物件。</span><span class="sxs-lookup"><span data-stu-id="12858-103">Creates an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="12858-104">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="12858-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12858-105">語法</span><span class="sxs-lookup"><span data-stu-id="12858-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12858-106">參數</span><span class="sxs-lookup"><span data-stu-id="12858-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="12858-107">脫銷新物件位址的指標 `ICeeFileGen` 。</span><span class="sxs-lookup"><span data-stu-id="12858-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12858-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="12858-108">Return Value</span></span>  
 <span data-ttu-id="12858-109">這個方法會傳回標準 COM 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="12858-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12858-110">備註</span><span class="sxs-lookup"><span data-stu-id="12858-110">Remarks</span></span>  
 <span data-ttu-id="12858-111">`ICeeFileGen`物件是用來建立 common language runtime （CLR）可移植執行檔（PE）檔案。</span><span class="sxs-lookup"><span data-stu-id="12858-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="12858-112">完成時，呼叫[DestroyICeeFileGen](destroyiceefilegen-function.md)函式以終結 `ICeeFileGen` 物件。</span><span class="sxs-lookup"><span data-stu-id="12858-112">Call the [DestroyICeeFileGen](destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12858-113">需求</span><span class="sxs-lookup"><span data-stu-id="12858-113">Requirements</span></span>  
 <span data-ttu-id="12858-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="12858-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12858-115">**標頭：** ICeeFileGen。h</span><span class="sxs-lookup"><span data-stu-id="12858-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="12858-116">連結**庫：** MSCorPE .dll</span><span class="sxs-lookup"><span data-stu-id="12858-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="12858-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12858-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12858-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12858-118">See also</span></span>

- [<span data-ttu-id="12858-119">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="12858-119">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)

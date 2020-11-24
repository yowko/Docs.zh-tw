---
title: GetResolutionScope 方法
ms.date: 03/30/2017
api_name:
- IALink.GetResolutionScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetResolutionScope
helpviewer_keywords:
- GetResolutionScope method
ms.assetid: 5b48ca60-dacd-44b2-9979-4a5122f00812
topic_type:
- apiref
ms.openlocfilehash: 6318890dd6f0259d8d6a7675380684a129c14c8b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684667"
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="98ac8-102">GetResolutionScope 方法</span><span class="sxs-lookup"><span data-stu-id="98ac8-102">GetResolutionScope Method</span></span>

<span data-ttu-id="98ac8-103">抓取給定型別的範圍。</span><span class="sxs-lookup"><span data-stu-id="98ac8-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98ac8-104">語法</span><span class="sxs-lookup"><span data-stu-id="98ac8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="98ac8-105">參數</span><span class="sxs-lookup"><span data-stu-id="98ac8-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="98ac8-106">元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="98ac8-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="98ac8-107">需要參考的檔案。</span><span class="sxs-lookup"><span data-stu-id="98ac8-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="98ac8-108">在中定義類型之檔案的標記，通常是使用 [ImportFile 方法](importfile-method.md)來取出。</span><span class="sxs-lookup"><span data-stu-id="98ac8-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="98ac8-109">接收元件或模組參考。</span><span class="sxs-lookup"><span data-stu-id="98ac8-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="98ac8-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="98ac8-110">Return Value</span></span>  

 <span data-ttu-id="98ac8-111">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="98ac8-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98ac8-112">需求</span><span class="sxs-lookup"><span data-stu-id="98ac8-112">Requirements</span></span>  

 <span data-ttu-id="98ac8-113">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="98ac8-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98ac8-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98ac8-114">See also</span></span>

- [<span data-ttu-id="98ac8-115">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="98ac8-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="98ac8-116">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="98ac8-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="98ac8-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="98ac8-117">ALink API</span></span>](index.md)

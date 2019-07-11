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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c6c2e741df594e265fdef51a602a9a4927733b7c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741871"
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="e84da-102">GetResolutionScope 方法</span><span class="sxs-lookup"><span data-stu-id="e84da-102">GetResolutionScope Method</span></span>
<span data-ttu-id="e84da-103">擷取指定型別的範圍。</span><span class="sxs-lookup"><span data-stu-id="e84da-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e84da-104">語法</span><span class="sxs-lookup"><span data-stu-id="e84da-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e84da-105">參數</span><span class="sxs-lookup"><span data-stu-id="e84da-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e84da-106">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="e84da-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="e84da-107">需要參考的檔案。</span><span class="sxs-lookup"><span data-stu-id="e84da-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="e84da-108">語彙基元的檔案該型別定義中，通常使用的擷取[ImportFile 方法](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)。</span><span class="sxs-lookup"><span data-stu-id="e84da-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="e84da-109">接收的組件或模組參考。</span><span class="sxs-lookup"><span data-stu-id="e84da-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e84da-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="e84da-110">Return Value</span></span>  
 <span data-ttu-id="e84da-111">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="e84da-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e84da-112">需求</span><span class="sxs-lookup"><span data-stu-id="e84da-112">Requirements</span></span>  
 <span data-ttu-id="e84da-113">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="e84da-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e84da-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e84da-114">See also</span></span>

- [<span data-ttu-id="e84da-115">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="e84da-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="e84da-116">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="e84da-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="e84da-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="e84da-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)

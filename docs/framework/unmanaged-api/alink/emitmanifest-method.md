---
title: EmitManifest 方法
ms.date: 03/30/2017
api_name:
- EmitManifest
- IALink.EmitManifest
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitManifest
helpviewer_keywords:
- EmitManifest method
ms.assetid: fdebc1f3-b62e-4d9e-b775-8ccaa8ecb250
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 051b5f47db05301f3a3326a2cc4cc5cf5c8b1ec2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137822"
---
# <a name="emitmanifest-method"></a><span data-ttu-id="78e90-102">EmitManifest 方法</span><span class="sxs-lookup"><span data-stu-id="78e90-102">EmitManifest Method</span></span>
<span data-ttu-id="78e90-103">發出的最後一個資訊清單。</span><span class="sxs-lookup"><span data-stu-id="78e90-103">Emits the final manifest.</span></span> <span data-ttu-id="78e90-104">匯入所有其他檔案和設定所有選項之後呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="78e90-104">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="78e90-105">請勿呼叫這個方法的未繫結的模組。</span><span class="sxs-lookup"><span data-stu-id="78e90-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78e90-106">語法</span><span class="sxs-lookup"><span data-stu-id="78e90-106">Syntax</span></span>  
  
```  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="78e90-107">參數</span><span class="sxs-lookup"><span data-stu-id="78e90-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="78e90-108">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="78e90-108">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="78e90-109">接收要保留在組件檔案中，從擷取的大小[StrongNameSignatureSize 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md)。</span><span class="sxs-lookup"><span data-stu-id="78e90-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="78e90-110">選擇性地接收的組件資訊清單語彙基元。</span><span class="sxs-lookup"><span data-stu-id="78e90-110">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78e90-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="78e90-111">Return Value</span></span>  
 <span data-ttu-id="78e90-112">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="78e90-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78e90-113">需求</span><span class="sxs-lookup"><span data-stu-id="78e90-113">Requirements</span></span>  
 <span data-ttu-id="78e90-114">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="78e90-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78e90-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78e90-115">See also</span></span>

- [<span data-ttu-id="78e90-116">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="78e90-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="78e90-117">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="78e90-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="78e90-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="78e90-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)

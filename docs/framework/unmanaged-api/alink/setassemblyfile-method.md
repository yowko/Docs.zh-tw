---
title: "SetAssemblyFile 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.SetAssemblyFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile
helpviewer_keywords:
- SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c0be76e93ab41860f7f3416d0baffe3e4daf84c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="028ca-102">SetAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="028ca-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="028ca-103">指定要建置的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="028ca-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="028ca-104">不適用於產生繫結的模組時使用。</span><span class="sxs-lookup"><span data-stu-id="028ca-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="028ca-105">語法</span><span class="sxs-lookup"><span data-stu-id="028ca-105">Syntax</span></span>  
  
```  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="028ca-106">參數</span><span class="sxs-lookup"><span data-stu-id="028ca-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="028ca-107">資訊清單檔案的完整限定的名稱。</span><span class="sxs-lookup"><span data-stu-id="028ca-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="028ca-108">指標[IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="028ca-108">Pointer to [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="028ca-109">中所定義的旗標[AssemblyFlags 列舉](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="028ca-109">Flags as defined in [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="028ca-110">產生的組件的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="028ca-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="028ca-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="028ca-111">Return Value</span></span>  
 <span data-ttu-id="028ca-112">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="028ca-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="028ca-113">需求</span><span class="sxs-lookup"><span data-stu-id="028ca-113">Requirements</span></span>  
 <span data-ttu-id="028ca-114">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="028ca-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="028ca-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="028ca-115">See Also</span></span>  
 [<span data-ttu-id="028ca-116">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="028ca-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="028ca-117">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="028ca-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="028ca-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="028ca-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)

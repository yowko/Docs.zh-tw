---
title: "SetAssemblyFile2 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.SetAssemblyFile2
api_location: alink.dll
api_type: COM
f1_keywords: SetAssemblyFile2
helpviewer_keywords: SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7363a8f633d5f447f72e27ba03055f589564bdd2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="04671-102">SetAssemblyFile2 方法</span><span class="sxs-lookup"><span data-stu-id="04671-102">SetAssemblyFile2 Method</span></span>
<span data-ttu-id="04671-103">設定的名稱和新的組件的選項。</span><span class="sxs-lookup"><span data-stu-id="04671-103">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="04671-104">當您產生未繫結的模組時，請勿呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="04671-104">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04671-105">語法</span><span class="sxs-lookup"><span data-stu-id="04671-105">Syntax</span></span>  
  
```  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04671-106">參數</span><span class="sxs-lookup"><span data-stu-id="04671-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="04671-107">資訊清單檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="04671-107">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="04671-108">[IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)介面，此檔案。</span><span class="sxs-lookup"><span data-stu-id="04671-108">[IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="04671-109">選項由[AssemblyFlags 列舉](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="04671-109">Options represented by [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="04671-110">正在建構的組件所收到的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="04671-110">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04671-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="04671-111">Return Value</span></span>  
 <span data-ttu-id="04671-112">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="04671-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04671-113">需求</span><span class="sxs-lookup"><span data-stu-id="04671-113">Requirements</span></span>  
 <span data-ttu-id="04671-114">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="04671-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04671-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04671-115">See Also</span></span>  
 [<span data-ttu-id="04671-116">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="04671-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="04671-117">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="04671-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="04671-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="04671-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)

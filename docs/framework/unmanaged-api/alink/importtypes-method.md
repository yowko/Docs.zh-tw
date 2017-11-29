---
title: "ImportTypes 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ImportTypes
api_location: alink.dll
api_type: COM
f1_keywords: ImportTypes
helpviewer_keywords: ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b8fb83d4e3244010550cb21fedbc6c3b1c5d60d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="importtypes-method"></a><span data-ttu-id="aebd3-102">ImportTypes 方法</span><span class="sxs-lookup"><span data-stu-id="aebd3-102">ImportTypes Method</span></span>
<span data-ttu-id="aebd3-103">起始從透過匯入每個範圍的型別匯入[ImportFile 方法](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)。</span><span class="sxs-lookup"><span data-stu-id="aebd3-103">Initiates the importing of types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aebd3-104">語法</span><span class="sxs-lookup"><span data-stu-id="aebd3-104">Syntax</span></span>  
  
```  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aebd3-105">參數</span><span class="sxs-lookup"><span data-stu-id="aebd3-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="aebd3-106">若要匯入的組件識別碼。</span><span class="sxs-lookup"><span data-stu-id="aebd3-106">ID of the assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="aebd3-107">要從匯入的檔案識別碼。</span><span class="sxs-lookup"><span data-stu-id="aebd3-107">ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="aebd3-108">若要匯入的以零為起始範圍。</span><span class="sxs-lookup"><span data-stu-id="aebd3-108">Zero-based scope to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="aebd3-109">在此範圍內接收列舉值類型的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="aebd3-109">Receives enumerator handle for the types in this scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="aebd3-110">選擇性地接收[IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="aebd3-110">Optionally receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="aebd3-111">選擇性地指定範圍內接收類型的計數。</span><span class="sxs-lookup"><span data-stu-id="aebd3-111">Optionally receives count of types in the indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aebd3-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="aebd3-112">Return Value</span></span>  
 <span data-ttu-id="aebd3-113">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="aebd3-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aebd3-114">需求</span><span class="sxs-lookup"><span data-stu-id="aebd3-114">Requirements</span></span>  
 <span data-ttu-id="aebd3-115">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="aebd3-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aebd3-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aebd3-116">See Also</span></span>  
 [<span data-ttu-id="aebd3-117">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="aebd3-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="aebd3-118">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="aebd3-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="aebd3-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="aebd3-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)

---
title: "ImportFileEx 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.ImportFileEx
api_location: alink.dll
api_type: COM
f1_keywords: ImportFileEx
helpviewer_keywords: ImportFileEx method
ms.assetid: ad276f3f-b303-46ac-97e0-66a377adaa4f
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 71a7bc1ba9f23f1c581ca3528752e04003d9857c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="importfileex-method"></a><span data-ttu-id="4d111-102">ImportFileEx 方法</span><span class="sxs-lookup"><span data-stu-id="4d111-102">ImportFileEx Method</span></span>
<span data-ttu-id="4d111-103">匯入指定組件或未繫結的模組。</span><span class="sxs-lookup"><span data-stu-id="4d111-103">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d111-104">語法</span><span class="sxs-lookup"><span data-stu-id="4d111-104">Syntax</span></span>  
  
```  
HRESULT ImportFileEx(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d111-105">參數</span><span class="sxs-lookup"><span data-stu-id="4d111-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="4d111-106">要從中匯入檔案的完整限定的名稱。</span><span class="sxs-lookup"><span data-stu-id="4d111-106">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="4d111-107">選用的目標檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="4d111-107">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="4d111-108">如果為 TRUE，會使用 ImportTypes，否則匯入必須手動執行。</span><span class="sxs-lookup"><span data-stu-id="4d111-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="4d111-109">旗標，以傳送到[OpenScope 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)。</span><span class="sxs-lookup"><span data-stu-id="4d111-109">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="4d111-110">接收匯入的檔案識別碼。</span><span class="sxs-lookup"><span data-stu-id="4d111-110">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="4d111-111">接收的組件匯入範圍[IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="4d111-111">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="4d111-112">如果檔案不是組件是設為 NULL。</span><span class="sxs-lookup"><span data-stu-id="4d111-112">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="4d111-113">接收匯入的檔案及/或範圍的數目。</span><span class="sxs-lookup"><span data-stu-id="4d111-113">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d111-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="4d111-114">Return Value</span></span>  
 <span data-ttu-id="4d111-115">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="4d111-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d111-116">需求</span><span class="sxs-lookup"><span data-stu-id="4d111-116">Requirements</span></span>  
 <span data-ttu-id="4d111-117">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="4d111-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d111-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d111-118">See Also</span></span>  
 [<span data-ttu-id="4d111-119">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="4d111-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="4d111-120">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="4d111-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="4d111-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="4d111-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)

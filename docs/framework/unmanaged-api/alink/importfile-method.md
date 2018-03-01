---
title: "ImportFile 方法"
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
- IALink.ImportFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile
helpviewer_keywords:
- ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b5d4f93336fe19210086c39b8db6d167b3caa222
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="importfile-method"></a><span data-ttu-id="0172a-102">ImportFile 方法</span><span class="sxs-lookup"><span data-stu-id="0172a-102">ImportFile Method</span></span>
<span data-ttu-id="0172a-103">匯入組件和未繫結的模組。</span><span class="sxs-lookup"><span data-stu-id="0172a-103">Imports assemblies and unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0172a-104">語法</span><span class="sxs-lookup"><span data-stu-id="0172a-104">Syntax</span></span>  
  
```  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0172a-105">參數</span><span class="sxs-lookup"><span data-stu-id="0172a-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="0172a-106">要匯入檔案的完整限定的名稱。</span><span class="sxs-lookup"><span data-stu-id="0172a-106">Fully qualified name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="0172a-107">可用來重新命名檔案，因為它會連結至組件的選擇性的輸出檔名稱。</span><span class="sxs-lookup"><span data-stu-id="0172a-107">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="0172a-108">如果為 TRUE，會使用 ImportTypes，否則匯入必須手動執行。</span><span class="sxs-lookup"><span data-stu-id="0172a-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="0172a-109">語彙基元的唯一檔案識別碼的儲存位置的指標。</span><span class="sxs-lookup"><span data-stu-id="0172a-109">Pointer to token where a unique file ID will be stored.</span></span> <span data-ttu-id="0172a-110">組件或檔案，可以是檔案。</span><span class="sxs-lookup"><span data-stu-id="0172a-110">The file can be an assembly or a file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="0172a-111">接收指標[IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="0172a-111">Receives pointer to [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md).</span></span> <span data-ttu-id="0172a-112">如果檔案不是組件時，就可以是 NULL。</span><span class="sxs-lookup"><span data-stu-id="0172a-112">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="0172a-113">檔案及/或已匯入的範圍數目指標。</span><span class="sxs-lookup"><span data-stu-id="0172a-113">Pointer to the count of files and/or scopes that have been imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0172a-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="0172a-114">Return Value</span></span>  
 <span data-ttu-id="0172a-115">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="0172a-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0172a-116">需求</span><span class="sxs-lookup"><span data-stu-id="0172a-116">Requirements</span></span>  
 <span data-ttu-id="0172a-117">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="0172a-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0172a-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="0172a-118">See Also</span></span>  
 [<span data-ttu-id="0172a-119">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="0172a-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="0172a-120">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="0172a-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="0172a-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="0172a-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)

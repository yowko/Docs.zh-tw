---
title: ImportFileEx2 方法
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx2
helpviewer_keywords:
- ImportFileEx2 method
ms.assetid: 02c789fd-16fc-48c6-9619-56e87e2a37ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e6584d31674670bcd005161a846b74df71a27a5f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741642"
---
# <a name="importfileex2-method"></a><span data-ttu-id="ac8d7-102">ImportFileEx2 方法</span><span class="sxs-lookup"><span data-stu-id="ac8d7-102">ImportFileEx2 Method</span></span>
<span data-ttu-id="ac8d7-103">匯入組件和未繫結的模組。</span><span class="sxs-lookup"><span data-stu-id="ac8d7-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="ac8d7-104">這個方法就像是[ImportFile 方法](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)，但即使正在匯入的檔案不存在磁碟上的運作方式。</span><span class="sxs-lookup"><span data-stu-id="ac8d7-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac8d7-105">語法</span><span class="sxs-lookup"><span data-stu-id="ac8d7-105">Syntax</span></span>  
  
```cpp  
HRESULT ImportFileEx2(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac8d7-106">參數</span><span class="sxs-lookup"><span data-stu-id="ac8d7-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="ac8d7-107">要匯入的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="ac8d7-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="ac8d7-108">選擇性的目標檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="ac8d7-108">Optional name of target file.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="ac8d7-109">選擇性的匯入範圍[IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="ac8d7-109">Optional import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="ac8d7-110">如果為 TRUE，會使用 ImportTypes，否則匯入必須手動執行。</span><span class="sxs-lookup"><span data-stu-id="ac8d7-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="ac8d7-111">要傳遞至旗標[OpenScope 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)。</span><span class="sxs-lookup"><span data-stu-id="ac8d7-111">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="ac8d7-112">接收的組件或檔案的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="ac8d7-112">Receives unique ID for the assembly or file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="ac8d7-113">接收的組件匯入範圍[IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="ac8d7-113">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="ac8d7-114">如果檔案不是組件時，就可以是 NULL。</span><span class="sxs-lookup"><span data-stu-id="ac8d7-114">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="ac8d7-115">接收檔案和/或匯入的範圍的數目。</span><span class="sxs-lookup"><span data-stu-id="ac8d7-115">Receives the number of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac8d7-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="ac8d7-116">Return Value</span></span>  
 <span data-ttu-id="ac8d7-117">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="ac8d7-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac8d7-118">需求</span><span class="sxs-lookup"><span data-stu-id="ac8d7-118">Requirements</span></span>  
 <span data-ttu-id="ac8d7-119">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="ac8d7-119">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac8d7-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac8d7-120">See also</span></span>

- [<span data-ttu-id="ac8d7-121">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="ac8d7-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="ac8d7-122">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="ac8d7-122">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="ac8d7-123">ALink API</span><span class="sxs-lookup"><span data-stu-id="ac8d7-123">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)

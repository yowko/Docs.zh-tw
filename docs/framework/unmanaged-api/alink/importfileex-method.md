---
title: ImportFileEx 方法
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx
helpviewer_keywords:
- ImportFileEx method
ms.assetid: ad276f3f-b303-46ac-97e0-66a377adaa4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b3cf91ad4e048ddfccb4086f36923f33d754ac0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949119"
---
# <a name="importfileex-method"></a><span data-ttu-id="4b86e-102">ImportFileEx 方法</span><span class="sxs-lookup"><span data-stu-id="4b86e-102">ImportFileEx Method</span></span>
<span data-ttu-id="4b86e-103">匯入指定組件或未繫結的模組。</span><span class="sxs-lookup"><span data-stu-id="4b86e-103">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b86e-104">語法</span><span class="sxs-lookup"><span data-stu-id="4b86e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4b86e-105">參數</span><span class="sxs-lookup"><span data-stu-id="4b86e-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="4b86e-106">要從中匯入檔案的完整的名稱。</span><span class="sxs-lookup"><span data-stu-id="4b86e-106">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="4b86e-107">選擇性的目標檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="4b86e-107">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="4b86e-108">如果為 TRUE，會使用 ImportTypes，否則匯入必須手動執行。</span><span class="sxs-lookup"><span data-stu-id="4b86e-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="4b86e-109">要傳遞至旗標[OpenScope 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)。</span><span class="sxs-lookup"><span data-stu-id="4b86e-109">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="4b86e-110">接收所匯入的檔案識別碼。</span><span class="sxs-lookup"><span data-stu-id="4b86e-110">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="4b86e-111">接收的組件匯入範圍[IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="4b86e-111">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="4b86e-112">如果檔案不是組件是設為 NULL。</span><span class="sxs-lookup"><span data-stu-id="4b86e-112">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="4b86e-113">接收的匯入的檔案和/或範圍的數目。</span><span class="sxs-lookup"><span data-stu-id="4b86e-113">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b86e-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="4b86e-114">Return Value</span></span>  
 <span data-ttu-id="4b86e-115">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="4b86e-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b86e-116">需求</span><span class="sxs-lookup"><span data-stu-id="4b86e-116">Requirements</span></span>  
 <span data-ttu-id="4b86e-117">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="4b86e-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b86e-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b86e-118">See also</span></span>

- [<span data-ttu-id="4b86e-119">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="4b86e-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="4b86e-120">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="4b86e-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="4b86e-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="4b86e-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)

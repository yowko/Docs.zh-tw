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
ms.openlocfilehash: 9e373f133830a5bc1f3cf7bdc8034cb67725d797
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705198"
---
# <a name="importfileex-method"></a><span data-ttu-id="9e58d-102">ImportFileEx 方法</span><span class="sxs-lookup"><span data-stu-id="9e58d-102">ImportFileEx Method</span></span>

<span data-ttu-id="9e58d-103">匯入指定的元件或未系結的模組。</span><span class="sxs-lookup"><span data-stu-id="9e58d-103">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e58d-104">語法</span><span class="sxs-lookup"><span data-stu-id="9e58d-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="9e58d-105">參數</span><span class="sxs-lookup"><span data-stu-id="9e58d-105">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="9e58d-106">要匯入之檔案的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="9e58d-106">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="9e58d-107">目的檔案名的選擇性名稱。</span><span class="sxs-lookup"><span data-stu-id="9e58d-107">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="9e58d-108">若為 TRUE，則會使用 ImportTypes，否則必須手動執行匯入。</span><span class="sxs-lookup"><span data-stu-id="9e58d-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="9e58d-109">要傳遞至 [OpenScope 方法](../metadata/imetadatadispenser-openscope-method.md)的旗標。</span><span class="sxs-lookup"><span data-stu-id="9e58d-109">Flags to be passed along to [OpenScope Method](../metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="9e58d-110">接收正在匯入之檔案的識別碼。</span><span class="sxs-lookup"><span data-stu-id="9e58d-110">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="9e58d-111">接收元件匯入範圍 [IMetaDataAssemblyImport 介面](../metadata/imetadataassemblyimport-interface.md) 介面。</span><span class="sxs-lookup"><span data-stu-id="9e58d-111">Receives assembly import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="9e58d-112">如果檔案不是元件，則設定為 Null。</span><span class="sxs-lookup"><span data-stu-id="9e58d-112">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="9e58d-113">接收已匯入檔案和/或範圍的計數。</span><span class="sxs-lookup"><span data-stu-id="9e58d-113">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e58d-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="9e58d-114">Return Value</span></span>  

 <span data-ttu-id="9e58d-115">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="9e58d-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e58d-116">需求</span><span class="sxs-lookup"><span data-stu-id="9e58d-116">Requirements</span></span>  

 <span data-ttu-id="9e58d-117">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="9e58d-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e58d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e58d-118">See also</span></span>

- [<span data-ttu-id="9e58d-119">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="9e58d-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="9e58d-120">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="9e58d-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="9e58d-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="9e58d-121">ALink API</span></span>](index.md)

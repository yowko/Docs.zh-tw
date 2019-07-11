---
title: ImportTypes2 方法
ms.date: 03/30/2017
api_name:
- IALink2.ImportTypes2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes2
helpviewer_keywords:
- ImportTypes2 method
ms.assetid: 32f3ba58-9695-41e9-ba58-fd19e45ed396
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a7fddfffed499537f5746998a94a3ef32d035685
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741610"
---
# <a name="importtypes2-method"></a><span data-ttu-id="29ec7-102">ImportTypes2 方法</span><span class="sxs-lookup"><span data-stu-id="29ec7-102">ImportTypes2 Method</span></span>
<span data-ttu-id="29ec7-103">會起始匯入的類型。</span><span class="sxs-lookup"><span data-stu-id="29ec7-103">Initiates the import of types.</span></span> <span data-ttu-id="29ec7-104">呼叫這個方法，以開始匯入類型，從透過匯入每個領域[ImportFile 方法](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)。</span><span class="sxs-lookup"><span data-stu-id="29ec7-104">Call this method to begin importing types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29ec7-105">語法</span><span class="sxs-lookup"><span data-stu-id="29ec7-105">Syntax</span></span>  
  
```cpp  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="29ec7-106">參數</span><span class="sxs-lookup"><span data-stu-id="29ec7-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="29ec7-107">用來匯入的組件識別碼。</span><span class="sxs-lookup"><span data-stu-id="29ec7-107">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="29ec7-108">要從中匯入的檔案識別碼。</span><span class="sxs-lookup"><span data-stu-id="29ec7-108">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="29ec7-109">要從中匯入的以零為起始範圍。</span><span class="sxs-lookup"><span data-stu-id="29ec7-109">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="29ec7-110">指定的範圍內接收類型的列舉值控制代碼。</span><span class="sxs-lookup"><span data-stu-id="29ec7-110">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="29ec7-111">選擇性地接收[IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="29ec7-111">Optionally receives [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="29ec7-112">選擇性地指定範圍內接收類型的計數。</span><span class="sxs-lookup"><span data-stu-id="29ec7-112">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29ec7-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="29ec7-113">Return Value</span></span>  
 <span data-ttu-id="29ec7-114">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="29ec7-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29ec7-115">需求</span><span class="sxs-lookup"><span data-stu-id="29ec7-115">Requirements</span></span>  
 <span data-ttu-id="29ec7-116">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="29ec7-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29ec7-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29ec7-117">See also</span></span>

- [<span data-ttu-id="29ec7-118">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="29ec7-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="29ec7-119">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="29ec7-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="29ec7-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="29ec7-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)

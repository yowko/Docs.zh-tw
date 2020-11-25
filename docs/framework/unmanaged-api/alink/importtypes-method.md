---
title: ImportTypes 方法
ms.date: 03/30/2017
api_name:
- IALink.ImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes
helpviewer_keywords:
- ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type:
- apiref
ms.openlocfilehash: 762f78900add70238971978ceecda089d0c725ce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705107"
---
# <a name="importtypes-method"></a><span data-ttu-id="2336d-102">ImportTypes 方法</span><span class="sxs-lookup"><span data-stu-id="2336d-102">ImportTypes Method</span></span>

<span data-ttu-id="2336d-103">從透過 [ImportFile 方法](importfile-method.md)匯入的每個範圍起始匯入類型。</span><span class="sxs-lookup"><span data-stu-id="2336d-103">Initiates the importing of types from each scope imported via [ImportFile Method](importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2336d-104">語法</span><span class="sxs-lookup"><span data-stu-id="2336d-104">Syntax</span></span>  
  
```cpp  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="2336d-105">參數</span><span class="sxs-lookup"><span data-stu-id="2336d-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="2336d-106">要匯入之元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="2336d-106">ID of the assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="2336d-107">要匯入之檔案的識別碼。</span><span class="sxs-lookup"><span data-stu-id="2336d-107">ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="2336d-108">要匯入之以零為基底的範圍。</span><span class="sxs-lookup"><span data-stu-id="2336d-108">Zero-based scope to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="2336d-109">接收此範圍中類型的枚舉器控制碼。</span><span class="sxs-lookup"><span data-stu-id="2336d-109">Receives enumerator handle for the types in this scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="2336d-110">選擇性地接收 [IMetaDataImport 介面](../metadata/imetadataimport-interface.md) 介面。</span><span class="sxs-lookup"><span data-stu-id="2336d-110">Optionally receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="2336d-111">（選擇性）在指定範圍內接收類型的計數。</span><span class="sxs-lookup"><span data-stu-id="2336d-111">Optionally receives count of types in the indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2336d-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="2336d-112">Return Value</span></span>  

 <span data-ttu-id="2336d-113">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="2336d-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2336d-114">需求</span><span class="sxs-lookup"><span data-stu-id="2336d-114">Requirements</span></span>  

 <span data-ttu-id="2336d-115">需要 alink。h</span><span class="sxs-lookup"><span data-stu-id="2336d-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2336d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2336d-116">See also</span></span>

- [<span data-ttu-id="2336d-117">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="2336d-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="2336d-118">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="2336d-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="2336d-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="2336d-119">ALink API</span></span>](index.md)

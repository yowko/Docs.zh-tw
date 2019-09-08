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
ms.openlocfilehash: ce09eca30e1edb9e1afc02216a07955a5fed4fd2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787263"
---
# <a name="importtypes2-method"></a><span data-ttu-id="da531-102">ImportTypes2 方法</span><span class="sxs-lookup"><span data-stu-id="da531-102">ImportTypes2 Method</span></span>
<span data-ttu-id="da531-103">起始類型的匯入。</span><span class="sxs-lookup"><span data-stu-id="da531-103">Initiates the import of types.</span></span> <span data-ttu-id="da531-104">呼叫這個方法，以開始從每個透過[ImportFile 方法](importfile-method.md)匯入的範圍匯入類型。</span><span class="sxs-lookup"><span data-stu-id="da531-104">Call this method to begin importing types from each scope imported via [ImportFile Method](importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da531-105">語法</span><span class="sxs-lookup"><span data-stu-id="da531-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="da531-106">參數</span><span class="sxs-lookup"><span data-stu-id="da531-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="da531-107">要匯入之元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="da531-107">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="da531-108">要從中匯入之檔案的識別碼。</span><span class="sxs-lookup"><span data-stu-id="da531-108">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="da531-109">要匯入之以零為基底的範圍。</span><span class="sxs-lookup"><span data-stu-id="da531-109">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="da531-110">接收指定範圍內之類型的列舉值控制碼。</span><span class="sxs-lookup"><span data-stu-id="da531-110">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="da531-111">選擇性地接收[IMetaDataImport2 介面](../metadata/imetadataimport2-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="da531-111">Optionally receives [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="da531-112">選擇性地接收指定範圍內的類型計數。</span><span class="sxs-lookup"><span data-stu-id="da531-112">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da531-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="da531-113">Return Value</span></span>  
 <span data-ttu-id="da531-114">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="da531-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da531-115">需求</span><span class="sxs-lookup"><span data-stu-id="da531-115">Requirements</span></span>  
 <span data-ttu-id="da531-116">需要 alink. h</span><span class="sxs-lookup"><span data-stu-id="da531-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da531-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da531-117">See also</span></span>

- [<span data-ttu-id="da531-118">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="da531-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="da531-119">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="da531-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="da531-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="da531-120">ALink API</span></span>](index.md)

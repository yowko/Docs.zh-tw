---
title: GetScope 方法
ms.date: 03/30/2017
api_name:
- IALink.GetScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope
helpviewer_keywords:
- GetScope method
ms.assetid: e1555328-2c71-4ece-b357-9eb6d3a8efc4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b3a0e42e9ffb99896bdd09dbbab65eafb40cafff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777203"
---
# <a name="getscope-method"></a><span data-ttu-id="4f7b3-102">GetScope 方法</span><span class="sxs-lookup"><span data-stu-id="4f7b3-102">GetScope Method</span></span>
<span data-ttu-id="4f7b3-103">取得匯入範圍。</span><span class="sxs-lookup"><span data-stu-id="4f7b3-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f7b3-104">語法</span><span class="sxs-lookup"><span data-stu-id="4f7b3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f7b3-105">參數</span><span class="sxs-lookup"><span data-stu-id="4f7b3-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="4f7b3-106">要匯入之元件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="4f7b3-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="4f7b3-107">要匯入之檔案的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="4f7b3-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="4f7b3-108">要匯入之以零為基底的範圍。</span><span class="sxs-lookup"><span data-stu-id="4f7b3-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="4f7b3-109">接收範圍的[IMetaDataImport 介面](../metadata/imetadataimport-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="4f7b3-109">Receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f7b3-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="4f7b3-110">Return Value</span></span>  
 <span data-ttu-id="4f7b3-111">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="4f7b3-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f7b3-112">需求</span><span class="sxs-lookup"><span data-stu-id="4f7b3-112">Requirements</span></span>  
 <span data-ttu-id="4f7b3-113">需要 alink. h</span><span class="sxs-lookup"><span data-stu-id="4f7b3-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f7b3-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f7b3-114">See also</span></span>

- [<span data-ttu-id="4f7b3-115">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="4f7b3-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="4f7b3-116">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="4f7b3-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="4f7b3-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="4f7b3-117">ALink API</span></span>](index.md)

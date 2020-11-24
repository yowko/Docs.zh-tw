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
ms.openlocfilehash: fd5ae6ef40cb171c33132df0f640acbef96d69b5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684666"
---
# <a name="getscope-method"></a><span data-ttu-id="d4e04-102">GetScope 方法</span><span class="sxs-lookup"><span data-stu-id="d4e04-102">GetScope Method</span></span>

<span data-ttu-id="d4e04-103">取得匯入範圍。</span><span class="sxs-lookup"><span data-stu-id="d4e04-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4e04-104">語法</span><span class="sxs-lookup"><span data-stu-id="d4e04-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4e04-105">參數</span><span class="sxs-lookup"><span data-stu-id="d4e04-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="d4e04-106">要匯入之元件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="d4e04-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="d4e04-107">要匯入之檔案的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="d4e04-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="d4e04-108">要匯入之以零為基底的範圍。</span><span class="sxs-lookup"><span data-stu-id="d4e04-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="d4e04-109">接收範圍的 [IMetaDataImport 介面](../metadata/imetadataimport-interface.md) 介面。</span><span class="sxs-lookup"><span data-stu-id="d4e04-109">Receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4e04-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="d4e04-110">Return Value</span></span>  

 <span data-ttu-id="d4e04-111">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="d4e04-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4e04-112">需求</span><span class="sxs-lookup"><span data-stu-id="d4e04-112">Requirements</span></span>  

 <span data-ttu-id="d4e04-113">需要 alink。h</span><span class="sxs-lookup"><span data-stu-id="d4e04-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4e04-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4e04-114">See also</span></span>

- [<span data-ttu-id="d4e04-115">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="d4e04-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="d4e04-116">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="d4e04-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="d4e04-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="d4e04-117">ALink API</span></span>](index.md)

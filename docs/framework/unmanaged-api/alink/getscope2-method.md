---
title: GetScope2 方法
ms.date: 03/30/2017
api_name:
- IALink2.GetScope2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope2
helpviewer_keywords:
- GetScope2 method
ms.assetid: 49435665-6f5a-4acd-9034-8c9244a04a63
topic_type:
- apiref
ms.openlocfilehash: 40df78cdf99c2e0f53be9664f3f5c6386b6c6f93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179402"
---
# <a name="getscope2-method"></a><span data-ttu-id="4b952-102">GetScope2 方法</span><span class="sxs-lookup"><span data-stu-id="4b952-102">GetScope2 Method</span></span>
<span data-ttu-id="4b952-103">獲取導入範圍。</span><span class="sxs-lookup"><span data-stu-id="4b952-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b952-104">語法</span><span class="sxs-lookup"><span data-stu-id="4b952-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;
```  
  
## <a name="parameters"></a><span data-ttu-id="4b952-105">參數</span><span class="sxs-lookup"><span data-stu-id="4b952-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="4b952-106">目的程式集的 ID。</span><span class="sxs-lookup"><span data-stu-id="4b952-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="4b952-107">要從中導入的檔的 ID。</span><span class="sxs-lookup"><span data-stu-id="4b952-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="4b952-108">要導入的零基作用域。</span><span class="sxs-lookup"><span data-stu-id="4b952-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="4b952-109">接收指向[IMetaDataImport2 介面](../metadata/imetadataimport2-interface.md)的指標，用於指示的範圍。</span><span class="sxs-lookup"><span data-stu-id="4b952-109">Receives pointer to [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b952-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="4b952-110">Return Value</span></span>  
 <span data-ttu-id="4b952-111">如果方法成功，則返回S_OK。</span><span class="sxs-lookup"><span data-stu-id="4b952-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b952-112">需求</span><span class="sxs-lookup"><span data-stu-id="4b952-112">Requirements</span></span>  
 <span data-ttu-id="4b952-113">需要 alink.h.</span><span class="sxs-lookup"><span data-stu-id="4b952-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b952-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b952-114">See also</span></span>

- [<span data-ttu-id="4b952-115">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="4b952-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="4b952-116">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="4b952-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="4b952-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="4b952-117">ALink API</span></span>](index.md)

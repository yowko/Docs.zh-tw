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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f08c4a97b8cbc61a735bb9c1e6a31a698e7eefc1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787355"
---
# <a name="getscope2-method"></a><span data-ttu-id="d63bf-102">GetScope2 方法</span><span class="sxs-lookup"><span data-stu-id="d63bf-102">GetScope2 Method</span></span>
<span data-ttu-id="d63bf-103">取得匯入範圍。</span><span class="sxs-lookup"><span data-stu-id="d63bf-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d63bf-104">語法</span><span class="sxs-lookup"><span data-stu-id="d63bf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="d63bf-105">參數</span><span class="sxs-lookup"><span data-stu-id="d63bf-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d63bf-106">目標群組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="d63bf-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="d63bf-107">要匯入之檔案的識別碼。</span><span class="sxs-lookup"><span data-stu-id="d63bf-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="d63bf-108">要匯入之以零為基底的範圍。</span><span class="sxs-lookup"><span data-stu-id="d63bf-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="d63bf-109">接收指定範圍之[IMetaDataImport2 介面](../metadata/imetadataimport2-interface.md)介面的指標。</span><span class="sxs-lookup"><span data-stu-id="d63bf-109">Receives pointer to [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d63bf-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="d63bf-110">Return Value</span></span>  
 <span data-ttu-id="d63bf-111">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="d63bf-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d63bf-112">需求</span><span class="sxs-lookup"><span data-stu-id="d63bf-112">Requirements</span></span>  
 <span data-ttu-id="d63bf-113">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="d63bf-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d63bf-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d63bf-114">See also</span></span>

- [<span data-ttu-id="d63bf-115">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="d63bf-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="d63bf-116">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="d63bf-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="d63bf-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="d63bf-117">ALink API</span></span>](index.md)

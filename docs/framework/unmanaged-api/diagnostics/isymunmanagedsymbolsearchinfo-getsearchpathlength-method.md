---
title: ISymUnmanagedSymbolSearchInfo::GetSearchPathLength 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetSearchPathLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength
helpviewer_keywords:
- GetSearchPathLength method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength method [.NET Framework debugging]
ms.assetid: 274e73cf-8333-47ba-ac12-70214e2b0112
topic_type:
- apiref
ms.openlocfilehash: 9803094753dee27318af9981bd2e2ad196d434e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729066"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpathlength-method"></a><span data-ttu-id="f5703-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength 方法</span><span class="sxs-lookup"><span data-stu-id="f5703-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength Method</span></span>

<span data-ttu-id="f5703-103">取得搜尋路徑長度。</span><span class="sxs-lookup"><span data-stu-id="f5703-103">Gets the search path length.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5703-104">語法</span><span class="sxs-lookup"><span data-stu-id="f5703-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5703-105">參數</span><span class="sxs-lookup"><span data-stu-id="f5703-105">Parameters</span></span>  

 `pcchPath`  
 <span data-ttu-id="f5703-106">擴展的指標， `ULONG32` 會接收包含搜尋路徑長度所需的緩衝區大小（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="f5703-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path length.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5703-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="f5703-107">Return Value</span></span>  

 <span data-ttu-id="f5703-108">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="f5703-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5703-109">需求</span><span class="sxs-lookup"><span data-stu-id="f5703-109">Requirements</span></span>  

 <span data-ttu-id="f5703-110">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="f5703-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5703-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5703-111">See also</span></span>

- [<span data-ttu-id="f5703-112">ISymUnmanagedSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="f5703-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)

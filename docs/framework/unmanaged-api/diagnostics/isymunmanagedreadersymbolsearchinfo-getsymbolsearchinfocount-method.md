---
title: ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfoCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount
helpviewer_keywords:
- GetSymbolSearchInfoCount method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount method [.NET Framework debugging]
ms.assetid: 4068b6ec-525f-4446-8818-0296178cbd19
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6764fe1472052e2657fd32078abe987b68cf9643
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465890"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfocount-method"></a><span data-ttu-id="02a8d-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount 方法</span><span class="sxs-lookup"><span data-stu-id="02a8d-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Method</span></span>
<span data-ttu-id="02a8d-103">取得符號搜尋資訊的計數。</span><span class="sxs-lookup"><span data-stu-id="02a8d-103">Gets a count of symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02a8d-104">語法</span><span class="sxs-lookup"><span data-stu-id="02a8d-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolSearchInfoCount(  
    [out] ULONG32 *pcSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02a8d-105">參數</span><span class="sxs-lookup"><span data-stu-id="02a8d-105">Parameters</span></span>  
 `pcSearchInfo`  
 <span data-ttu-id="02a8d-106">] out] 的指標`ULONG32`接收包含搜尋資訊所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="02a8d-106">]out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="02a8d-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="02a8d-107">Return Value</span></span>  
 <span data-ttu-id="02a8d-108">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="02a8d-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02a8d-109">需求</span><span class="sxs-lookup"><span data-stu-id="02a8d-109">Requirements</span></span>  
 <span data-ttu-id="02a8d-110">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="02a8d-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02a8d-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02a8d-111">See also</span></span>
- [<span data-ttu-id="02a8d-112">ISymUnmanagedReaderSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="02a8d-112">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)

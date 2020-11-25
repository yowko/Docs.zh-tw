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
ms.openlocfilehash: 5883b35bb3f1fec24ec108c9839501f0e81881fc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708864"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfocount-method"></a><span data-ttu-id="17c78-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount 方法</span><span class="sxs-lookup"><span data-stu-id="17c78-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Method</span></span>

<span data-ttu-id="17c78-103">取得符號搜尋資訊的計數。</span><span class="sxs-lookup"><span data-stu-id="17c78-103">Gets a count of symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17c78-104">語法</span><span class="sxs-lookup"><span data-stu-id="17c78-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolSearchInfoCount(  
    [out] ULONG32 *pcSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17c78-105">參數</span><span class="sxs-lookup"><span data-stu-id="17c78-105">Parameters</span></span>  

 `pcSearchInfo`  
 <span data-ttu-id="17c78-106">]）的指標 `ULONG32` ，該指標會接收包含搜尋資訊所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="17c78-106">]out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17c78-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="17c78-107">Return Value</span></span>  

 <span data-ttu-id="17c78-108">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="17c78-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17c78-109">需求</span><span class="sxs-lookup"><span data-stu-id="17c78-109">Requirements</span></span>  

 <span data-ttu-id="17c78-110">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="17c78-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17c78-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17c78-111">See also</span></span>

- [<span data-ttu-id="17c78-112">ISymUnmanagedReaderSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="17c78-112">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)

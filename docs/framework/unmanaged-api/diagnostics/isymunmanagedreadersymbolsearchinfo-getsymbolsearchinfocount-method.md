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
ms.openlocfilehash: 0b59d85227f21bb230333456eda9130416563111
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180524"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfocount-method"></a><span data-ttu-id="614cd-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount 方法</span><span class="sxs-lookup"><span data-stu-id="614cd-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Method</span></span>
<span data-ttu-id="614cd-103">取得符號搜尋資訊的計數。</span><span class="sxs-lookup"><span data-stu-id="614cd-103">Gets a count of symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="614cd-104">語法</span><span class="sxs-lookup"><span data-stu-id="614cd-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolSearchInfoCount(  
    [out] ULONG32 *pcSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="614cd-105">參數</span><span class="sxs-lookup"><span data-stu-id="614cd-105">Parameters</span></span>  
 `pcSearchInfo`  
 <span data-ttu-id="614cd-106">] out] 的指標`ULONG32`接收包含搜尋資訊所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="614cd-106">]out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="614cd-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="614cd-107">Return Value</span></span>  
 <span data-ttu-id="614cd-108">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="614cd-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="614cd-109">需求</span><span class="sxs-lookup"><span data-stu-id="614cd-109">Requirements</span></span>  
 <span data-ttu-id="614cd-110">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="614cd-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="614cd-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="614cd-111">See also</span></span>

- [<span data-ttu-id="614cd-112">ISymUnmanagedReaderSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="614cd-112">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)

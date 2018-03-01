---
title: "ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c87ef1b3ce185c2a92813f231abe6a9ef14ac055
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfocount-method"></a><span data-ttu-id="36672-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount 方法</span><span class="sxs-lookup"><span data-stu-id="36672-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Method</span></span>
<span data-ttu-id="36672-103">取得符號搜尋資訊的計數。</span><span class="sxs-lookup"><span data-stu-id="36672-103">Gets a count of symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36672-104">語法</span><span class="sxs-lookup"><span data-stu-id="36672-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolSearchInfoCount(  
    [out] ULONG32 *pcSearchInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="36672-105">參數</span><span class="sxs-lookup"><span data-stu-id="36672-105">Parameters</span></span>  
 `pcSearchInfo`  
 <span data-ttu-id="36672-106">] out] 的指標`ULONG32`包含搜尋資訊時所需要的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="36672-106">]out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="36672-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="36672-107">Return Value</span></span>  
 <span data-ttu-id="36672-108">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="36672-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36672-109">需求</span><span class="sxs-lookup"><span data-stu-id="36672-109">Requirements</span></span>  
 <span data-ttu-id="36672-110">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="36672-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36672-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="36672-111">See Also</span></span>  
 [<span data-ttu-id="36672-112">ISymUnmanagedReaderSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="36672-112">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)

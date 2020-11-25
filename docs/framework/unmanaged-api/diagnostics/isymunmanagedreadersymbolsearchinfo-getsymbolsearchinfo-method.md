---
title: ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo
helpviewer_keywords:
- GetSymbolSearchInfo method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo method [.NET Framework debugging]
ms.assetid: 40fcdbc5-3bb2-41e9-b995-40984c209a7f
topic_type:
- apiref
ms.openlocfilehash: 69e05fc33b3489f535f1d051da0294fe59e11e00
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708955"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfo-method"></a><span data-ttu-id="4e3a2-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo 方法</span><span class="sxs-lookup"><span data-stu-id="4e3a2-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Method</span></span>

<span data-ttu-id="4e3a2-103">取得符號搜尋資訊。</span><span class="sxs-lookup"><span data-stu-id="4e3a2-103">Gets symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e3a2-104">語法</span><span class="sxs-lookup"><span data-stu-id="4e3a2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
    [in]  ULONG32  cSearchInfo,  
    [out] ULONG32  *pcSearchInfo,  
    [out, size_is(cSearchInfo), length_is(*pcSearchInfo)]  
        ISymUnmanagedSymbolSearchInfo **rgpSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e3a2-105">參數</span><span class="sxs-lookup"><span data-stu-id="4e3a2-105">Parameters</span></span>  

 `cSearchInfo`  
 <span data-ttu-id="4e3a2-106">在 `ULONG32` ，表示的大小 `rgpSearchInfo` 。</span><span class="sxs-lookup"><span data-stu-id="4e3a2-106">[in] A `ULONG32` that indicates the size of `rgpSearchInfo`.</span></span>  
  
 `pcSearchInfo`  
 <span data-ttu-id="4e3a2-107">擴展的指標 `ULONG32` ，會接收包含搜尋資訊所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="4e3a2-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
 `rgpSearchInfo`  
 <span data-ttu-id="4e3a2-108">擴展設定為傳回之 [ISymUnmanagedSymbolSearchInfo](isymunmanagedsymbolsearchinfo-interface.md) 介面的指標。</span><span class="sxs-lookup"><span data-stu-id="4e3a2-108">[out] A pointer that is set to the returned [ISymUnmanagedSymbolSearchInfo](isymunmanagedsymbolsearchinfo-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4e3a2-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="4e3a2-109">Return Value</span></span>  

 <span data-ttu-id="4e3a2-110">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="4e3a2-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e3a2-111">需求</span><span class="sxs-lookup"><span data-stu-id="4e3a2-111">Requirements</span></span>  

 <span data-ttu-id="4e3a2-112">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="4e3a2-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e3a2-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e3a2-113">See also</span></span>

- [<span data-ttu-id="4e3a2-114">ISymUnmanagedReaderSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="4e3a2-114">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)

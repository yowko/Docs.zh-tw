---
title: ISymUnmanagedSymbolSearchInfo::GetSearchPath 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetSearchPath
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetSearchPath
helpviewer_keywords:
- GetSearchPath method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPath method [.NET Framework debugging]
ms.assetid: b588d470-53c2-4492-be8c-957323eaca0b
topic_type:
- apiref
ms.openlocfilehash: eda8a7ff1d8b3031173bf5f73a8b8a8355e6a62c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705523"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpath-method"></a><span data-ttu-id="19649-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath 方法</span><span class="sxs-lookup"><span data-stu-id="19649-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath Method</span></span>

<span data-ttu-id="19649-103">取得搜尋路徑。</span><span class="sxs-lookup"><span data-stu-id="19649-103">Gets the search path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19649-104">語法</span><span class="sxs-lookup"><span data-stu-id="19649-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19649-105">參數</span><span class="sxs-lookup"><span data-stu-id="19649-105">Parameters</span></span>  

 `pcchPath`  
 <span data-ttu-id="19649-106">擴展的指標， `ULONG32` 會接收包含搜尋路徑所需緩衝區的大小（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="19649-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="19649-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="19649-107">Return Value</span></span>  

 <span data-ttu-id="19649-108">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="19649-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19649-109">需求</span><span class="sxs-lookup"><span data-stu-id="19649-109">Requirements</span></span>  

 <span data-ttu-id="19649-110">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="19649-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19649-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19649-111">See also</span></span>

- [<span data-ttu-id="19649-112">ISymUnmanagedSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="19649-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)

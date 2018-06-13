---
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans 方法
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d3bc8b00b568f96cd55b7811f310d34c1ff700d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428644"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="02e3a-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans 方法</span><span class="sxs-lookup"><span data-stu-id="02e3a-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="02e3a-103">開啟發出到語彙基元至來源範圍的對應資訊的特殊的自訂資料區段。</span><span class="sxs-lookup"><span data-stu-id="02e3a-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="02e3a-104">方法已經開啟，或反之亦然，會發生錯誤時，請開啟此區段。</span><span class="sxs-lookup"><span data-stu-id="02e3a-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02e3a-105">語法</span><span class="sxs-lookup"><span data-stu-id="02e3a-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="02e3a-106">傳回值</span><span class="sxs-lookup"><span data-stu-id="02e3a-106">Return Value</span></span>  
 <span data-ttu-id="02e3a-107">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="02e3a-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02e3a-108">需求</span><span class="sxs-lookup"><span data-stu-id="02e3a-108">Requirements</span></span>  
 <span data-ttu-id="02e3a-109">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="02e3a-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02e3a-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02e3a-110">See Also</span></span>  
 [<span data-ttu-id="02e3a-111">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="02e3a-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)

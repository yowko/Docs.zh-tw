---
title: ISymUnmanagedWriter5::CloseMapTokensToSourceSpans 方法
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b3dea6b9710f1ee5ccf8c51261f59b2de026f5e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127773"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="b93ca-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans 方法</span><span class="sxs-lookup"><span data-stu-id="b93ca-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="b93ca-103">關閉對應資訊的語彙基元至來源範圍的特殊的自訂資料區段。</span><span class="sxs-lookup"><span data-stu-id="b93ca-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="b93ca-104">它已關閉之後，就可以不新增任何更多的對應資訊。</span><span class="sxs-lookup"><span data-stu-id="b93ca-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b93ca-105">語法</span><span class="sxs-lookup"><span data-stu-id="b93ca-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b93ca-106">傳回值</span><span class="sxs-lookup"><span data-stu-id="b93ca-106">Return Value</span></span>  
 <span data-ttu-id="b93ca-107">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="b93ca-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b93ca-108">需求</span><span class="sxs-lookup"><span data-stu-id="b93ca-108">Requirements</span></span>  
 <span data-ttu-id="b93ca-109">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b93ca-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b93ca-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b93ca-110">See also</span></span>

- [<span data-ttu-id="b93ca-111">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="b93ca-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)

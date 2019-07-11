---
title: ISymUnmanagedWriter3::Commit 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.Commit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::Commit
helpviewer_keywords:
- Commit method, ISymUnmanagedWriter3 interface [.NET Framework debugging]
- ISymUnmanagedWriter3::Commit method [.NET Framework debugging]
ms.assetid: f6961922-46ec-4d2c-8369-85f880731f37
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bcfa0c01dc36a68711c42a7e8318cea023b1772f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752439"
---
# <a name="isymunmanagedwriter3commit-method"></a><span data-ttu-id="8e914-102">ISymUnmanagedWriter3::Commit 方法</span><span class="sxs-lookup"><span data-stu-id="8e914-102">ISymUnmanagedWriter3::Commit Method</span></span>
<span data-ttu-id="8e914-103">認可的變更寫入目前資料流。</span><span class="sxs-lookup"><span data-stu-id="8e914-103">Commits the changes written so far to the stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e914-104">語法</span><span class="sxs-lookup"><span data-stu-id="8e914-104">Syntax</span></span>  
  
```cpp  
HRESULT Commit();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8e914-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="8e914-105">Return Value</span></span>  
 <span data-ttu-id="8e914-106">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="8e914-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e914-107">需求</span><span class="sxs-lookup"><span data-stu-id="8e914-107">Requirements</span></span>  
 <span data-ttu-id="8e914-108">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8e914-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e914-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e914-109">See also</span></span>

- [<span data-ttu-id="8e914-110">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="8e914-110">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)

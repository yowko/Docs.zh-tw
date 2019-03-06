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
ms.openlocfilehash: 38d9c3eeb5cdb8b15ef5306a641910f2f4bcc9cf
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372343"
---
# <a name="isymunmanagedwriter3commit-method"></a><span data-ttu-id="49db8-102">ISymUnmanagedWriter3::Commit 方法</span><span class="sxs-lookup"><span data-stu-id="49db8-102">ISymUnmanagedWriter3::Commit Method</span></span>
<span data-ttu-id="49db8-103">認可的變更寫入目前資料流。</span><span class="sxs-lookup"><span data-stu-id="49db8-103">Commits the changes written so far to the stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49db8-104">語法</span><span class="sxs-lookup"><span data-stu-id="49db8-104">Syntax</span></span>  
  
```  
HRESULT Commit();  
```  
  
## <a name="return-value"></a><span data-ttu-id="49db8-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="49db8-105">Return Value</span></span>  
 <span data-ttu-id="49db8-106">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="49db8-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49db8-107">需求</span><span class="sxs-lookup"><span data-stu-id="49db8-107">Requirements</span></span>  
 <span data-ttu-id="49db8-108">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="49db8-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49db8-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49db8-109">See also</span></span>
- [<span data-ttu-id="49db8-110">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="49db8-110">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)

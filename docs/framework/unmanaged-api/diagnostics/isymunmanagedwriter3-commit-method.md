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
ms.openlocfilehash: 9e4e2cd49bdffd0a1293a5601cb44e4804e2b1ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428950"
---
# <a name="isymunmanagedwriter3commit-method"></a><span data-ttu-id="f4992-102">ISymUnmanagedWriter3::Commit 方法</span><span class="sxs-lookup"><span data-stu-id="f4992-102">ISymUnmanagedWriter3::Commit Method</span></span>
<span data-ttu-id="f4992-103">認可的變更寫入目前資料流。</span><span class="sxs-lookup"><span data-stu-id="f4992-103">Commits the changes written so far to the stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4992-104">語法</span><span class="sxs-lookup"><span data-stu-id="f4992-104">Syntax</span></span>  
  
```  
HRESULT Commit();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f4992-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="f4992-105">Return Value</span></span>  
 <span data-ttu-id="f4992-106">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="f4992-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4992-107">需求</span><span class="sxs-lookup"><span data-stu-id="f4992-107">Requirements</span></span>  
 <span data-ttu-id="f4992-108">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f4992-108">**Header:** CorSym.idl , CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4992-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4992-109">See Also</span></span>  
 [<span data-ttu-id="f4992-110">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="f4992-110">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)

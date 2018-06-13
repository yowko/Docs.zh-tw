---
title: ISymUnmanagedWriter::Close 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Close
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 30747fa25528f5679264ebfb67addf401b7d01d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426325"
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="8e991-102">ISymUnmanagedWriter::Close 方法</span><span class="sxs-lookup"><span data-stu-id="8e991-102">ISymUnmanagedWriter::Close Method</span></span>
<span data-ttu-id="8e991-103">關閉後認可到符號存放區的符號的符號寫入器。</span><span class="sxs-lookup"><span data-stu-id="8e991-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e991-104">語法</span><span class="sxs-lookup"><span data-stu-id="8e991-104">Syntax</span></span>  
  
```  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8e991-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="8e991-105">Return Value</span></span>  
 <span data-ttu-id="8e991-106">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="8e991-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e991-107">備註</span><span class="sxs-lookup"><span data-stu-id="8e991-107">Remarks</span></span>  
 <span data-ttu-id="8e991-108">呼叫後，符號寫入器會變成無效的進一步更新。</span><span class="sxs-lookup"><span data-stu-id="8e991-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="8e991-109">若要關閉符號寫入器未認可的符號，請使用[isymunmanagedwriter:: Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="8e991-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e991-110">需求</span><span class="sxs-lookup"><span data-stu-id="8e991-110">Requirements</span></span>  
 <span data-ttu-id="8e991-111">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8e991-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e991-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e991-112">See Also</span></span>  
 [<span data-ttu-id="8e991-113">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="8e991-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

---
title: "ISymUnmanagedDocument::GetCheckSum 方法"
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
- ISymUnmanagedDocument.GetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSum method [.NET Framework debugging]
- GetCheckSum method [.NET Framework debugging]
ms.assetid: 9bc881b3-e2ce-48a7-ad69-17eaaa304120
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 19cd8881bdbd482cb420717855593d7b9583ae51
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="fd099-102">ISymUnmanagedDocument::GetCheckSum 方法</span><span class="sxs-lookup"><span data-stu-id="fd099-102">ISymUnmanagedDocument::GetCheckSum Method</span></span>
<span data-ttu-id="fd099-103">取得總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="fd099-103">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd099-104">語法</span><span class="sxs-lookup"><span data-stu-id="fd099-104">Syntax</span></span>  
  
```  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fd099-105">參數</span><span class="sxs-lookup"><span data-stu-id="fd099-105">Parameters</span></span>  
 `cData`  
 <span data-ttu-id="fd099-106">[in]所提供的緩衝區長度`data`參數</span><span class="sxs-lookup"><span data-stu-id="fd099-106">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="fd099-107">[out]大小和總和檢查碼，以位元組為單位的長度。</span><span class="sxs-lookup"><span data-stu-id="fd099-107">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="fd099-108">[out]接收總和檢查碼的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="fd099-108">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd099-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="fd099-109">Return Value</span></span>  
 <span data-ttu-id="fd099-110">如果方法成功則為 S_OK否則，錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="fd099-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd099-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="fd099-111">See Also</span></span>  
 [<span data-ttu-id="fd099-112">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="fd099-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)

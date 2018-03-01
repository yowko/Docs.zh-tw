---
title: "ISymUnmanagedDocument::GetCheckSumAlgorithmId 方法"
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
- ISymUnmanagedDocument.GetCheckSumAlgorithmId
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId method [.NET Framework debugging]
- GetCheckSumAlgorithmId method [.NET Framework debugging]
ms.assetid: c7f941cd-e25b-4b85-b1ce-5f77c9208fa9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 58fbb5ae13433e0faa47db1e1e49d086670e69d9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a><span data-ttu-id="be40a-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId 方法</span><span class="sxs-lookup"><span data-stu-id="be40a-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId Method</span></span>
<span data-ttu-id="be40a-103">取得總和檢查碼演算法識別項，或如果沒有任何總和檢查碼傳回全部為零的 GUID。</span><span class="sxs-lookup"><span data-stu-id="be40a-103">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be40a-104">語法</span><span class="sxs-lookup"><span data-stu-id="be40a-104">Syntax</span></span>  
  
```  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be40a-105">參數</span><span class="sxs-lookup"><span data-stu-id="be40a-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="be40a-106">[out]接收的總和檢查碼演算法識別項變數的指標。</span><span class="sxs-lookup"><span data-stu-id="be40a-106">[out] A pointer to a variable that receives the checksum algorithm identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be40a-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="be40a-107">Return Value</span></span>  
 <span data-ttu-id="be40a-108">如果此方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="be40a-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be40a-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="be40a-109">See Also</span></span>  
 [<span data-ttu-id="be40a-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="be40a-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)

---
title: ISymUnmanagedDocument::GetCheckSumAlgorithmId 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6c5861f598a653f433ffaa611d6f1be3ba6f69a2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585600"
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a><span data-ttu-id="cbf5d-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId 方法</span><span class="sxs-lookup"><span data-stu-id="cbf5d-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId Method</span></span>
<span data-ttu-id="cbf5d-103">取得總和檢查碼演算法識別項，或如果沒有任何總和檢查碼會傳回全部為零的 GUID。</span><span class="sxs-lookup"><span data-stu-id="cbf5d-103">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbf5d-104">語法</span><span class="sxs-lookup"><span data-stu-id="cbf5d-104">Syntax</span></span>  
  
```  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cbf5d-105">參數</span><span class="sxs-lookup"><span data-stu-id="cbf5d-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="cbf5d-106">[out]收到的總和檢查碼演算法識別項變數的指標。</span><span class="sxs-lookup"><span data-stu-id="cbf5d-106">[out] A pointer to a variable that receives the checksum algorithm identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cbf5d-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="cbf5d-107">Return Value</span></span>  
 <span data-ttu-id="cbf5d-108">如果方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="cbf5d-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbf5d-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbf5d-109">See also</span></span>
- [<span data-ttu-id="cbf5d-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="cbf5d-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)

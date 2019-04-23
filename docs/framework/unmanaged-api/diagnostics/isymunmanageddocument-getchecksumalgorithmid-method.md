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
ms.openlocfilehash: f2df98728eec28ffca05b2e246575fc5c882a078
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59229637"
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a><span data-ttu-id="f9357-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId 方法</span><span class="sxs-lookup"><span data-stu-id="f9357-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId Method</span></span>
<span data-ttu-id="f9357-103">取得總和檢查碼演算法識別項，或如果沒有任何總和檢查碼會傳回全部為零的 GUID。</span><span class="sxs-lookup"><span data-stu-id="f9357-103">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9357-104">語法</span><span class="sxs-lookup"><span data-stu-id="f9357-104">Syntax</span></span>  
  
```  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9357-105">參數</span><span class="sxs-lookup"><span data-stu-id="f9357-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="f9357-106">[out]收到的總和檢查碼演算法識別項變數的指標。</span><span class="sxs-lookup"><span data-stu-id="f9357-106">[out] A pointer to a variable that receives the checksum algorithm identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9357-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="f9357-107">Return Value</span></span>  
 <span data-ttu-id="f9357-108">如果方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="f9357-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9357-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9357-109">See also</span></span>

- [<span data-ttu-id="f9357-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="f9357-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)

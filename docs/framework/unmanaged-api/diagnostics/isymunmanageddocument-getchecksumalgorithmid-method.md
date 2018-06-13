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
ms.openlocfilehash: c815b256ebdab82a57f921a5df016a1552f6d052
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424348"
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a><span data-ttu-id="fa131-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId 方法</span><span class="sxs-lookup"><span data-stu-id="fa131-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId Method</span></span>
<span data-ttu-id="fa131-103">取得總和檢查碼演算法識別項，或如果沒有任何總和檢查碼傳回全部為零的 GUID。</span><span class="sxs-lookup"><span data-stu-id="fa131-103">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa131-104">語法</span><span class="sxs-lookup"><span data-stu-id="fa131-104">Syntax</span></span>  
  
```  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fa131-105">參數</span><span class="sxs-lookup"><span data-stu-id="fa131-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="fa131-106">[out]接收的總和檢查碼演算法識別項變數的指標。</span><span class="sxs-lookup"><span data-stu-id="fa131-106">[out] A pointer to a variable that receives the checksum algorithm identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa131-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="fa131-107">Return Value</span></span>  
 <span data-ttu-id="fa131-108">如果此方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="fa131-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa131-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa131-109">See Also</span></span>  
 [<span data-ttu-id="fa131-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="fa131-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)

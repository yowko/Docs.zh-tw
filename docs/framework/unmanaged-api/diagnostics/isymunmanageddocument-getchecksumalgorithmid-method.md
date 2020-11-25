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
ms.openlocfilehash: 3c82cf45bca3cc9ec73255586db73a903edaf1ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698568"
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a><span data-ttu-id="d2546-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId 方法</span><span class="sxs-lookup"><span data-stu-id="d2546-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId Method</span></span>

<span data-ttu-id="d2546-103">取得總和檢查碼演算法識別碼，如果沒有總和檢查碼，則會傳回所有零的 GUID。</span><span class="sxs-lookup"><span data-stu-id="d2546-103">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2546-104">語法</span><span class="sxs-lookup"><span data-stu-id="d2546-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2546-105">參數</span><span class="sxs-lookup"><span data-stu-id="d2546-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="d2546-106">擴展變數的指標，此變數會接收總和檢查碼演算法識別碼。</span><span class="sxs-lookup"><span data-stu-id="d2546-106">[out] A pointer to a variable that receives the checksum algorithm identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2546-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="d2546-107">Return Value</span></span>  

 <span data-ttu-id="d2546-108">如果方法成功，則為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="d2546-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2546-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2546-109">See also</span></span>

- [<span data-ttu-id="d2546-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="d2546-110">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)

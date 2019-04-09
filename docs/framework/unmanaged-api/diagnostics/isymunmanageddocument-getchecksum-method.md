---
title: ISymUnmanagedDocument::GetCheckSum 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a60bf279c143559e7410d8dfd8213d3da1d05a6d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127553"
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="7bb25-102">ISymUnmanagedDocument::GetCheckSum 方法</span><span class="sxs-lookup"><span data-stu-id="7bb25-102">ISymUnmanagedDocument::GetCheckSum Method</span></span>
<span data-ttu-id="7bb25-103">取得總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="7bb25-103">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bb25-104">語法</span><span class="sxs-lookup"><span data-stu-id="7bb25-104">Syntax</span></span>  
  
```  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bb25-105">參數</span><span class="sxs-lookup"><span data-stu-id="7bb25-105">Parameters</span></span>  
 `cData`  
 <span data-ttu-id="7bb25-106">[in]所提供的緩衝區長度`data`參數</span><span class="sxs-lookup"><span data-stu-id="7bb25-106">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="7bb25-107">[out]大小和總和檢查碼，以位元組為單位的長度。</span><span class="sxs-lookup"><span data-stu-id="7bb25-107">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="7bb25-108">[out]接收的總和檢查碼的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="7bb25-108">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7bb25-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="7bb25-109">Return Value</span></span>  
 <span data-ttu-id="7bb25-110">如果方法成功，則為 S_OK否則，出現錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="7bb25-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bb25-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bb25-111">See also</span></span>

- [<span data-ttu-id="7bb25-112">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="7bb25-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)

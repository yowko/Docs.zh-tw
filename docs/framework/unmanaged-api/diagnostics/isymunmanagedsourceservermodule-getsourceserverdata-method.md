---
title: "ISymUnmanagedSourceServerModule::GetSourceServerData 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedSourceServerModule.GetSourceServerData
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedSourceServerModule::GetSourceServerData
helpviewer_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData method [.NET Framework debugging]
- GetSourceServerData method [.NET Framework debugging]
ms.assetid: 20bdf8ff-2d15-4c64-8950-6888f642d6c0
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5774e46f69a7c38943314697575c7aef67b96693
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="bc4b9-102">ISymUnmanagedSourceServerModule::GetSourceServerData 方法</span><span class="sxs-lookup"><span data-stu-id="bc4b9-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="bc4b9-103">傳回模組的來源伺服器資料。</span><span class="sxs-lookup"><span data-stu-id="bc4b9-103">Returns the source server data for the module.</span></span> <span data-ttu-id="bc4b9-104">呼叫端必須釋放資源，使用`CoTaskMemFree`。</span><span class="sxs-lookup"><span data-stu-id="bc4b9-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc4b9-105">語法</span><span class="sxs-lookup"><span data-stu-id="bc4b9-105">Syntax</span></span>  
  
```  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,   
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bc4b9-106">參數</span><span class="sxs-lookup"><span data-stu-id="bc4b9-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="bc4b9-107">[out]指標`ULONG32`接收大小，以位元組為單位的來源伺服器資料。</span><span class="sxs-lookup"><span data-stu-id="bc4b9-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="bc4b9-108">[out]所傳回的指標`pDataByteCount`值。</span><span class="sxs-lookup"><span data-stu-id="bc4b9-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc4b9-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="bc4b9-109">Return Value</span></span>  
 <span data-ttu-id="bc4b9-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="bc4b9-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc4b9-111">需求</span><span class="sxs-lookup"><span data-stu-id="bc4b9-111">Requirements</span></span>  
 <span data-ttu-id="bc4b9-112">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bc4b9-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc4b9-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc4b9-113">See Also</span></span>  
 [<span data-ttu-id="bc4b9-114">ISymUnmanagedSourceServerModule 介面</span><span class="sxs-lookup"><span data-stu-id="bc4b9-114">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)

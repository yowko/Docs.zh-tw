---
title: "ICorDebugAssembly::GetCodeBase 方法"
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
- ICorDebugAssembly.GetCodeBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetCodeBase
helpviewer_keywords:
- GetCodeBase method [.NET Framework debugging]
- ICorDebugAssembly::GetCodeBase method [.NET Framework debugging]
ms.assetid: 48adc154-9058-4fef-9c43-e9aad80e4dbf
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 24ac81f841be21fe477ad46ef210e2f7d1595acb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassemblygetcodebase-method"></a><span data-ttu-id="3ef0c-102">ICorDebugAssembly::GetCodeBase 方法</span><span class="sxs-lookup"><span data-stu-id="3ef0c-102">ICorDebugAssembly::GetCodeBase Method</span></span>
<span data-ttu-id="3ef0c-103">在目前版本的.NET framework 不實作這個方法。</span><span class="sxs-lookup"><span data-stu-id="3ef0c-103">This method is not implemented in the current version of the .NET Framework.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ef0c-104">語法</span><span class="sxs-lookup"><span data-stu-id="3ef0c-104">Syntax</span></span>  
  
```  
HRESULT GetCodeBase (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR szName[]  
);  
```

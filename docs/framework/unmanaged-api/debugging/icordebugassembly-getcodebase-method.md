---
title: ICorDebugAssembly::GetCodeBase 方法
ms.date: 03/30/2017
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
ms.openlocfilehash: e01cbc5e01a2f32e834c54b60abb05de65cc112c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734058"
---
# <a name="icordebugassemblygetcodebase-method"></a><span data-ttu-id="112ec-102">ICorDebugAssembly::GetCodeBase 方法</span><span class="sxs-lookup"><span data-stu-id="112ec-102">ICorDebugAssembly::GetCodeBase Method</span></span>

<span data-ttu-id="112ec-103">這個方法不會在目前的 .NET Framework 版本中執行。</span><span class="sxs-lookup"><span data-stu-id="112ec-103">This method is not implemented in the current version of the .NET Framework.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="112ec-104">語法</span><span class="sxs-lookup"><span data-stu-id="112ec-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeBase (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR szName[]  
);  
```

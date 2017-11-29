---
title: "ICorDebugAppDomain::EnumerateAssemblies 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.EnumerateAssemblies
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::EnumerateAssemblies
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateAssemblies method [.NET Framework debugging]
- EnumerateAssemblies method [.NET Framework debugging]
ms.assetid: 7add64f9-19a8-46a9-be62-905d5e7d1bd8
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dde65b9a3add4c0b7cd4dea90d5cebaae9f05794
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomainenumerateassemblies-method"></a><span data-ttu-id="2127b-102">ICorDebugAppDomain::EnumerateAssemblies 方法</span><span class="sxs-lookup"><span data-stu-id="2127b-102">ICorDebugAppDomain::EnumerateAssemblies Method</span></span>
<span data-ttu-id="2127b-103">取得應用程式定義域中之組件列舉值。</span><span class="sxs-lookup"><span data-stu-id="2127b-103">Gets an enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2127b-104">語法</span><span class="sxs-lookup"><span data-stu-id="2127b-104">Syntax</span></span>  
  
```  
HRESULT EnumerateAssemblies (  
    [out] ICorDebugAssemblyEnum  **ppAssemblies  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2127b-105">參數</span><span class="sxs-lookup"><span data-stu-id="2127b-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="2127b-106">[out]ICorDebugAssemblyEnum 物件，應用程式定義域中的組件的列舉值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="2127b-106">[out] A pointer to the address of an ICorDebugAssemblyEnum object that is the enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2127b-107">需求</span><span class="sxs-lookup"><span data-stu-id="2127b-107">Requirements</span></span>  
 <span data-ttu-id="2127b-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2127b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2127b-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2127b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2127b-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2127b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2127b-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2127b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

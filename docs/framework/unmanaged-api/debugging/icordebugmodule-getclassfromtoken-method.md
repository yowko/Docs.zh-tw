---
title: "ICorDebugModule::GetClassFromToken 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetClassFromToken
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetClassFromToken
helpviewer_keywords:
- GetClassFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetClassFromToken method [.NET Framework debugging]
ms.assetid: 622a4d3c-0425-4c54-a7e4-0735377cdad2
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bd483eebc66b1274c0d28c46b3ccb1b1272f74b1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulegetclassfromtoken-method"></a><span data-ttu-id="6f0ff-102">ICorDebugModule::GetClassFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="6f0ff-102">ICorDebugModule::GetClassFromToken Method</span></span>
<span data-ttu-id="6f0ff-103">取得指定中繼資料語彙基元的類別。</span><span class="sxs-lookup"><span data-stu-id="6f0ff-103">Gets the class specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f0ff-104">語法</span><span class="sxs-lookup"><span data-stu-id="6f0ff-104">Syntax</span></span>  
  
```  
HRESULT GetClassFromToken(  
    [in]  mdTypeDef        typeDef,  
    [out] ICorDebugClass **ppClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f0ff-105">參數</span><span class="sxs-lookup"><span data-stu-id="6f0ff-105">Parameters</span></span>  
 `typedef`  
 <span data-ttu-id="6f0ff-106">[in]`mdTypeDef`參考類別的中繼資料的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="6f0ff-106">[in] An `mdTypeDef` metadata token that references the metadata of a class.</span></span>  
  
 `ppClass`  
 <span data-ttu-id="6f0ff-107">[out]ICorDebugClass 物件代表之類別的位址指標。</span><span class="sxs-lookup"><span data-stu-id="6f0ff-107">[out] A pointer to the address of an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f0ff-108">需求</span><span class="sxs-lookup"><span data-stu-id="6f0ff-108">Requirements</span></span>  
 <span data-ttu-id="6f0ff-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6f0ff-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f0ff-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f0ff-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f0ff-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f0ff-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f0ff-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f0ff-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

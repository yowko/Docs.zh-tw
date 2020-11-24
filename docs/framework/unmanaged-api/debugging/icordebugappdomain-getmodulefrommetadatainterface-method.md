---
title: ICorDebugAppDomain::GetModuleFromMetaDataInterface 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetModuleFromMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetModuleFromMetaDataInterface
helpviewer_keywords:
- ICorDebugAppDomain::GetModuleFromMetaDatainterface method [.NET Framework debugging]
- GetModuleFromMetaDatainterface method [.NET Framework debugging]
ms.assetid: f35225b3-5dda-4d5a-913d-b3373e9ab81e
topic_type:
- apiref
ms.openlocfilehash: 5dede67412711736d269386a20446cf45fab1619
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672197"
---
# <a name="icordebugappdomaingetmodulefrommetadatainterface-method"></a><span data-ttu-id="3b899-102">ICorDebugAppDomain::GetModuleFromMetaDataInterface 方法</span><span class="sxs-lookup"><span data-stu-id="3b899-102">ICorDebugAppDomain::GetModuleFromMetaDataInterface Method</span></span>

<span data-ttu-id="3b899-103">取得對應至指定中繼資料介面的模組。</span><span class="sxs-lookup"><span data-stu-id="3b899-103">Gets the module that corresponds to the given metadata interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b899-104">語法</span><span class="sxs-lookup"><span data-stu-id="3b899-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromMetaDataInterface (  
    [in] IUnknown           *pIMetaData,  
    [out] ICorDebugModule  **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b899-105">參數</span><span class="sxs-lookup"><span data-stu-id="3b899-105">Parameters</span></span>  

 `pIMetaData`  
 <span data-ttu-id="3b899-106">在物件的指標，該物件為其中一個 [中繼資料介面](../metadata/metadata-interfaces.md)。</span><span class="sxs-lookup"><span data-stu-id="3b899-106">[in] A pointer to an object that is one of the [Metadata interfaces](../metadata/metadata-interfaces.md).</span></span>  
  
 `ppModule`  
 <span data-ttu-id="3b899-107">擴展ICorDebugModule 物件位址的指標，該物件表示對應至指定之中繼資料介面的模組。</span><span class="sxs-lookup"><span data-stu-id="3b899-107">[out] A pointer to the address of an ICorDebugModule object that represents the module corresponding to the given metadata interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b899-108">需求</span><span class="sxs-lookup"><span data-stu-id="3b899-108">Requirements</span></span>  

 <span data-ttu-id="3b899-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3b899-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b899-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3b899-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b899-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b899-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b899-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b899-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

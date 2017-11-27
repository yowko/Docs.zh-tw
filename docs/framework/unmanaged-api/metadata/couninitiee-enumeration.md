---
title: "COUNINITIEE 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COUNINITIEE
api_location: mscoree.dll
api_type: COM
f1_keywords: COUNINITIEE
helpviewer_keywords: COUNINITIEE enumeration [.NET Framework metadata]
ms.assetid: c42baa79-f469-4330-95a2-baf7f021c2fc
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c849a32850b5fc9aaca7ea75fdfb30db3de5d8c9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="04c1b-102">COUNINITIEE 列舉</span><span class="sxs-lookup"><span data-stu-id="04c1b-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="04c1b-103">指定所使用的常數[CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md)初始化 common language runtime 時。</span><span class="sxs-lookup"><span data-stu-id="04c1b-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04c1b-104">語法</span><span class="sxs-lookup"><span data-stu-id="04c1b-104">Syntax</span></span>  
  
```  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,   
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="04c1b-105">成員</span><span class="sxs-lookup"><span data-stu-id="04c1b-105">Members</span></span>  
  
|<span data-ttu-id="04c1b-106">成員</span><span class="sxs-lookup"><span data-stu-id="04c1b-106">Member</span></span>|<span data-ttu-id="04c1b-107">說明</span><span class="sxs-lookup"><span data-stu-id="04c1b-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="04c1b-108">表示預設未初始化模式。</span><span class="sxs-lookup"><span data-stu-id="04c1b-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="04c1b-109">表示卸載組件的未初始化模式。</span><span class="sxs-lookup"><span data-stu-id="04c1b-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="04c1b-110">需求</span><span class="sxs-lookup"><span data-stu-id="04c1b-110">Requirements</span></span>  
 <span data-ttu-id="04c1b-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="04c1b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04c1b-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="04c1b-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="04c1b-113">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="04c1b-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="04c1b-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04c1b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04c1b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04c1b-115">See Also</span></span>  
 [<span data-ttu-id="04c1b-116">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="04c1b-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

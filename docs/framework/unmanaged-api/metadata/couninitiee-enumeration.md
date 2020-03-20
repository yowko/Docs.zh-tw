---
title: COUNINITIEE 列舉
ms.date: 03/30/2017
api_name:
- COUNINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COUNINITIEE
helpviewer_keywords:
- COUNINITIEE enumeration [.NET Framework metadata]
ms.assetid: c42baa79-f469-4330-95a2-baf7f021c2fc
topic_type:
- apiref
ms.openlocfilehash: e5cbd8c5b1bb048088fe137b1359d0bb9e29af20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176119"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="ef088-102">COUNINITIEE 列舉</span><span class="sxs-lookup"><span data-stu-id="ef088-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="ef088-103">指定[CoUn初始化 EE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md)在初始化通用語言運行時使用的常量。</span><span class="sxs-lookup"><span data-stu-id="ef088-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef088-104">語法</span><span class="sxs-lookup"><span data-stu-id="ef088-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="ef088-105">成員</span><span class="sxs-lookup"><span data-stu-id="ef088-105">Members</span></span>  
  
|<span data-ttu-id="ef088-106">member</span><span class="sxs-lookup"><span data-stu-id="ef088-106">Member</span></span>|<span data-ttu-id="ef088-107">描述</span><span class="sxs-lookup"><span data-stu-id="ef088-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="ef088-108">指示預設的未初始化模式。</span><span class="sxs-lookup"><span data-stu-id="ef088-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="ef088-109">指示卸載程式集的未初始化模式。</span><span class="sxs-lookup"><span data-stu-id="ef088-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ef088-110">需求</span><span class="sxs-lookup"><span data-stu-id="ef088-110">Requirements</span></span>  
 <span data-ttu-id="ef088-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ef088-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef088-112">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="ef088-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ef088-113">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="ef088-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ef088-114">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef088-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef088-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef088-115">See also</span></span>

- [<span data-ttu-id="ef088-116">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="ef088-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

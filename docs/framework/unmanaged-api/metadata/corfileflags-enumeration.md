---
title: "CorFileFlags 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorFileFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorFileFlags
helpviewer_keywords: CorFileFlags enumeration [.NET Framework metadata]
ms.assetid: d16703fd-518f-412e-92cb-74433d11032e
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bf123f734f73ecfe726a80099de6ec06b0ced06b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="4972c-102">CorFileFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="4972c-102">CorFileFlags Enumeration</span></span>
<span data-ttu-id="4972c-103">包含描述檔案的呼叫中所定義的類型值[imetadataassemblyemit:: Definefile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)。</span><span class="sxs-lookup"><span data-stu-id="4972c-103">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4972c-104">語法</span><span class="sxs-lookup"><span data-stu-id="4972c-104">Syntax</span></span>  
  
```  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="4972c-105">成員</span><span class="sxs-lookup"><span data-stu-id="4972c-105">Members</span></span>  
  
|<span data-ttu-id="4972c-106">成員</span><span class="sxs-lookup"><span data-stu-id="4972c-106">Member</span></span>|<span data-ttu-id="4972c-107">說明</span><span class="sxs-lookup"><span data-stu-id="4972c-107">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="4972c-108">指出檔案不是資源檔。</span><span class="sxs-lookup"><span data-stu-id="4972c-108">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="4972c-109">指出檔案，可能是資源檔，不包含中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4972c-109">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4972c-110">需求</span><span class="sxs-lookup"><span data-stu-id="4972c-110">Requirements</span></span>  
 <span data-ttu-id="4972c-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4972c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4972c-112">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="4972c-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="4972c-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4972c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4972c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4972c-114">See Also</span></span>  
 [<span data-ttu-id="4972c-115">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="4972c-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

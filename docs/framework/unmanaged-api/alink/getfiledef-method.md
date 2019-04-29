---
title: GetFileDef 方法
ms.date: 03/30/2017
api_name:
- IALink2.GetFileDef
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetFileDef
helpviewer_keywords:
- GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9153c9b3735e265d59ba072f747c92434c95d9ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789866"
---
# <a name="getfiledef-method"></a><span data-ttu-id="7fb93-102">GetFileDef 方法</span><span class="sxs-lookup"><span data-stu-id="7fb93-102">GetFileDef Method</span></span>
<span data-ttu-id="7fb93-103">擷取中繼資料 （而不是由 ALink 指派的權杖） 中所使用的實際 FileDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="7fb93-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fb93-104">語法</span><span class="sxs-lookup"><span data-stu-id="7fb93-104">Syntax</span></span>  
  
```  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fb93-105">參數</span><span class="sxs-lookup"><span data-stu-id="7fb93-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="7fb93-106">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="7fb93-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="7fb93-107">語彙基元的加入的檔案從 AddFile 方法或 AddImport 方法擷取。</span><span class="sxs-lookup"><span data-stu-id="7fb93-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="7fb93-108">接收 FileDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="7fb93-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7fb93-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="7fb93-109">Return Value</span></span>  
 <span data-ttu-id="7fb93-110">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="7fb93-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fb93-111">需求</span><span class="sxs-lookup"><span data-stu-id="7fb93-111">Requirements</span></span>  
 <span data-ttu-id="7fb93-112">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="7fb93-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fb93-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7fb93-113">See also</span></span>

- [<span data-ttu-id="7fb93-114">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="7fb93-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="7fb93-115">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="7fb93-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="7fb93-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="7fb93-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)

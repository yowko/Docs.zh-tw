---
title: "GetFileDef 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.GetFileDef
api_location: alink.dll
api_type: COM
f1_keywords: GetFileDef
helpviewer_keywords: GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a31dee6bb1af4f555211822a3b7ec108353214a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="getfiledef-method"></a><span data-ttu-id="0adcd-102">GetFileDef 方法</span><span class="sxs-lookup"><span data-stu-id="0adcd-102">GetFileDef Method</span></span>
<span data-ttu-id="0adcd-103">擷取中繼資料 （而不是指派的 ALink 語彙基元） 中所使用的實際 FileDef 權杖。</span><span class="sxs-lookup"><span data-stu-id="0adcd-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0adcd-104">語法</span><span class="sxs-lookup"><span data-stu-id="0adcd-104">Syntax</span></span>  
  
```  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0adcd-105">參數</span><span class="sxs-lookup"><span data-stu-id="0adcd-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="0adcd-106">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="0adcd-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="0adcd-107">語彙基元加入的檔案從 AddFile 方法或 AddImport 方法擷取。</span><span class="sxs-lookup"><span data-stu-id="0adcd-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="0adcd-108">接收 FileDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="0adcd-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0adcd-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="0adcd-109">Return Value</span></span>  
 <span data-ttu-id="0adcd-110">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="0adcd-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0adcd-111">需求</span><span class="sxs-lookup"><span data-stu-id="0adcd-111">Requirements</span></span>  
 <span data-ttu-id="0adcd-112">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="0adcd-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0adcd-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0adcd-113">See Also</span></span>  
 [<span data-ttu-id="0adcd-114">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="0adcd-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="0adcd-115">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="0adcd-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="0adcd-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="0adcd-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)

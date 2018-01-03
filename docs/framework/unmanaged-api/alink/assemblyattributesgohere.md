---
title: AssemblyAttributesGoHere
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyAttributesGoHere
api_location: alink.dll
api_type: COM
f1_keywords: AssemblyAttributesGoHere
helpviewer_keywords:
- AssemblyAttributesGoHere type
- Alink API, AssemblyAttributesGoHere type
ms.assetid: 7b26fcb6-94f4-4f09-933e-b33efe451f4f
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3363ac5bd53688cfaa667a57afce17b6b52b1f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="assemblyattributesgohere"></a>AssemblyAttributesGoHere
供 ALink 用來做為儲存自訂屬性相關資訊的預留位置。  
  
## <a name="syntax"></a>語法  
  
```  
AssemblyAttributesGoHere  
```  
  
## <a name="remarks"></a>備註  
 這個類型的參考可能會內嵌在來源中包含組件自訂屬性的 netmodule 中。 從一個或多個包含這些類型參考的 netmodule 建置組件資訊清單時，ALink 會使用附加至這些參考的資訊來發出真正的自訂屬性。 因此，這個類型永遠不會具現化，而其參考只會用來做為建置流程的一部分，在最後的組件中並沒有任何用途。  
  
 這個類型的參考會指出與安全性無關且不是多用途的自訂屬性。  
  
 這些類型會在 .NET Framework 中標示為「內部」，其位於 <xref:System.Runtime.CompilerServices>。  
  
## <a name="requirements"></a>需求  
 mscorlib.dll  
  
## <a name="see-also"></a>請參閱  
 [AssemblyAttributesGoHereM](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)  
 [AssemblyAttributesGoHereS](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)  
 [AssemblyAttributesGoHereSM](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)

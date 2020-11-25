---
title: Tlbexp Helper 函式 (Unmanaged API 參考)
ms.date: 03/30/2017
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
ms.openlocfilehash: 9386918f3574720d90bda7e8da592fa0c91160e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708240"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a>Tlbexp Helper 函式 (Unmanaged API 參考)

[型別程式庫匯出工具](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) 會載入名為 TlbRef.dll 的˙動態連結程式庫。 此 DLL 包含兩個協助程式函式，以及匯出工具在「組件-至-型別-程式庫」轉換程序期間使用的介面。  
  
## <a name="in-this-section"></a>本節內容  

 [GetTypeLibInfo 函式](gettypelibinfo-function.md)  
 提供型別程式庫的當地語系化與作業系統資訊。  
  
 [LoadTypeLibWithResolver 函式](loadtypelibwithresolver-function.md)  
 透過使用 [ITypeLibResolver 介面](itypelibresolver-interface.md)的實載入型別程式庫，以解析任何參考的型別程式庫。  
  
 [ITypeLibResolver 介面](itypelibresolver-interface.md)  
 提供 [ResolveTypeLib 方法](resolvetypelib-method.md)，此方法會傳回型別程式庫的完整路徑。

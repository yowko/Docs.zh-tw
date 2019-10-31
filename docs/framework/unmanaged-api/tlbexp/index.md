---
title: Tlbexp Helper 函式 (Unmanaged API 參考)
ms.date: 03/30/2017
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
ms.openlocfilehash: cbde2af9c8a03e6c41f571120027030713f1b8d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104118"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a>Tlbexp Helper 函式 (Unmanaged API 參考)
[型別程式庫匯出工具](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) 會載入名為 TlbRef.dll 的˙動態連結程式庫。 此 DLL 包含兩個協助程式函式，以及匯出工具在「組件-至-型別-程式庫」轉換程序期間使用的介面。  
  
## <a name="in-this-section"></a>本章節內容  
 [GetTypeLibInfo 函式](gettypelibinfo-function.md)  
 提供型別程式庫的當地語系化與作業系統資訊。  
  
 [LoadTypeLibWithResolver 函式](loadtypelibwithresolver-function.md)  
 透過使用 [ITypeLibResolver 介面](itypelibresolver-interface.md)的實載入型別程式庫，以解析任何參考的型別程式庫。  
  
 [ITypeLibResolver 介面](itypelibresolver-interface.md)  
 提供 [ResolveTypeLib 方法](resolvetypelib-method.md)，此方法會傳回型別程式庫的完整路徑。

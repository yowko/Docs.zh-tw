---
title: Tlbexp Helper 函式 (Unmanaged API 參考)
ms.date: 03/30/2017
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a95ff535a4d0847fbd4b8af28f873b67a1829a4f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798831"
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

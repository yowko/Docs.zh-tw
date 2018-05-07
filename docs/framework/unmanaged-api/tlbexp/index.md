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
ms.openlocfilehash: 9f41a233e9b5338bdb0a324ff9af267a97821d4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a>Tlbexp Helper 函式 (Unmanaged API 參考)
[類型程式庫匯出工具](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)(Tlbexp.exe) 載入名為 TlbRef.dll 動態連結程式庫。 此 DLL 包含兩個 helper 函式和匯出工具在組件至類型程式庫轉換程序期間所使用的介面。  
  
## <a name="in-this-section"></a>本節內容  
 [GetTypeLibInfo 函式](../../../../docs/framework/unmanaged-api/tlbexp/gettypelibinfo-function.md)  
 提供類型程式庫的當地語系化和作業系統的資訊。  
  
 [LoadTypeLibWithResolver 函式](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md)  
 藉由使用的實作載入類型程式庫[ITypeLibResolver 介面](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)來解決任何參考類型程式庫。  
  
 [ITypeLibResolver 介面](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)  
 提供[ResolveTypeLib 方法](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md)，它會傳回型別程式庫的完整的路徑。
